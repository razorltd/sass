# .razor-coding-standards--sass {

We use [Sass](http://sass-lang.com/) to write our CSS on all of our projects at Razor. Sass allows us to write styles that are more understandable and easier to maintain. It also allows us to separate our styles using partials, set up variables for flexibility, and mixins help make our styles reusable.

We also regularly use the [Bootstrap 4](https://v4-alpha.getbootstrap.com/) framework to build our front-ends. It comes with Bootstrap’s source Sass files and enables us to create an attractive front-end quickly. Sometimes, Bootstrap can be too heavy for some projects and in this case we may choose not to use it at all or to only use parts of it. Even if we don’t use it, we can create some key principles for all of our projects from it.

## Key principles
- Use [partials](#parials-architecture) well, don’t lumber everything in one big file.
- Keep [class names](#class-naming) human and as simple as they can be. Use BEM when appropriate and describe the content, not the style.
- Pay attention to [syntax and formatting](#syntax-and-formatting), we all need to work with each others code so this should be consistent across projects.
- Be mindful of [nesting rules](#nesting-rules). Sass has many benefits but one of its draw backs is that it’s easy to nest too deeply. We want to stick to no more than three levels deep.
- Take note not to use unnecessary [markup](#markup-best-practices), it makes it harder to read and work with. Stick to simple and semantic markup, and keep accessibility in mind.
- We’re sure you’ll know most of this but it’s always good to familiarise yourself with basic [CSS best practices](#css-best-practices) such as using quotations around strings, preferable units and avoiding the use of `!important`. 😇


## Partials architecture
- Place global partials such as `_typography.scss`, `_reset.scss` and `_base.scss` in a folder called **base**.
- Split site sections into different partials (e.g. `_header.scss`, `_footer.scss`, `_sidebar.scss`, `_navigation.scss`, `_grid.scss`), put these in their own folder called **layout**.
- Split interface elements into different partials (e.g. `_buttons.scss`, `_forms.scss`, `_tables.scss`), these should live in their own folder called **components**.

These partials should only contain styles that are to be applied globally and should make up the bulk of our styles. Don’t apply class names like `case-study-heading` to them. We want the styles to be reusable. We might want to use that heading on multiple sections so a better class name might be `section-heading`.

Sometimes though, we may want to apply styles only to a specific page, in this case we would create a folder called **templates** and store page specific partials in there such as `_home.scss`, `_about.scss` etc. In these partials we may decide that we need to override elements defined before so these should always be called into `site.scss` after the interface element and site section partials. This way, we can easily avoid creating multiple classes for similar styles and having to define those styles multiple times. 

![alt text](https://github.com/razorltd/sass/blob/master/partials-screenshot.png “Partials structure”)

## Class naming
We should always strive not to give too specific class names to our elements. Keeping class names as simple as we can will make them readable for yourself and other front-end developers. Our CSS needs to be maintainable, reusable and as future-proof as possible.

- Don’t over complicate it. We don’t want to use super long class names but we also don’t want abbreviations that aren’t human; `sidebar` is always better than `sb` even if it is longer.
- Just to note though, some shorthand is acceptable. `btn` commonly represents button.
- Keep it flexible. `btn-primary` is a better class name than `btn-red`, that button might not always be red after all.
- Describe the content, not the styling. `success` is semantically meaningful, `green-message` is not.
- We should strive to adopt the [BEM](http://getbem.com/) methodology to ensure that everyone who works on the project speaks the same language. BEM gives us a solid structure that is simple, easy to understand and one that we can all learn and use.
- But you don’t need to use BEM for everything! Save it for the more complex styles. A standalone rule doesn’t need BEM, nor does anything that is only using our global styles.
- Class names should always be lowercase.

⭐️ **Tip:** Don’t worry about Bootstrap style vs BEM style. Leave Bootstrap class names as they are and just use BEM when *you* create styles (and only when you think it’s helpful to do so, as mentioned above; standalone rules don’t need BEM). 
 
## Syntax and formatting
Coding guidelines help us code consistently with one another. We all have our own way of writing CSS but doing things our own way can make our CSS hard to read when others need to work on the project. For consistency please try to write in the following way:

- Three-space indentation
- Multi-line CSS rules
- Multiple class names on their own line
- Useful comments are good and we encourage you to use them even if it’s just so you can remember why you did something. 👌
- Try not to use IDs in your CSS.

```sass
// Do this //
header,
aside,
footer {
   background-color: $brand-primary;
}

// Not this //
#header, #aside, #footer { background-color: $brand-primary; }

```

⭐️ **Tip:** You can change the tab indentation from four spaces (default) to three in Sublime.

⭐️ **Tip:** Add `"draw_white_space": "all",` to **Preferences: Settings – User** in Sublime to always show inconsistent use of whitespace in your files.

## Nesting rules
Despite the many benefits of using Sass, it unfortunately makes it easy to nest too deeply. This can cause problems in older browsers but also make it more difficult for a front-end developer to read and make changes to styles. Therefore, we recommend you don’t nest more than three levels deep.

Fortunately, if our coding standards are followed correctly, this shouldn’t be much of an issue and nesting problems will be easily avoidable.

## Markup best practices
- Take a minimal approach. Don’t use extra `div`, `span` etc if you don’t need to.
- Try to use more semantic markup. `article`, `section`, `footer`, `aside` etc instead of `div`.
- Avoid inline CSS and JavaScript whenever possible.
- Accessibility is key. Don’t forget your `alt` and ARIA roles.

## CSS best practices
- Use `!important` sparingly.
- Wrap strings in single quotes (e.g. `font-family: Verdana, Arial, ‘sans-serif’;`). Wrap URLs in single quotes too and use double quotes if the string contains single quotes.
- Decimal numbers less than one should lead with a zero (e.g. `opacity: 0.5;` not `opacity: .5;`).
- When dealing with lengths, a `0` value should not have a unit (e.g. `padding: 1em 0;`).
- Try to use `rem` and `em` instead of `px`.
- Keep specificity low, you don’t want to be fighting with yourself and it’ll help you avoid the use of `!important`.


🌈🦄💖 **Happy coding!** 💖🦄🌈

# }