Garnet Hill CSS formatting Guide
======

CSS formatting standards for Garnet Hill

## Table of contents

1. [General principles](#general)
2. [Whitespace](#whitespace)
3. [Comments](#comments)
4. [Declaration Order](#order)
5. [Formatting ](#format)

[Acknowledgements](#ack)

[License](#lic)

By following this simple set of rules for the creation of CSS stylesheets, all code will appear identical regardless of who wrote it. And in return, any individual can edit another's code with ease by understanding the simple layout prioncipals established.

Designed to be pragmatic, though at times possibly pedantic, this guide will cover the principals of formatting the CSS code for Garnet Hill's web site.
 
<a name="general"></a>
### 1. General principles###
*	All code in any code-base should look like a single person typed it, even when many people are contributing to it.
*	Strictly enforce the agreed-upon style.
*	If in doubt when deciding upon a style use existing, common patterns.

<a name="whitespace"></a>
### 2. Whitespace###
Formatting whitespace with tabs/spaces within the code helps the document's readability. You should never mix tabs and spaces within the same document though. For our standard, we use TAB formatting.
* Use a single tab to indent values.
* Use multiple tabs for nested elements, making sure to never nest further than a third level.
* If deeper nesting is needed, consider adding secondary classes to elements.

<a name="comments"></a>
### 3. Comments###
Commenting code helps future users decipher what is goin on with ease. The extended use of comments can help organize what would normally be a long, messy document. Never add an element to a stylesheeet that is exploratory, unless it is thoroughly commented and organized to discuss what the goal was. Comment format should be consistent throughout the code base.
* Section headings should be used to help organize the entire document.
* Header descriptors should be used to tag versions,creation date, last update date, and author/contributor information.
* Table Of Contents should be considered in the case of long CSS files.
* New comments should go directly above the line they reference.
* Use consistent text indentation and formatting to keep comments uniform throughout the document.
* _Optional:_ Special character groups such as `~$~`, `~@~`, or `~#~` could be used to mark specific elements within the document for easier locating with a program's "find" function.

EXAMPLES:

#####*Header information:*#####

```css
/***************************************
* Special Promo Generator Ver 0.5 - Beta
* Authored by Chad Fillion
* 
* Created on: 2-3-14.
* Last Update: 2-6-14 
****************************************/
```

#####*Section Headers:*#####

```css
/* ================================
   Global Styles | Overwrite
================================ */
```

#####*Sub-Section Headers:*#####

```css
/* Form styles
================================ */
```

#####*Single Line Comment:*#####

```css
/* Header color */
```

#####*Multiple Line Comment:*#####

```css
/* The header color should match the logo
 * color and be certain that the font color
 * has enough contrast so the text stands out 
 */
```
<a name="order"></a>
### 4. Declaration Order###
Declarations are to be ordered following this principle:
* Alphabetically sort declarations if there are no more than 10 rules.
* If there are more than 10 rules, Cluster all related properties together (see below).

For long list declarations the rules should be clustered into 5 discernable chunks: **Positioning**, **Display**, **Stylizing**, **Transforms**, &amp; **Animation** with the `@-keyframes` rule set and its vendor prefixed versions grouped directly after the declared animation. Single line comments should be used to separate the rules as needed. 

```css 
/* ALPHABETICAL ( no more than 10 rules ): */ 
h4 {
  color: #990000;
	font-weight: bold;
	margin: 0 auto;
	margin-bottom: 10px;
	padding: 5px;
  width: 90%;
  }
```

```css
/* ALPHABETICAL W/ Positioning  ( 10 rules or less ) */
h4 {
	color: #990000;
	margin-bottom: 10px;
	padding: 5px;
	position: relative;
    top: 20px;
    right: 10px;
	width: 90%;
	z-index: 2;
  }
```
```css
/* Long Rule list clustered: */
.selector {
  /* Positioning */
  position: absolute;
    top: 0;
    right: 0;
    left: 0;
  z-index: 10;       

/* Display & Box Model */
  border: 10px solid #333;
  display: inline-block;
  margin: 10px;
  overflow: hidden;
  padding: 10px;
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
       -o-box-sizing: border-box;
          box-sizing: border-box;

/* Stylizing */
  background: #000;
  color: #fff;
  font-family: sans-serif;
  font-size: 16px;
  text-align: right;

/* Transforms / Transitions */
  -webkit-transform: rotate(7deg;
      -ie-transform: rotate(7deg;
          transform: rotate(7deg;

/* Animation */
  -webkit-animation: myfade 5s linear;
      -ie-animation: myfade 5s linear;
          animation: myfade 5s linear;
  }
  
  @-webkit-keyframes myfade {
    0%   { opacity: 0; }
    100% { opacity: 1; }
  }
  
  @-moz-keyframes myfade {
    0%   { opacity: 0; }
    100% { opacity: 1; }
  }

  @-o-keyframes myfade {
    0%   { opacity: 0; }
    100% { opacity: 1; }
  }
  
  @keyframes myfade {
    0%   { opacity: 0; }
    100% { opacity: 1; }
  }
```

<a name="format"></a>
### 5. Formatting###
Formatting the code for multiple users is critical for accessibility and editing purposes. It ensures that code is: easy to read; easy to clearly comment; is minimized of the chance of accidentally introducing errors to the final rendering. We would like to adhere to the following standards:
*	Separate each rule set by a blank line.
*	Use one discrete selector per line in multi-selector rule sets.
*	Include one declaration per line in a declaration block.
*	Use one level of indentation for each declaration.
*	Include a single space after the colon of a declaration.
*	Include a single space before the opening brace of a rule set.
*	Use lowercase and shorthand hex values, e.g., `#aaa`.
*	Use single or double quotes consistently. Preference is for double quotes, e.g., `content: ""`.
*	Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
*	Where allowed, avoid specifying units for zero-values, e.g.,` margin: 0`.
*	Include a space after each comma in comma-separated property or function values.
*	Include a semi-colon at the end of the last declaration in a declaration block, no space before.
*	Place the closing brace of a rule set in the same column as the first character of the rule set.

#####*Special Case formatting:*#####
* `min` and `max` rules should directly follow the parent declaration with no additioanl indents
* **With position rules:** list **clockwise** starting with `top` and indent 1 level directly below the parent `position` rule.
*	**Vendor prefixed rules** should **Always** go at the bottom of the list.
*	*	Large blocks of single declarations can use a slightly different, single-line format.(see below)
*	In the case of single-line formatting, a space should be included after the opening brace and before the closing brace.
*	Long, comma-separated property values - such as collections of gradients or shadows - can be arranged across multiple lines.
*	A reverse stairstep should be the sort order of all prefixed rules.
*	Indent vendor prefixed rules with **spaces** so that the colons all line up, ending with the non-pefixed rule last.

#####*Special Case Example:*#####

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }

.selector-4 {
  background-image:
    linear-gradient(#fff, #ccc),
    linear-gradient(#f3c, #4ec);
  box-shadow:
    1px 1px 1px #000,
    2px 2px 1px 1px #ccc inset;
  }

.selector-5 {
  /* Positioning */
  position: absolute;
    top: 0;
    right: 0;
    left: 0;
  z-index: 10;       

  /* Display & Box Model */
  border: 10px solid #333;
  display: inline-block;
  height: 200px;
  max-height: auto;
  margin: 10px;
  overflow: hidden;
  padding: 10px;
  width: auto;
  min-width: 50px;
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
       -o-box-sizing: border-box;
          box-sizing: border-box;
  }
```

**NOTE:** You can format the Dreamweaver editor environment to adhere to these simple principals as a baseline by going to Edit > Preferences [CTRL/CMD + U]. Select  “Code Format” and then select the “Advanced Formatting: CSS…”

<a name="ack"></a>
### 6. Acknowledgements###

Special thank you to Niclas Gallagher for the inspiration. [github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).

Thank you to all who have, and might still, contributed to this project.


<a name="lic"></a>
### 7. License###
_Garnet Hill CSS formatting Guide_ by Chad Fillion is
licensed under the [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). This applies to all
documents and translations in this repository.
