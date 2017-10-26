Wedia CSS/Sass Styleguide
===================

### Table of contents

 1. [Formatting](#formatting)
 2. [Syntax](#syntax)
 3.  [CSS / Sass](#css-sass)
 4.  [Naming Conventions](#naming-conventions)
 5. [File organization / Structure](#file-organization-structure)
 6. [Comments](#comments)
 7.  [References](#references)



Formatting
-------------
* Identate using soft tabs with two spaces
* Add a space before the opening brace `{` of declaration blocks
* Add a space after `:` for each declaration
* Write multi-line CSS unless the ruleset have one declaration, then you should use single-line CSS
* Put closing braces `}` of rule declarations on a new line
* When using multiple selectors, every individual selector should have its own line
* Add an empty line between rulesets & nested blocks

```SCSS
// example 1
.wrapper {
  width: 80%;
  margin: 0 auto;
  max-width: $content-width;
  
  .inner { padding: 20px 0; }
}

// example 2
.field__title,
.field__description {
   @include font-size(12px);
   color: $color-secondary;
   font-weight: 700;
}

```
Syntax
-------------
* Use a semicolon `;` after every declaration
* Use hex color codes `#fff` in lowercase, instead of using rgb or `color: white`
* Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`
* Prefer `border: 0` over `border: none`
* Strip out the zero for decimal number, prefer `.5s` over `0.5s`.
* single `'` quotes, double quotes`”`
* Attributes selector should always be enclosed within quotes `[type="text"]`
* Avoid shorthand notation when you don't need to set all the values

```SCSS
//prefer this
.center {
  margin-left: auto;
  margin-right: auto;
}

//not that
.center { margin: 0 auto; }
```


CSS / Sass
-------------

Nesting shouldn't exceed 3 levels, so don't nest when not needed

###CSS / Sass rules order

 1. @extend
 2.  Positioning
 3. Box model
 4. Typography
 5. Visual
 5. Other
 6. Nested selectors

```SCSS
// example

.box {
  @extend %box;
  
  /* Positioning rules*/
  position: absolute; 
  top: 20px;
  left: 20px;

  /* Box model rules */
  display: block; 
  float: left;
  width: 20px;
  height: 20px;

  /* Typography */
  @include font-size(16px);
  color: $color-primary;
  font-weight: 300;
	
  /* Visual */
  background-color: #fff;
  border: 1px solid #ccc;

  /* Other */
  overflow: hidden;
}
```

Naming Conventions
-------------
### Naming Variables

* Names should be reusable, not project specific
* Group specific variables by using the same word as a prefix. This will make it easier for you to use them later in the project.

```SCSS
// Do

//Basic variables
$base-font-size: 14px;
$base-font-family: 'Open Sans', Helvetica, Arial, sans-serif;

$content-width: 1200px;

//Colors
$color-primary:   #7a1ea1;
$color-secondary: #787878;
$color-error:     #xxxxxx;
$color-success:   #xxxxxx;
$color-highlight: #f6f8b4;

//Additional fonts
$font-serif: "Times New Roman", Times, serif;
$font-highlight: "Roboto Slab", sans-serif;
```

```SCSS
// Don't
$blue: #xxxxxx;
$width: 1200px;
```

### Class names

* Keep in mind that your Sass code is supposed to be reused within the project or in another project with similar needs, so try to name your classes according to what they accomplish not to what they represent at that time. (Reusable code means less code, which is easier to maintain.)
* Add a `.js-` prefixed class to use it as a JavaScript hook, don't add styles to that class
* Use `-` instead of camelCase
* Use BEM methodology for naming your classes when this is efficient. We want to keep our code well structured & simple to understand.

> **Example**
> 
*  .section {} is the Block; the higher-level component
* .section__header {} is an Element; a smaller part of the section {} Block. 
* .section--home {} is a Modifier; a different state or variation of .section {} Block.


----------


File organization/Structure
-------------


    
    scss
    |
    ├── base
    │   ├── _variables.scss
    │   ├── _base.scss
    │   ├── _helpers.scss
    │   └── _inputs.scss
    |   └── ...
    ├── layout
    |   ├── _grid.scss
    │   ├── _header.scss
    |   ├── _footer.scss
    │   ├── _main.scss/_shared.scss
    │   └── ...
    ├── component
    │   ├── _pagination.scss
    │   ├── _sidebar.scss
    │   ├── _lists.scss
    │   └── ...
    ├── responsive
    │   ├── _responsive-medium.scss
    │   ├── _responsive-large.scss
    │   ├── _responsive-xlarge.scss
    └── ...


Comments
-------------

Commenting style should be consistent within a project. 

Try to 'title' every Sass partial or block of code the same way

```CSS
/*Form styling
   -------------------------------------------------- */
or

/* Form styling
   ================================================== */
   
or

/* ==================================================
   Form styling
   ================================================== */
```

   

References
-------------

General
https://css-tricks.com/write-better-code-3-levels-code-consistency/
http://cssguidelin.es/
http://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/

Sass / SCSS related
https://sass-guidelin.es/
https://css-tricks.com/snippets/sass/bem-mixins/
https://css-tricks.com/sass-style-guide/
https://css-tricks.com/build-style-guide-straight-sass/

Drupal related
https://www.drupal.org/docs/develop/standards/css/css-architecture-for-drupal-8
https://www.drupal.org/node/1887922

BEM
http://getbem.com/introduction/
https://blog.decaf.de/2015/06/24/why-bem-in-a-nutshell/
http://mikefowler.me/journal/2013/10/17/support-for-bem-modules-sass-3.3
https://cssguidelin.es/#bem-like-naming

Styleguides
http://codeguide.co/
https://github.com/airbnb/css
https://github.com/Workable/css-style-guide
https://github.com/skroutz/css-style-guide
https://google.github.io/styleguide/htmlcssguide.html#CSS_Meta_Rules
https://github.com/necolas/idiomatic-css
