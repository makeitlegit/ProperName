[Home](README.md) • **Best Practices** • [Resources](resources.md) • [Common Format](definition.md) • [Why It Matters](whyitmatters.md)

---

# Best Practices

These goals can help make individual features better, but are most powerful when tackled at the lowest level (data structures) and the greatest breadth (centralized teams and systems). 

Start where you can and bring awareness to the other parts of the org that can do something about it. Many of these best practices relate to feature development such as content strategy, design methods, validation, and development processes. But those can only do so much to mitigate upstream issues...so solutions here also touch on system architecture and integrations, centralized services (e.g. search), and support policies.


# Fundamentals for Name Inputs

Name input can happen any time names are collected, which includes forms, chatbots, and data import.

## 1. Avoid the biggest problem areas

### 1a. DO store names using UTF-8

Many name problems result from the way names are stored. UTF-8 doesn't require users or systems to glean the right ISO character set, which is the most common cause of garbled displays.

*Note that this is an English-centric baseline; while it covers many cases, it leaves out Traditional Chinese and possibly other character sets for particular languages.*

- *DO capture and store names in UTF-8*
- *DO accept what is input and preserve it as best as possible*. 
  - *DO escape strings* for proper storage.
  - *DO ensure the Autocorrect is suppressed* for name inputs.
  - *DO take care how that data is extracted for use and use the correct encoding to display it properly.
