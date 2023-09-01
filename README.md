<!--![cover](/cover.png)
// ![Contributions Welcome](https://img.shields.io/badge/Contributions-welcome-blue.svg)
// Got techniques or resources to help? [Add an issue](https://github.com/makeitlegit/ProperName/issues) or [create a new pull request](https://github.com/makeitlegit/ProperName/pulls).
-->
**Home** • [Best Practices](bestpractices.md) • [Resources](resources.md) • [Common Format](definition.md) • [Why It Matters](whyitmatters.md)

---

# Start Here

ProperName is a knowledge-sharing effort. Getting people's names right is not an impossible task. This is for *developers, designers, and anyone else* who shapes the products/services we all use. It should be used in conjunction with guidance about the globalization/internationalization (I18N) appropriate for the locale.

## [Best Practices](bestpractices.md)  
Guidelines for designing, building, and maintaining systems that will best honor proper names.

## [Resources](resources.md)  
Links to additional tools that either help people with their own name issues, or help those creating products/services.

## [Common Format (experimental)](definition.md)  
A proposal for a common format that can match how names are typically used in products/services.

## [Why It Matters](whyitmatters.md)  
The reasoning behind making an effort to get people's names right. It's not a small thing to those who experience it, nor is it just poor etiquette...and it is painfully common for people to hear that their "[name is invalid](https://www.twitter.com/yournameisvalid)" by a product or service. We can do better.  



# FAQ

## Why is this a thing?
There are so many systems that get people’s names wrong. While it’s easy for a person to accidentally mess up someone else’s name (everyone’s done it at some point), the systems we use can still screw it up even when people mean well. Some people encounter these problems in practically every product and service they use. There’s got to be a better way.


## Is this even solvable?
While it may be impractical to solve for every variant, given that legal name rules vary across countries (and even states in the U.S.), it can certainly be improved.

It's true that plenty of solo developers are discouraged about the complexity once they’ve looked into it. They point to this blog post about [falsehoods programmers believe about names](https://www.kalzumeus.com/2010/06/17/falsehoods-programmers-believe-about-names/) or [this version with examples](https://shinesolutions.com/2018/01/08/falsehoods-programmers-believe-about-names-with-examples/) as a reason that it is impossible to “fix”. That's why the goal needs to be "improve" rather than "solve". A little effort can make the difference for many people.


## Is this a developer problem?
Not exclusively. Even if this were only a problem for developers, it’s absurd to expect every developer to [independently develop solutions](https://twitter.com/dev_johannes/status/1300884211159584768?s=20) for it. Even for those that do, it doesn’t help much to have only one product or service, or only one company, doing the right thing.


## Is this a diversity problem?
Yes and no. It is a diversity problem to have systems with assumptions that make it impossible to store someone’s name correctly. It is not a diversity problem in terms of who works on it – having a diverse team won’t solve this.

To be clear, diverse teams are stronger for a lot of reasons…but just as a team member who happens to be underrepresented shouldn’t suddenly be designated the diversity lead (on top of their other work), it’s also not up to them to be the de facto testing lead to catch “diversity” issues. Let them do their actual job, and seek tools for everyone to do better.

## Aren’t there already groups working to fix this?
Not in a comprehensive way, but there are many folks helping tackle particular name challenges in the Resources. So this is an attempt to gather both awareness and best practices until baseline expectations are set(hopefully with good tools we can use and/or standards we can all point to). Please share this with anyone that's looking to make progress on these issues!

## But what about digital identity?
"Digital Identity" sounded like a promising area that might provide ways to use proper names. Some of those efforts include:
- [Decentralized Identity](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2DjfY)
- [Functional Identity](https://github.com/WebOfTrustInfo/rwot10-buenosaires/blob/master/topics-and-advance-readings/functional-identity-primer.md)
- [Known Traveler Digital Identity](https://ktdi.org/)

These all appear to be focused primarily on a unique identifier for each person. That’s a big hairy issue…and not the focus of ProperName. There’s no guarantee someone else out there isn’t using the same name as you. In fact, you’ve probably already found people that do on the web or on social networks. The goal here is not uniqueness in the world – the goal is accuracy for your own name as you choose it.


## How did this start?
My name is Julie Meridian, and I pursue independent design projects under the banner of my consultancy [Make It Legit](https://www.makeitlegit.com). I split my time between [UX design](https://www.linkedin.com/in/juliemeridian) and [fine art and illustration](https://www.juliemeridian.com). 

I saw this tweet thread about [yet another name frustration](https://twitter.com/rockbot/status/1270400995567169536) that got me thinking about it anew, and got annoyed that this issue has been treated as such an intractable one. So I started looking for best practices…and while there are many stories, and a few resources of folks making progress on small parts of this, I couldn’t find anything comprehensive that tackled _both_ the social and technical challenges.

There are so many people feeling like they’re dealing with this on their own: 
- people encountered their own names mangled yet again
- support folks trying to discern where customers are in ‘the system’ and how to fix issues
- developers anguished by the complexity of this one piece amidst so many other puzzles to solve
- designers disappointed when they discover how their work appears with real use

I realized how much easier it became to design after the [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/) established _specific_ color contrast guidelines. From these, people made tools that designers could use (such as [Stark](https://www.getstark.co/) to anticipate roadblocks for users and design workable variations. The foundation is well-thought guidelines upon which tools can be built to apply them that make them real. 

This is an open-source approach so its core isn’t limited by proprietary technology or licensing. This can be built upon freely for commercial or non-commercial work – whatever it takes to solve these problems. That’s the goal here. As there doesn’t appear to be any top-down effort yet from existing open source organizations, why not start a bottom-up one to set a vision and create/collect useful resources?

I don’t know where this particular project will go…but at least I can get it started. Please [add an issue](https://github.com/makeitlegit/ProperName/issues) if you have ideas for moving this forward, or better yet, [create a new pull request](https://github.com/makeitlegit/ProperName/pulls) if you're GitHub-savvy and in a spot to contribute!
