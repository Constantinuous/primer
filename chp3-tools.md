# A Primer About Software Engineering
# Chapter 3: Know your Tools

## Write plain text [Pragmatic Programmer]
Plain text will survive and outlive all other file formats and the applications that created them. So write in plain text and have applications store their data in plain text. Html, Xml, Json are great formats for storing structured, generic data. So is Markdown, Restructured Text, LaTex for documents. Csv and Tsv are great for tables. Just make sure the format and namings you pick are human __understandable__.

If you write plain text you can also easily put it in version control and the merge changes from other team members.

### Markdown

You should know what Markdown is. You should know that there are different Markdown flavors.

* [GFM (Github-flavored Markdown) Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

If you want you can use a nice Markdown editor:

* [MarkdownPad (Windows)](http://markdownpad.com/)
* [WriteMonkey (Windows)](http://writemonkey.com/index.php)
* [MacDown (Mac)](http://macdown.uranusjr.com/)
* [Atom](https://atom.io/)
* [Visual Studio Code (Multi)](https://code.visualstudio.com/Download)

## (Git) Bash
Learn how to use Bash. If you are on Windows you should have Git installed anyway, which comes with Git Bash. Open your Bash (on Windows Right-Click->"Open Git Bash Here") and start scripting.

### Find/Grep scripting
*Which Java files have not been changed in the last week?*
`find . -name '*.java' -mtime +7 -print`

*Of these java files, which use the awt Libraries?* 
`find . -name '*.java' -mtime +7 -print | xargs grep 'java.awt'`

*Grep all unique imports in java files*
`grep -ri '^import ' --include=\*.java | sed -e's/.*import *//' | sort | uniq`

*List all directories and sort by size (Limit to top ten)*
`du -m --max-depth 1 | sort -rn`
`du -m --max-depth 1 | sort -rn | head -11`

*List biggest files and sort by size (list only jar files)*
`find . -type f -printf "%k %p\n" | sort -rn | head -11`
`find . -name "*.jar" -type f -printf "%k %p\n" | sort -rn | head -11`

*Grep "some text" recursively in a folder (count files with "some text")*
`grep -r --color "some text"`
`grep -ril "some text" * | wc -l`

*Grep all non-sql files with sql strings (count asp files with sql strings)*
`grep -ril --exclude=\*.sql "\"select.*from" | wc -l`

`grep -ril --include=\*.asp "\"select.*from" | wc -l`
`grep -ril --include=\*.asp "\"update.*set" | wc -l`
`grep -ril --include=\*.asp "\"insert into.*values" | wc -l`
`grep -ril --include=\*.asp "\"delete from" | wc -l`

*Find files with name (with most Lines | top 10)*
`find . -type f -name "*.java" | wc -l`

*List all file names (that are duplicate)*
`find . -type f -printf "%f\n"`
`find . -type f -printf "%f\n" | sort | uniq -cd | sort -rn`

*Find top 100 files with with most Lines (top 10 with ending .java)*
`find . -type f -print0 | wc -l --files0-from=- | sort -rn | head -100`
`find . -type f -iname "*.java" -print0 | wc -l --files0-from=- | sort -rn | head -10`

*Find all file extensions*
`find . -type f -name '*.*' | sed 's|.*\.||' | tr '[:upper:]' '[:lower:]' | sort -u`

### Repository scripting
*Restore all repositories with a .git folder*
`for d in `find . -name .git -type d -prune`; do (cd "$d/.." && git checkout . ); done`

*Remove all .git folders*
`for d in `find . -name .git -type d -prune`; do (rm -r -f $d); done`

*Remove all files with ending .par*
`find . -name "*.par" -type f|xargs rm -f`

## Always put anything in Version Control [Continuous Delivery]
Notice I did not use the term Source Control. CSV, SVN, Git are __version control__ tools. You can put anything in there and you should. 

* Source Code belongs in version control
* Documentation belongs in version control
* Configuration belongs in version control
* Otto, vagrant, ansible files belong in version control
* Initial Database snapshots belong in version control
* [Lambda CD](http://www.lambda.cd/) Build Pipelines as code belong in version control
* Passwords __do not__ belong in version control!

Really anything you need to build and understand the project belong in version control and in the same repository. In the end any new team member should check out one repository and have all the data he needs to build, run and understand the project. 

Your version control should be your single point of truth. You have a version control smell when your team members continuously ask where they can find document x or where to put file y.

You don't need to put Maven, Npm, Nuget dependencies here, but you can if your team wants to. Just don't put your compiled source code here. That is a duplication (sources and the binaries) and we hate duplications!

## Fiddle around
There are many web fiddles where you can try out ideas in many programming languages. A list can be found [here](https://fiddles.io/).

* [.Net](https://dotnetfiddle.net/)
* [JavaScript](https://jsfiddle.net/)
* [JavaScript ES6](https://babeljs.io/repl/)
* [TypeScript(https://www.typescriptlang.org/play/)
* [SQL](http://sqlfiddle.com/)
* [Regex](http://refiddle.com/)
* [Python](http://pythonfiddle.com/)
* [Rust](https://play.rust-lang.org/)
* [Swift](https://swiftlang.ng.bluemix.net/#/repl)

## Shell
Linux has great shell options. Windows, not so much. Powershell is fine but usually it's not enabled due to security reasons or out-of-date. So why not install a serious shell with all the linux goodness? 
* [Git Bash, comes with Git](https://git-for-windows.github.io/). Only a couple core programs.
* [Babun](http://babun.github.io/). Has lots of programs (728 Mb) and has a pre-configured git.  Also has a package manager *pact*.

## Package Manager
* [Chocolatey (Windows)](https://chocolatey.org/)
* [Homebrew (Mac)](http://brew.sh/)
* [NPM which comes with node](https://nodejs.org/en/).
* [Pip which comes with Python >=2.7.9 or 3.4](https://www.python.org/).

## Cool tools
* [Pandoc](http://pandoc.org/): A swiss-army knife for converting one markup format into another (docx, odt, slidy, reveal.js, latex, pdf, markdown, epub etc.). `choco install pandoc` or `brew install pandoc`.
* [Httpie](https://github.com/jkbrzt/httpie): a command line HTTP client. Its goal is to make CLI interaction with web services as human-friendly as possible. POST comments with authentication, submit forms, download/upload files `pip install --upgrade httpie`
* [jq](https://stedolan.github.io/jq/): like sed for JSON data.
* [pup](https://github.com/ericchiang/pup): filter html data with css selectors.
* [CLOC - Count Lines of Code](https://github.com/AlDanial/cloc). cloc counts blank lines, comment lines, and physical lines of source code in many programming languages and can diff them. It can also filter out duplications. `npm install -g cloc` or `choco install cloc` or `brew install cloc`.

## Disk Usage Tools
* [WinDirStat (Windows)](https://windirstat.info/)
* [Disk Inventory X (Mac)](http://www.derlien.com/)

## Tool Collections
* [Coreutils](http://gnuwin32.sourceforge.net/packages/coreutils.htm). The GNU Core Utilities are the basic file, shell and text manipulation utilities of the GNU operating system. `choco install gnuwin32-coreutils.install` or `brew install coreutils`.
* [Moreutils](https://joeyh.name/code/moreutils/) including amongst others *vipe: insert a text editor into a pipe*.
