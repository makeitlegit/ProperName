# Best Practices

Many of these best practices relate to feature development such as content strategy, design methods, validation, and development processes. But those can only do so much to mitigate bad assumptions in system architecture and integrations, simplistic support policies, and overreliance on algorithms for content issues.

These are the goals: work backward to figure out how to addres it in the most comprehensive way your company can control. Don't assume everyone at your company already understands how their choices ripple out to the way people experience your product/service.

# Storing Names

## Make your database robust

It's best to remember that people can (and do) travel, work, and live in places all around the world. Since every family and individual has their own ethnic and geographic history, assumptions based on location and language risk excluding potential users.

In other words: the database should support the rich variety of names regardless of where your product or service operates, and/or what languages it supports. Their names are valid; make sure your system is intelligent enough to support them.

*UTF-8 helps preserve names best* as it doesn't require users or systems to glean the right ISO character set (the most common cause of garbled displays). Note that this is an English-centric baseline; while it covers many cases, it leaves out Traditional Chinese and possibly other character sets for particular languages.

If those back end systems cannot properly store a name, you'll have to use fallbacks just to proceed. This can make it [difficult to be “found”](https://twitter.com/math3mag1c1an/status/1301224194844360705?s=21) in a system when you don’t know what fallback was used, so be consistent about them and make these conventions clear to anyone who uses the system.


## Have a human verify names flagged by community guidelines

There are two types of names that frequently get flagged as fake when automating content guidelines. These should go through secondary (human) validation before getting banned:

- Names that look like banned words (like "Candace Poon" or "Cara Dick" - also known as the [Scunthorpe Problem](https://en.wikipedia.org/wiki/Scunthorpe_problem))
- Names that sound like banned words (like "[Phuc Dat Bich](https://www.independent.co.uk/news/world/australasia/man-called-phuc-dat-bich-posts-passport-to-facebook-to-prove-his-name-is-real-a6741586.html)")
- Names that are shared with celebrities (like "Michael Jackson")


## Prepare for predictable name variations

These are common reasons for narrowly-scoped systems to reject names, and to add insult to injury, often do so by rudely responding to a person their name is "invalid".

Note that the error validation should be handled on the front end so there's the opportunity to *escape* them rather than reject them.


### Variation: single-word names

**Names may consist of only one word (as their full name)**, a common practice in [Indonesia](https://twitter.com/perangkaiaksara/status/1300941766074327045?s=20) that also happens in Nigeria and [indigenous](https://twitter.com/DobroMichael/status/1301185855369998338?s=20) communities.

- *DO be consistent about where to store the name*. When a system expects both a FirstName and a LastName, fill your name in the FirstName field since that’s usually used for sorting and make the LastName **LNU** (“last name unknown”).
- *DO prepare for "FNU"* A variant on this approach is to put the name in the LastName field instead and make the FirstName **FNU**. Consider looking for both cases as data may get imported from other systems now or in the future.
- *DO not store the same name in both fields* as it is indistinguishable from a valid two-word name.


### Variation: very short names

**Names can be 1-3 characters**, whether popular Asian surnames like [Wu](https://twitter.com/shirleyywu/status/1300628412466298881?s=20) or [Xu](https://twitter.com/sinxccc/status/1300840632081149954?s=20), Danish names like [Då or ø](https://twitter.com/danishmunk/status/1301128159044272129?s=20), or 33rd U.S. President [Harry S Truman](https://www.nps.gov/hstr/faqs.htm). 

- *DO allow 1 character names.* Don't assume they are abbreviations.


### Variation: very long names

**Names that are longer than a field supports** might trigger a maximum character limit error on the form, or worse, be silently truncated by the back-end system. 

- *DO set an upper limit, but make it very generous* and match that on form field validation.


### Variation: name with a space in it

**Names with spaces** may be rejected if form inputs will not allow a space. One approach is to eliminate the space in the same for a kind of “camel case” variant, but that fails to indicate that something changed in the name.

- *DO allow spaces in form entry* If there are any spaces at the beginning or end of the field, ignore them.
- *DO NOT special-case the term "nil" or "null"* as those can be names too. Use a zero-width space (U+200B) or "" (set it to "empty")


### Variation: name has "special" characters

**Names with accent marks and diacritical marks** may be more or less common in particular regions, but are as normal as any of these other variations. 

- *DO use consistent substitutions (such as these [transliteration recommendations on p.24]("https://www.icao.int/publications/Documents/9303_p3_cons_en.pdf")) when needed*.


### Variation: isn't named yet

**Infants may not be named for some time** and may need a special-case name designation (or to be flagged separately). Don't assume they will share any part of their name with parents or relatives.


# Using Names

## Honor user choices for what names they display

There are many reasons why people may choose to use a different name than their legal name. Having a product/service use their legal name can be more than disconcerting – it can have serious repercussions for that person's safety. 

- *DO restrict legal name use to absolutely necessary identity confirmations*, and be clear about why it's needed and who will see it. Consider it comparable to the caution used for PHI (patient health information) due to healthcare privacy concerns.
- *DO use a unique identifier for the user that is not dependent on their legal name.* Consider it comparable to not using a SSN (Social Security Number) due to identity theft concerns.  
- *DO NOT use, show, or allow searches on a user's legal name.* These can be used for harm by abusers and stalkers.

In addition, artists use artist names are a way to separate **public** personas from the person. Some artists will only use those names in products/services to ensure that separation.

- *If your system allows for user-alterable display names, it's possible that your users will not expect their proper name to be shown, or be connected to their display name.*


## Make your tone appropriate

Names are used to make systems feel more personal, and it can be disconcerting when the wrong name is used. Since names usually consist of multiple parts, consider what parts matter for the tone:

- When the context is casual, address by personal-use name.
- When the context is formal, address by title-prefix and family-use name.


## Make your alphabetical sorts smart

Names are also used for sorting people. They are often sorted by affinity networks & activity to ensure relevance to the viewer & context. Even so...at some point, sorts always fall back to a simple alphabetical order. Since names usually consist of multiple parts, consider what parts matter for the sort:

- When the context is casual, sort on persoanl-use name (special case for single-world names: if it's FNU, use family-use name)
- When the context is formal, sort on title-prefix + family-use name (special case for single-word names: use personal-use name if it's LNU). A note on internationalization: some countries will expect to sort on family-use name only and may ignore any prefixes that originate there (such as in the Netherlands where "Van Gogh" may be sorted under G).


## Make your search smart

Names are a key identifier for finding people. Partial searches are the most powerful tool to ensure people can continue to use the fundamental purpose of the system even if/when their names get mangled. 

- *DO search across all stored name fields*, no matter what they're labeled (First, Last, etc.).
- *DO allow partial search terms.*
- *DO NOT rely on first letter matches*, since names can end up truncated or stored in surprising ways.
- *DO search on alternatives for special characters*, including potential common substitutions (like these [transliteration recommendations on p.24 of these international travel document guidelines]("https://www.icao.int/publications/Documents/9303_p3_cons_en.pdf")).

*Why this is important*: A person's name may have been entered by someone other than themselves, and/or may have passed through another system that modified it. The only way for that person to reliably be found may be to search on a partial string in the middle of their name that's least likely to be misspelled or interpreted differently. It's not great to have your name messed up, but it's far worse to be delayed, have your requests rejected, or be entirely blocked from proceeding because your account can't be found.


[< Back to ProperName overview ](README.md)


