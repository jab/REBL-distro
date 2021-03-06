# `REBL`

REBL is a graphical, interactive tool for browsing Clojure data. REBL is extracted from Datomic tools developed by the [Datomic Team](https://www.datomic.com/) at [Cognitect](https://cognitect.com), and is available for non-commercial use (per EULA on downloads page) free of charge. We hope that many Clojure developers will find it useful. 

## Features

* A two-pane browser/viewer system for viewing collections and their contents
* Navigation into and back out of nested collections
* A structured editor pane for entering expressions to be evaluated
* A root browse of a history of expression evaluations
* The ability to 'wrap' a stdio based REPL (e.g. Clojure's native REPL) so that it can monitor and display the interactions therein, while still allowing them to flow back to the host (e.g. the editor)
* When used with non-stdio repls (e.g. nREPL), can be launched a la carte and accepts values to inspect via an API call
* The ability to capture nested values as defs in the user namespace
* The ability to run multiple independent UI windows
* Metadata viewing
* Datafy support
* Extensibility to new browsers and viewers
* Full keyboard control via [hotkeys](https://github.com/cognitect-labs/REBL-distro/wiki/Hotkeys)

### NOTE - tap> is not currently wired up in the UI.

![screenshot](screenshot.png)

REBL runs in your application JVM process, and can be used at dev-time without adding any runtime deps. The UI is written in JavaFX.

## Release Status

REBL is early access. Your feedback can help make it better. Please report any [issues](https://github.com/cognitect-labs/REBL-distro/issues) that you encounter.

## Requirements

- Clojure 1.10.0 or higher
- Java 1.8 at 1.8.0_151 or higher
  - or Java 11.0.1 or higher [utilizing these dependencies](https://github.com/cognitect-labs/REBL-distro/wiki/Java-11-Usage)
- core.async (tested with 0.4.490)

## Usage:

[Download REBL](http://rebl.cognitect.com/download.html) and unzip it to your local drive.

Add an alias to (your existing project's) deps.edn with a [local dependency](https://clojure.org/guides/deps_and_cli#local_jar) on the rebl jar file:

``` clj
{:deps {}
 :aliases
 {:rebl {:extra-deps {
	org.clojure/clojure {:mvn/version "1.10.0"}
        org.clojure/core.async {:mvn/version "0.4.490"}
	com.cognitect/rebl {:local/root "/path/to/rebl-VERSION.jar"}}}}}
```

[Java 11 requires a slightly different deps.edn](https://github.com/cognitect-labs/REBL-distro/wiki/Java-11-Usage).

Replace your normal repl invocation (`clj`, or `clojure` e.g. for inferior-lisp) with REBL:

`clj -R:rebl -m cognitect.rebl`

Your repl should start, along with the REBL UI. Everything you type in the repl will also appear in REBL. You can also type expressions right into REBL's editor (in the upper left). REBL will maintain a history of exprs+results in the root browse table.

You can start more UIs with `(cognitect.rebl/ui)`

## Limitations

REBL currently requires Java 1.8 or [Java 11](https://github.com/cognitect-labs/REBL-distro/wiki/Java-11-Usage)
