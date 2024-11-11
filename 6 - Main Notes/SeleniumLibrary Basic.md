2024-11-09 15:56

Tags: 

---

## Introduction
- a web testing library for [[Robot Framework]].
- uses the Selenium WebDriver modules internally to control a web browser
- can use for automation test and automate administration tasks
## Locating elements
- All keywords in SeleniumLibrary that need to interact with an element on a web page take an argument typically named `locator` that specifies how to find the element
### Locator syntax
Different strategies:
	- The element id
	- XPath expressions
	- CSS selectors. 
#### Default locator strategy
- Use the keyword locator strategy (by id or name).
- Some keywords support additional attributes or other values. For example, `Click Link` supports the `href` attribute and the link text and addition to the normal `id` and `name`.
- Examples:

| Keyword | Locator | Note |
| --- | --- | --- |
| Click Element | id: abc | Click element with id `abc` |
| Click Link | href: https://abc.com | Click link with href is  `https:abc.com` | 

If a locator accidentally starts with a prefix recognized as [[Explicit locator strategy]] or [[Implicit XPath strategy]], it is possible to use the explicit `default` prefix to enable the default strategy.

| Keyword | Locator | Note |
| --- | --- | --- |
| Click Element | default:name:abc | Use default strategy with value `name:foo` |


#### Explicit locator strategy
Using either syntax `strategy:value` or `strategy=value`.
Locator strategies that are supported by default are listed in the table below. In addition to them, it is possible to register [custom locators](https://robotframework.org/SeleniumLibrary/SeleniumLibrary.html#Custom%20locators).

| Strategy | Match based on | Example |
| --- | --- | --- | --- | --- |
| id | Element `id` | `id:example` |
| name | `name` attribute. | `name:example`  |
|  identifier |Either `id` or `name`. | `identifier:example` |
| class | Element `class`. | `class:example` |
| tag | Tag name. | `tag:div` |  |  |
| xpath | XPath expression. | `xpath://div[@id="example"]` |
| css | CSS selector. | `css:div#example` |
| dom | DOM expression. | `dom:document.images[5]` |
| link | Exact text a link has. | `link:The example` |
| partial link | Partial link text. | `partial link:he ex` |
| sizzle | Sizzle selector deprecated. | `sizzle:div.example` |
| data | Element `data-*` attribute | `data:id:my_id` |
| jquery | jQuery expression. | `jquery:div.example` |
| default | Keyword specific default behavior. | `default:example` |

#### Implicit XPath strategy

Starts with `//` or multiple opening parenthesis in front of the `//`
Examples:
| Keyword | Locator |
| --- | --- | --- |
| [Click Element](https://robotframework.org/SeleniumLibrary/SeleniumLibrary.html#Click%20Element) | //div[@id="foo"]//h1 |
| [Click Element](https://robotframework.org/SeleniumLibrary/SeleniumLibrary.html#Click%20Element) | (//div)[2] | 

#### Chaining locators

css:.bar >> [xpath://a](xpath://a) means `To find a link which is present after an element with class "bar"`

### Custom locators
#### Create keyword
| Custom Locator Strategy | [Arguments] | ${browser} | ${locator} | ${tag} | ${constraints} |
| --- | --- | --- | --- | --- | --- |
|  | ${element}= | Execute Javascript | return window.document.getElementById('${locator}') |  |  |
|  | return | ${element} |  |  |  |
#### Register keyword
| [Add Location Strategy](https://robotframework.org/SeleniumLibrary/SeleniumLibrary.html#Add%20Location%20Strategy) | custom | Custom Locator Strategy |
| --- | --- | --- |

## Browser and Window
![[Pasted image 20241109155644.png]]

## Timeout, wait, delay
Read in doc


---
# References