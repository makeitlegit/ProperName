# BEST PRACTICES

## Make your database robust

It's good to remember that people can travel, work, and live in places around the world. Since every family and individual has their own ethnic and geographic history, assumptions based on location and language risk excluding potential users.

In other words: the database should support the rich variety of names regardless of where your product or service operates, and/or what languages it supports. Their names are valid; make sure your system is intelligent enough to support them.

If those back end systems cannot properly store a name, you'll have to use fallbacks just to proceed. This can make it [difficult to be “found”](https://twitter.com/math3mag1c1an/status/1301224194844360705?s=21) in a system when you don’t know what fallback was used, so be consistent about them and make these conventions clear to anyone who uses the system.

## Honor user choices for what names they display

There are many reasons why people may choose to use a different name than their legal name. Having a product/service use their legal name can be more than disconcerting – it can have serious repercussions for that person's safety. 

- *DO restrict legal name use to absolutely necessary identity confirmations*, and be clear about why it's needed and who will see it. Consider it comparable to the caution used for PHI (patient health information) due to healthcare privacy concerns.
- *DO use a unique identifier for the user that is not dependent on their legal name.* Consider it comparable to not using a SSN (Social Security Number) due to identity theft concerns.  
- *DO NOT use, show, or allow searches on a user's legal name.* These can be used for harm by abusers and stalkers.

In addition, artists use artist names are a way to separate **public** personas from the person. Some artists will only use those names in products/services to ensure that separation.

- *If your system allows for user-alterable display names, it's possible that your users will not expect their proper name to be shown, or be connected to their display name.*


## Make your search smart

Names are a key identifier for finding people. Partial searches are the most powerful tool to ensure people can continue to use the fundamental purpose of the system even if/when their names get mangled. 

- *DO search across all stored name fields*, no matter what they're labeled (First, Last, etc.).
- *DO allow partial search terms.*
- *DO NOT rely on first letter matches*, since names can end up truncated or stored in surprising ways.  

*Why this is important*: A person's name may have been entered by someone other than themselves, and/or may have passed through another system that modified it. The only way for that person to reliably be found may be to search on a partial string in the middle of their name that's least likely to be misspelled or interpreted differently. It's not great to have your name messed up, but it's far worse to be delayed, have your requests rejected, or be entirely blocked from proceeding because your account can't be found.


## Make your alphabetical sorts smart

Names are also used for sorting people. They are often sorted by affinity networks & activity to ensure relevance to the viewer & context. Even so...at some point, sorts always fall back to a simple alphabetical order. Since names usually consist of multiple parts, consider what parts matter for the sort:

- When the context is casual, sort on Conversational Name (special case for single-world names: if it's FNU, use Family Name)
- When the context is formal, sort on Affix + Family Name (special case for single-word names: use Conversational Name if it's LNU). A note on internationalization: some countries will expect to sort on Family Name only and ignore affixes that originate there.


## Make your tone appropriate

Names are used to make systems feel more personal, and it can be disconcerting when the wrong name is used. Since names usually consist of multiple parts, consider what parts matter for the tone:

- When the context is casual, address by Conversational Name
- When the context is formal, address by Honorific Prefix and Current Family Name


# COMMON NAME VARIATIONS


## Single-word names

**Names may consist of only one word (as their full name)**, a common practice in [Indonesia](https://twitter.com/perangkaiaksara/status/1300941766074327045?s=20) that also happens in Nigeria and [indigenous](https://twitter.com/DobroMichael/status/1301185855369998338?s=20) communities.

- *DO store the name in the most important name field (usually Last Name)*. When a system expects both a FirstName** and a LastName, fill your name in the LastName field since that’s usually used for sorting and make the FirstName **FNU** (“first name unknown”).
- *DO prepare for "LNU"* A variant on this approach is to put the name in the FirstName field instead and made the LastName **LNU**. Consider looking for both cases as data may get imported from other systems now or in the future.
- *DO not store the same name in both fields* as it is indistinguishable from a valid two-word name.


## Shorter than supported

**Names can be 1-3 characters**, whether popular Asian surnames like [Wu](https://twitter.com/shirleyywu/status/1300628412466298881?s=20) or [Xu](https://twitter.com/sinxccc/status/1300840632081149954?s=20), Danish names like [Då or ø](https://twitter.com/danishmunk/status/1301128159044272129?s=20), or 33rd U.S. President [Harry S Truman](https://www.nps.gov/hstr/faqs.htm). 

- *DO allow 1 character names.*


## Longer than supported

**Names that are longer than a field supports** might trigger a maximum character limit error on the form, or worse, be silently truncated by the back-end system. 

- *DO set an upper limit, but make it very generous* and match that on form field validation.


## Has a space in it

Sometimes a form input will not allow a space. One approach is to eliminate the space in the same for a kind of “camel case” variant, but that fails to indicate that something changed in the name.

- *DO allow spaces in form entry*.


## Has "special" characters


- *DO use the same substitutions when needed*.