- *DO NOT use fallbacks ("sanitize") unless it is impossible to capture UTF-8*. This can make it [difficult to be “found”](https://twitter.com/math3mag1c1an/status/1301224194844360705?s=21) in a system when fallbacks are hidden or inconsistent. If you must...
  - *DO make these conventions clear at the point of substitution* so people know how they can be "found" in the system.
  - *DO notify your Support team about these specific fallbacks*
  - *DO use the same fallbacks throughout your product/service* ideally through a centrally-defined function.

### 1b. DO NOT build in assumptions that block names

**Assumptions about exactly one word in each name** lead to bad data, whether it's truncation or junk. The concept of "middle name" in particular is not a univeral one.

**Assumptions about location** are not helpful given that people travel, work, and live in places all around the world. Additionally, every person has their own unique ethnic, geographic, and family history. Location may determine whether your product/service is available within a workplace, or potentialy even within an entire country. However, location does not lead to any reasonable conclusions about which names to support. Do assume that *any* location may have a user with *any* type of name.

**Assumptions about language** can cause similar problems as assumptions about location. Even if your product/service is only available in English, assume that it may have a user with *any* type of name.

**Assumptions about "acceptable" content** happen when content filters/validation is run on name input fields. While it's not a good idea to outright *reject* names, it's okay to introduce an extra step for caution. Anything that flags content validation should be reviewed by a human. It is also a good idea to let users know when this happens; unfortunately, they've probably had it happen many times before. Because of that, handling these in a thoughtful and humane way can make a huge difference for their experience with your product/service. See the next section about human verification. 

### 1c. DO NOT EVER say a name is invalid

Bad error messages are the fastest way to insult and infuriate your users. If you don't have control over other aspects of your product/service, you can still make a difference here by writing better error messages. Remember that the strings you use for errors are first and foremost for the person attempting to use your product/service to understand what happened. If the system can't handle a name as typed, that's *your* problem. It does not mean their name is any less valid. 

This isn't an edge case. At that moment, when that happens to you, that's the voice of a product or service rejecting you. It's like having someone refuse to pronounce your name correctly...or give you an unwanted nickname because they can't be bothered to respect your name. You feel bad, and they seem incompetent. 

*In case you're not convinced how frequently this happens, follow [@yournameisvalid](https://twitter.com/yournameisvalid) and [@gotapostrophe](https://twitter.com/GotApostrophe) to get a regular reminder.*


## 2. Have a human verify names that get flagged

The best content moderation, including names, is a combination of system design and human oversight. 

Names that get flagged for violation should go through secondary (human) validation that involves direct outreach to these users *before* getting rejected or banned. Ideally those users will not be blocked from using the product/service in the meantime with some mild obfuscation of their name (initials for the questionable parts, or an innocuous system-generated placeholder name). It's also a good idea to have a setting or an "allow" list once their name clears human validation so that any further flagging won't sideline their use of the produt/service (a potential vector for abuse). 

There are two types of names that frequently get flagged as fake when automating content guidelines. 
- Names that look like banned words (like "Candace Poon" or "Cara Dick" - also known as the [Scunthorpe Problem](https://en.wikipedia.org/wiki/Scunthorpe_problem))
- Names that sound like banned words (like "[Phuc Dat Bich](https://www.independent.co.uk/news/world/australasia/man-called-phuc-dat-bich-posts-passport-to-facebook-to-prove-his-name-is-real-a6741586.html)")
- Names that are shared with celebrities (like "Michael Jackson")

Knowledge of slang for types of names can help for troubleshooting Support issues, like "maiden name" (for a prior family name used before a marriage-related family name change)or "double-barreled name" (for a family name consistenting of two names appended together).


## 3. Prepare for predictable name variations in forms and display

These are common reasons for narrowly-scoped systems to reject names, and to add insult to injury, often do so by rudely responding to a person their name is "invalid".

Note that the error validation should be handled on the front end so there's the opportunity to *escape* them rather than reject them.


### 3a. Variation: single-word names

**Names may consist of only one word (as their full name)**, a common practice in [Indonesia](https://twitter.com/perangkaiaksara/status/1300941766074327045?s=20) that also happens in Nigeria and [indigenous](https://twitter.com/DobroMichael/status/1301185855369998338?s=20) communities.

- *DO be consistent about where to store the name*. When a system expects both a FirstName and a LastName, fill your name in the FirstName field since that’s usually used for sorting and make the LastName **LNU** (“last name unknown”).
- *DO prepare for "FNU"* A variant on this approach is to put the name in the LastName field instead and make the FirstName **FNU**. Consider looking for both cases as data may get imported from other systems now or in the future.
- *DO NOT store the same name in both fields* as it is indistinguishable from a valid two-word name, and some people do have the same word as a first and last name.


### 3b. Variation: very short names

**Names can be 1-3 characters**, whether popular Asian surnames like [Wu](https://twitter.com/shirleyywu/status/1300628412466298881?s=20) or [Xu](https://twitter.com/sinxccc/status/1300840632081149954?s=20), Danish names like [Då or ø](https://twitter.com/danishmunk/status/1301128159044272129?s=20), or 33rd U.S. President [Harry S Truman](https://www.nps.gov/hstr/faqs.htm). 

- *DO allow 1 character names.* Don't assume they are abbreviations.


### 3c. Variation: very long names

**Names that are longer than a field supports** might trigger a maximum character limit error on the form, or worse, be silently truncated by the back-end system. 

- *DO set an upper limit, but make it very generous* and match that on form field validation.


### 3d. Variation: name with a space in it

**Names with spaces** may be rejected if form inputs will not allow a space, so plan for that.

- *DO allow spaces in form entry* If there are any spaces at the beginning or end of the field, ignore them (and check browser-specific validation here).
- *DO NOT special-case the term "nil" or "null"* as those can be names too. Use a zero-width space (U+200B) or "" (set it to "empty")


### 3e. Variation: name has "special" characters

**Names with accent marks and diacritical marks** may be more or less common in particular regions but are as normal as any of these other variations. 

- *DO plan for apostrophes*. They're one of the most commonly-occuring special characters in a name, but some systems block them because they have a special meaning for databases. So be sure to [escape the apostrophe](https://github.com/makeitlegit/ProperName/issues/6) on input from the start to prevent database issues. 
- *DO use consistent substitutions (such as these [transliteration recommendations on p.24](https://www.icao.int/publications/Documents/9303_p3_cons_en.pdf)) when needed*.

### 3f. Variation: name varies in capitalization

- *DO preserve the capitalization* The field can automatically capitalize the first letter that is typed, but if a user then corrects that, preserve their intent (ex: de Leon). 
- *DO verify user intent if input is all caps or all lowercase*.

### 3g. Variation: isn't named yet

**Infants may not be named for some time** and may need a special-case name designation (or to be flagged separately). Don't assume they will share any part of their name with parents or relatives.


# Ways to Ensure Features Use Names Right

## I. Honor user choices for what names they display

There are many reasons why people may choose to use a different name than their legal name. Having a product/service use their legal name can be more than disconcerting – it can have serious repercussions for that person's safety. 

- *DO restrict legal name use to absolutely necessary identity confirmations*, and be clear about why it's needed and who will see it. Consider it comparable to the caution used for PHI (patient health information) due to healthcare privacy concerns.
- *DO use a unique identifier for the user that is not dependent on their legal name.* Consider it comparable to not using a SSN (Social Security Number) due to identity theft concerns.  
- *DO NOT use, show, or allow searches on a user's legal name.* These can be used for harm by abusers and stalkers.

In addition, artists use artist names are a way to separate **public** personas from the person. Some artists will only use those names in products/services to ensure that separation.

- *If your system allows for user-alterable display names, it's likely that your users will not expect their proper name to be shown, or be connected to their display name.*


## II. Make your tone appropriate

Names are used to make systems feel more personal, and it can be disconcerting when the wrong name is used. Assumptions about cultural heritage based on names can be problematic, though, so rely on their locale instead of their name to determine what globalization and internationalization (I18N) rules should apply.

- When the context is casual, check the locale-appropriate way to address that person. In western contexts, that usually means addressing them by their personal-use name.
- When the context is formal, check the locale-appropriate way to address that person. In western contexts, that usually means addressing them by title-role and family-use name.

Sometimes people will write their personal name as their legal first name along with their preferred name or nickname in quotes or parentheses. This is a sign that they want to be findable this way, and presented this way to other users. However, they may appreciate being addressed by that preferred name/nickname.


## III. Make your initials smart

Initials can be a useful shorthand for a person's name when they fit what they would write themselves. They may be used as a visual identifier or in place of a [signature](https://github.com/makeitlegit/ProperName/issues/15).

- When the family-name is hyphenated, use the first letter of each word before and after the hyphen. (e.g. Aaron Taylor-Johnson = ATJ)
- When the family-name is multiple words, use the first letter of each word and honor their capitalization. (e.g. Vincent van Gogh = VvG)


## IV. Make your alphabetical sorts smart

Names are also used for sorting people. They are often sorted by affinity networks & activity to ensure relevance to the viewer & context. Even so...at some point, sorts always fall back to a simple alphabetical order. Since names usually consist of multiple parts, consider what parts matter for the sort:

- When the context is casual, sort on persoanl-use name (special case for single-world names: if it's FNU, use family-use name)
- When the context is formal, sort on title-role + family-use name (special case for single-word names: use personal-use name if it's LNU). A note on internationalization: some countries will expect to sort on family-use name only and may ignore any prefixes that originate there (such as in the Netherlands where "Van Gogh" may be sorted under G).


## V. Make your search smart

Names are a key identifier for finding people. Partial searches are the most powerful tool to ensure people can continue to use the fundamental purpose of the system even if/when their names get mangled. 

- *DO search across all stored name fields*, no matter what they're labeled (First, Last, etc.).
- *DO allow partial search terms.* Some people who have changed their family name will show their previous family name in parentheses to more easily be found.
- *DO NOT rely on first letter matches*, since names can end up truncated or stored in surprising ways.
- *DO search on alternatives for special characters*, including potential common substitutions (like these [transliteration recommendations on p.24 of these international travel document guidelines](https://www.icao.int/publications/Documents/9303_p3_cons_en.pdf)).

*Why this is important*: A person's name may have been entered by someone other than themselves, and/or may have passed through another system that modified it. The only way for that person to reliably be found may be to search on a partial string in the middle of their name that's least likely to be misspelled or interpreted differently. It's not great to have your name messed up, but it's far worse to be delayed, have your requests rejected, or be entirely blocked from proceeding because your account can't be found.

## VI. Be flexible about matching names (or match a unique identifier instead)

Any feature that depends on one record's name field matching another needs to be savvy about potential substitutions.

- *DO NOT match on name if a unique identifier exists*. For instance, Passport ID number may be the best way to identify a person if your product/service involves global travel. Show and tell people how to find that number, and use it whenever their ID must be confirmed.
- *DO check for substitutions when a match isn't found (such as these [transliteration recommendations on p.24](https://www.icao.int/publications/Documents/9303_p3_cons_en.pdf))*.

## VII. Make your autocorrect smart

It's maddening to correctly type a name only to have the system change it. This can lead to potentially embarrassing interactions too.

- *DO NOT leave autocorrect on for input fields for names*. Assume that every input field includes autocorrect by default, so take care to disable it for any field asking for a name.
- *DO ensure your autocorrect dictionary isn't leaving out common names*. Contact the I Am Not a Typo campaign for a [common name spreadsheet](https://www.iamnotatypo.org/dear-tech-giants) to train yours to help fill in gaps for "ethnic" names. 


  
[< Back to ProperName overview ](README.md)


