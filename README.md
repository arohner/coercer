# Coercer

A library for converting data of one type into another type.

## Installation

Add the following dependency to your `project.clj` file:

    [coercer "0.1.1"]

## Usage

Use the `coerce` multimethod to convert between types:

```clojure
(use 'coercer.core)

(coerce 1 String)      ; => "1"
(coerce "5.5" Double)  ; => 5.5
(coerce "foo" Keyword) ; => :foo
(coerce :abc String)   ; => "abc"

(use '[clj-time.core :only (now)])
(import 'java.util.Date)

(coerce (now) String)       ; => "2012-04-17T20:53:55.552Z"
(coerce (now) Long)         ; => 1334696086921
(coerce 1334696086921 Date) ; => #<Date Tue Apr 17 21:54:46 BST 2012>
```

Currently `coerce` supports the following types by default:

* java.lang.String
* java.lang.Integer
* java.lang.Long
* java.lang.Float
* java.lang.Double
* clojure.lang.Keyword
* clojure.lang.Symbol
* java.util.Date
* org.joda.time.DateTime

## License

Copyright © 2012 James Reeves

Distributed under the Eclipse Public License, the same as Clojure.
