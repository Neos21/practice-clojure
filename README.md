# Practice Clojure

Practice [Clojure](https://clojure.org/) With [Leiningen](https://leiningen.org/).

- Setup By MacOS Homebrew

```bash
$ type java
java is hashed (/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/bin/java)
$ java -version
Picked up _JAVA_OPTIONS: -Dfile.encoding=UTF-8
java version "1.8.0_202"
Java(TM) SE Runtime Environment (build 1.8.0_202-b08)
Java HotSpot(TM) 64-Bit Server VM (build 25.202-b08, mixed mode)

$ brew install leiningen

$ lein version
Leiningen 2.9.10 on Java 1.8.0_202 Java HotSpot(TM) 64-Bit Server VM
```

- REPL

```bash
$ lein repl
nREPL server started on port 53031 on host 127.0.0.1 - nrepl://127.0.0.1:53031
REPL-y 0.5.1, nREPL 0.9.0
Clojure 1.11.1
Java HotSpot(TM) 64-Bit Server VM 1.8.0_202-b08
    Docs: (doc function-name-here)
          (find-doc "part-of-name-here")
  Source: (source function-name-here)
 Javadoc: (javadoc java-object-or-class-here)
    Exit: Control+D or (exit) or (quit)
 Results: Stored in vars *1, *2, *3, an exception in *e

user=> (println "Hello World")
Hello World
nil
user=> (exit)
Bye for now!
```

- Create Project From App Template

```bash
$ lein new app practice-clojure
Generating a project called practice-clojure based on the 'app' template.

$ tree -a ./practice-clojure/
./practice-clojure/
├── .gitignore
├── .hgignore
├── CHANGELOG.md
├── LICENSE
├── README.md
├── doc
│   └── intro.md
├── project.clj
├── resources
├── src
│   └── practice_clojure
│       └── core.clj
└── test
    └── practice_clojure
        └── core_test.clj
6 directories, 9 files
```

- Run Project

```bash
$ lein run
Hello, World!
```

- Check

```bash
$ lein check
Compiling namespace practice-clojure.core

# Has Error
$ lein check
Compiling namespace practice-clojure.core
Syntax error compiling at (practice_clojure/core.clj:4:1).
Unable to resolve symbol: XXXXX in this context

Full report at:
/var/folders/nd/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/T/clojure-000000000000000000.edn
Failed.
```

- Unit Test

```bash
$ lein test

lein test practice-clojure.core-test

lein test :only practice-clojure.core-test/a-test

FAIL in (a-test) (core_test.clj:7)
FIXME, I fail.
expected: (= 0 1)
  actual: (not (= 0 1))

Ran 1 tests containing 1 assertions.
1 failures, 0 errors.
Subprocess failed (exit code: 1)
```

- Build

```bash
# Remove `./target/` Directory
$ lein clean

# Build
$ lein uberjar
Compiling practice-clojure.core
Created /Users/Neo/practice-clojure/practice-clojure/target/default+uberjar/practice-clojure-0.1.0-SNAPSHOT.jar
Created /Users/Neo/practice-clojure/practice-clojure/target/default+uberjar/practice-clojure-0.1.0-SNAPSHOT-standalone.jar

# Execute With `java` Command (4.8MB)
$ java -jar ./target/default+uberjar/practice-clojure-0.1.0-SNAPSHOT-standalone.jar
Hello, World!

# Normal JAR (14KB)
$ java -jar ./target/default+uberjar/practice-clojure-0.1.0-SNAPSHOT.jar
Exception in thread "main" java.lang.NoClassDefFoundError: clojure/lang/Var
        at practice_clojure.core.<clinit>(Unknown Source)
Caused by: java.lang.ClassNotFoundException: clojure.lang.Var
        at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:349)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
        ... 1 more
```


## Links

- [Neo's World](https://neos21.net/)
