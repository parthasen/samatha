Samatha
=======

#### Copyright David Sprigate 2013 ([CC BY 3.0](creativecommons.org/licenses/by/3.0))

Samatha is a package for rendering HTML in R. It is based on the [Hiccup](http://github.com/weavejester/hiccup) library for [Clojure](clojure.org).

Samatha can render html and generic xml to R strings.  The functions are designed to be nested inside one another.

## Install

Samatha is not currently in a state to be built with devtools


```r
load_all(".")
```

```
## Loading samatha
```


## Documentation

Documentation is not yet available but will be on daspringate.github.com

## Syntax

The central function is html:


```r
# The first argument is the html tag:
html("p")
```

```
## [1] "<p  />"
```

```r
# Any strings after that are concatenated to be the content of the tag:
html("p", "This is a Sentence.", " So is this")
```

```
## [1] "<p>This is a Sentence. So is this</p>"
```

```r
# The opts argument defines html tag attributes
html("span", "bar", opts = list(class = "foo"))
```

```
## [1] "<span class=\"foo\">bar</span>"
```

```r
html("span", opts = list(id = "foo", class = "bar"), "baz")
```

```
## [1] "<span id=\"foo\" class=\"bar\">baz</span>"
```

```r
# Tags can be nested inside of tags and everything ends up concatenated
html("p", "Goodbye", html("strong", "cruel"), "world")
```

```
## [1] "<p>Goodbye<strong>cruel</strong>world</p>"
```

```r
# There are CSS-style shortcuts for setting ID and class
html("p#my-p", html("span.pretty", "hey"))
```

```
## [1] "<p id=\"my-p\"><span class=\"pretty\">hey</span></p>"
```

```r
# You can escape a tag using the (escape-html) function
html("p", html("script", "Do something evil", escape.html.p = TRUE))
```

```
## [1] "<p>&lt;script&gt;Do something evil&lt;/script&gt;</p>"
```


There are also wrappers to generate a range of common html elements:
