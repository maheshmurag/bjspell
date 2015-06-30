## Introduction ##
Hunspell is a mature and Open Source project which aim is to bring language spell checkers for everyone and with a wide range of supported languages.
Since JavaScript is not fast as C, Java or other languages are, common browsers are spell-check capable only via plug-ins (e.g. FireFox) or via server side Ajax request.


## About BJSpell ##
The main goal of this project is to make possible "_Hunspell_ _like_" checks runtime and without usage of plug-ins or server side interactions (stress), using best practices to make possible small as large document parsing in a couple of milliseconds.
The basic concept behind BJSpell is **cache** **everything**, starting from a pre "_compiled_" dictionary derived from Hunspell .aff and .dic files plus lazy incremental caching procedure to avoid redundant checks for already verified words.

## Pros ##
  * pure JavaScript implementation (even compiled dictionaries are created via JavaScript, thanks to [Jaxer](http://www.aptana.com/jaxer)), it does **NOT** require Ajax/server-side interactions
  * dictionaries are compiled via Hunspell official .aff or .dic files, it is easily possible to implement your own words in the dictionary and recompile them in a click
  * usage of best JavaScript practices to make possible parsing of large amount of text as well
  * usage of singleton pattern to avoid multiple server calls being able to switch language runtime without server stress
  * the BJSpell file is about **1.12Kb** minified and gzipped, an fast parser for a ridiculous size
  * project entirely focused on performances and a good compromise between spell check reliability, global project size, and browser compatibility
  * highly browser compatible, I could not find a single "_recent_ _browser_", IE6 included ... with a single problem

## Cons ##
  * spell check is case insensitive, a must for hundreds of reasons (so January and january will both pass the check, for example)
  * everything is cached, starting from the dictionary, ending with every possible distinct word a user could write down - requires, with a single dictionary, 1Mb of RAM or more (not ideal, as example, for iPhones with limited amount of ram)
  * dictionaries should be served using best compression practices, as gzip is, to reduce bandwidth, as example, from 934Kb to 250Kb for en\_US dictionary
  * we are still in Internet Explorer era, nowadays the slowest JavaScript implementation ever ... this means that documents with hundred thousands words to parse could slow down old PCs if the browser is IE isntead of FireFox, Chrome, Safari, Opera. The same problem is more evident for current suggestion method
  * the suggestion method is truly rude since I was more focused on speed and runtime spell and nothing else
  * the grammar check is quick and dirty, results could not be perfect as Hunspell results are