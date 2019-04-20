# Accessible fonts for people in a hurry

**TLDR**: 
Fonts can be more a11y friendly by: 
* Using a bigger font size.
* Having sans-serif font Families.
* More contrasting colors.
* If you don't have a11y first, could you provide an a11y theme?

## Alternative ways to interact with the web

 My current job and a few post inspired this post. There is a keen interest on the business side towards making the application more accessible and we are doing some heavy lifting in order to facilitate the interaction for most users.

Some of those include but are not limited to:
* Cognitive impairments (head injury, autism, developmental disabilities) and learning disabilities (such as dyslexia, dyscalculia or ADHD).
* Visual impairment such as low-vision, complete or partial blindness, and color blindness.
* Hearing-related disabilities.
* Motor or dexterity impairment such as carpal tunnel syndrome, artritis and repetitive strain injury.

Most of us interact with a mouse and a keyboard, but there is a wide range of people that just can't. Depending on their condition, our users might use assistive software or devices like: 

* Screen readers like [JAWS](https://www.freedomscientific.com/products/software/jaws/), [talkback](https://support.google.com/accessibility/android/answer/6283677?hl=en), 
* A [braile keyboard](https://www.amazon.com/Braille-Overlays-for-Computer-Keyboards/dp/B00I5PPUKM/ref=sr_1_1_sspa?keywords=braille%20keyboard&qid=1555548524&s=gateway&sr=8-1-spons&psc=1).
* A [switch device](https://www.youtube.com/watch?v=V1yoOLhx_qA&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=2) or their phone volume buttons in the same way.
* A keyboard without a mouse.
* A [Chrome extension](https://chrome.google.com/webstore/detail/opendyslexic-font-for-chr/cdnapgfjopgaggbmfgbiinmmbdcglnam) due to dislexya. 

## What we can do about it

As you can see, there is a wide variety on conditions, for the purpose of this post,  visual impairment is the most relevant for us. Keep in mind that it also includes people wearing glasses due to some degree of [myopia](https://medical-dictionary.thefreedictionary.com/Miopia), [astigmatism](https://www.webmd.com/eye-health/astigmatism-eyes). Even poor illumination or a bad monitor can pose some difficulty for experiencing the web.

Let us begin with the end in mind. Most developers are not expected to design, but there are situations where our input is required, so I want to give you some [heuristics](https://www.thefreedictionary.com/heuristic+rule) in order to make some a11y aware decisions. 

In this post, our goal is **to improve the fonts for readability**.  According to Wikipedia:

> **Readability** is the ease with which a reader can understand a written text. In natural language, the readability of text depends on its content and its presentation.

 **As a rule of thumb, readability most come first**.

### Make fonts bigger

Fonts serve different purposes, they help determine the atmosphere of a website, might even remind us of things and help us better convey a message.

In a world with [ever more mobile internet access](https://www.statista.com/statistics/284202/mobile-phone-internet-user-penetration-worldwide/), having a smaller font might be a good optimization, specially since screens are smaller on mobile devices. However passing a certain threshold, it messes up readability, zooming in might break your layout. Having bigger fonts as a default, makes our layout less prone to break when zooming in.
 
**Bigger fonts are easier to read from a distance**. Here is an [article with use cases](https://blog.usejournal.com/your-body-text-is-too-small-5e02d36dc902).

### Could you avoid serifs?
Serifs are the small lines at the end of a larger stroke in a letter. The image below explains it way better.
![Serif illustration](https://upload.wikimedia.org/wikipedia/en/7/79/Serif-Sans-Comparison.png)

During the early days of the web, there used to be a debate about  why sans serif fonts are better for screens with low resolution. However, the reasons to avoid them are:

* Serif fonts can confuse dyslexics, for example lowercase “p” for a “b”, d”, or “q”.
* Serif fonts can be distracting on narrow spaces. 

### Colors and contrast

When two colors are similar, if the difference is two subtle, people might not perceive the difference, this is why **contrast matters**. Here is the contrast definition:

> [Contrast](https://www.merriam-webster.com/dictionary/contrast) is the difference or degree of difference between things having similar or comparable natures.

As crazy as it sounds, two people can be seeing the same color, with one hexadecimal value and still perceive a different color. If the ability to perceive the difference between two colors is too high, this is what we call [color blindness](https://en.wikipedia.org/wiki/Color_blindness). 

The question that arises is: **How do I if the colors I'm using are contrasting enough?** I am glad you asked. 

The unit we use as a reference to measure the contrast between two colors, is called **contrast ratio** A contrast ratio of 4.5:1 is the minimum [Web Content Accessibility Guideline](https://www.w3.org/TR/WCAG/#contrast-minimum).

Here are **tools to help you pick more contrasting colors**:

* http://colorsafe.co/
* http://clrs.cc/a11y/

### A11y themes

In the later months, having a dark theme has become [something cool](https://www.digitaltrends.com/computing/macos-siri-shortcuts-screen-time-ios-wwdc/), [appreciated by the users](https://www.digitaltrends.com/computing/macos-siri-shortcuts-screen-time-ios-wwdc/) and [hype-worthy](https://www.xda-developers.com/facebook-messenger-redesign-dark-theme/).

#### What does it take to provide a dark theme?

From a "[First principle's approach](https://en.wikipedia.org/wiki/First_principle)", a dark theme requires two things:

* To have the color's across an application to be defined a variables. I know this might not be necessary but, stick with me for a bit.
* An alternative color palette.
* A mechanism that allows the user to switch themes.

The question I am trying to pose is, could we provide an `a11y` theme too?

For starters, an `a11y` theme could have two things:
* **Even more contrasting colors**, like [Monokai Charcoal High Contrast theme](https://marketplace.visualstudio.com/items?itemName=74th.monokai-charcoal-high-contrast) for VS Code.
* **Dyslexic friendly fonts**.


## Further resources

Tool to check [Contrast ratio](https://contrast-ratio.com/).
Video about [Typefaces for dyslexics](https://www.youtube.com/watch?v=VLtYFcHx7ec).
[Pulp Fiction Dialog with Typography](https://www.youtube.com/watch?v=wF8f8w6HPoo).
CSS Tricks on [Updating a variable with JavasScript](https://css-tricks.com/updating-a-css-variable-with-javascript/).
Article by Microsoft about  [variable fonts](https://developer.microsoft.com/en-us/microsoft-edge/testdrive/demos/variable-fonts/).
Paul Boag's podscast [episode about Web Typography](https://boagworld.com/season/10/episode/1016/).
[Hemingway app](http://www.hemingwayapp.com/).
Article [about a11y audits](https://addyosmani.com/a11y/) by [Addy Osmani](https://twitter.com/addyosmani)
Article: [Special font for dislexya?](https://web.archive.org/web/20111101034537/http://www.ilo.gw.utwente.nl/ilo/attachments/032_Masterthesis_Leeuw.pdf)


----------

That's all folks, thanks for taking the time to read this article. I'm building a blog with all my blog posts. On the mean time, you peek into my future blog posts along with all the previous ones in this [repo](https://github.com/papaponmx/blog).

You can find me as [@papaponmx](https://twitter.com/papaponmx) on your favorite social network.

Cheers.
