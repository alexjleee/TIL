# Regular Expressions Basics

Regular Expressions (_regex_ for short) are special text strings used to search patterns within text.
- Regex is used in many different languages, such as JS, Python, PHP, Ruby, Java and so on.
- Regex is useful in extracting, validating, parsing or replacing information from strings.

## Basic Syntax
`/regex/flag`
- The forward slashes (`/`) indicate the start and end of a regex.
- At the end of regex, you can add _flags_
  - `g` : global search : search for all the matches (without it, regex only searches for a single match)
  - `i` : ignore case : make regex case-insensitive


## Character Classes
- [abc] : character set : match any character in the set
  - `/[abc]/g` : A **c**ute **ca**t
- [^abc] : negated set : match any character NOT in the set
  - `/[^abc]/g` : **A** c**ute** ca**t**
- [a-z] : range : match any character in the range
  - `/[a-z]/g` : T**he** M**oon**
- . : dot : match any character except linebreak
  - `/./g` : **ABC abc 012 ?!.**
- \w : word : match any word character (alphanumeric & _)
  - `/\w/g` : **contact** : (**123**) **456** - **7890**
- \W : not word : match any character except word character
  - `/\w/g` : contact **: (**123**)** 456 **-** 7890
- \d : digit : match any digit character (0-9)
  - `/\d/g` : Call **911** !
- \D : not digit : match any character except digit character
  - `/\D/g` : **Call** 911 **!**
- \s : whitespace : match any whitespace (spaces, tabs, linebreaks)
- \S : not whitespace : match any character except whitespace character

## Quantifiers
- {1,2} : quantifier : between 1 and 2
  - `/c\w{2,3}/g` : **cat cara**mel **code cod cas**tle
  - `/c\w{3,}/g` : cat **caramel code** cod **castle**
- \+ : plus : 1 or more
  - `/colou+r/g` : color **colour colouur colouuur**
- \* : star : 0 or more
  - `/colou+r/g` : **color colour colouur colouuur**  
- ? : optional : 0 or 1
  - `/colou+r/g` : **color colour** colouur colouuur

## Alternations
- | : alternation : match expression before OR after the |
  - `/(c|b)at/g` : **cat bat** mat fat hat

## Anchors
- ^ : beginning : match the beginning of a string
  - `/^w+/g` : **Beginning** of a string
- $ : end : match the end of a string
  - `/\w+$/g` : End of a **string**
- \b : word boundary : match a word boundary
  - `/\ba/g` : **a**ll the data **a**ccessible
- \B : not word boundary : match any character not a word boundary
  - `/a\B/g` : **a**ll the d**a**ta **a**ccessible

## Groups
- (abc) : capturing group
  - `/(\d{3})[ -]?(\d{3})[ -]?(\d{4})/g` : 123 456 7890 -> group#1 123, group#2 456, group#3 7890
- (?:abc) : non-capturing group
  - `/(\d{3})[ -]?(?:\d{3})[ -]?(?:\d{4})/g` : 123 456 7890 -> group#1 123
- (?<name>abc) : named capturing group
  - `/(?<areacode>\d{3})[ -]?(?:\d{3})[ -]?(?:\d{4})/g` : 123 456 7890 -> areacode 123

## Lookaround
- a(?=b) : positive lookahead : match 'a' only if it is followed by 'b'
  - `/\d+(?=\s?dollars?)/g` : **15** dollars, **1** dollar, five dollars
- a(?!b) : negative lookahead : match 'a' only if it is NOT followed by 'b'
  - `/\d+(?!\$)/g` : 1$ **5**€ **10**£ **1000**₩ **10**
- (?<=a)b : positive lookbehind : match 'a' only if there is 'b' before it
  - `/(?<=[tT]he )\w+/g` : The **Fox** and the **Hound**
- (?<!a)b : negative lookbehind : match 'a' only if there is NO 'b' before it
  - `/(?<![tT]he )\b\w+/g` : **The** Fox **and the** Hound