# Template for CLJC libraries

[![Clojars](https://img.shields.io/clojars/v/io.helins/templ-lib.cljc.svg)](https://clojars.org/io.helins/templ-lib.cljc)

Template for [clj-new](https://github.com/seancorfield/clj-new) aimed at creating
CLJC libraries.

Provides a workflow adapted for working in Clojure and Clojurescript at the
same time. Based around [deps](https://clojure.org/reference/deps_and_cli), the
Clojurescript parts being handled by
[Shadow-CLJS](https://github.com/thheller/shadow-cljs).

Testing is done via [Kaocha](https://github.com/lambdaisland/kaocha) on the JVM
and Shadow-CLJS for Clojurescript.

Created repository is aimed to be managed with [Babashka](https://github.com/babashka/babashka), a wonderful
tool for any Clojurist that provides a powerful task runner. A default `bb.edn` file is generated with a set
of common tasks:

```shell
$ bb tasks

The following tasks are available:

cp                 Print the classpath
cp:del             Delete cached classpath
deploy             Deploy this project to Clojars ; need username and path to file with Clojars token
devclojure         Start Clojure JVM dev environment (NREPL on port 14563)
dev:cljs           Start CLJS dev environment (NREPL on port 14563, server on port 8000)
install            Install jar to local Maven repo
jar                Build a jar for this project
lint               Start Clj-kondo on './src' (further path can be provided as command-line argument)
lint:import        Initialize Clj-kondo and copy configuration files from dependencies
pom                Sync POM file with 'deps.edn'
shadow:clean       Remove the given profile from Shadow-CLJS cache (for full recompilation)
shadow:clean-test  Like 'shadow:clean' but for the ':test-node' profile
test:jvm           Run tests on the JVM once ; accepts Kaocha CLI arguments
test:jvm:watch     Run tests on the JVM everytime a file is changed ; accepts Kaocha CLI arguments
test:node          Run tests on NodeJS after unoptimized compilation
test:node:optimize Run tests on NodeJS after advanced compilation
```


## Usage

In `~/.clojure/deps.edn`, add an alias such as (substituting `$VERSION`):

```clojure
{:alias
 {:new-lib-cljc
  {:extra-deps {io.helins/templ-lib.cljc {:mvn/version "$VERSION"}}
   :exec-args  {:template helins-lib-cljc}
   :exec-fn    clj-new/create}
```

Creating a new project:

```shell
$ clj -X:new-lib-cljc :name your-group/project-name
```


## Extra

The `./extra` directory contains additional files, not part of the template, but which the user might be interested in.
Currently, it only holds an example of a CircleCI configuration file.


## License

Copyright © 2021 Adam Helinski and Contributors

Licensed under the term of the Mozilla Public License 2.0, see LICENSE.
