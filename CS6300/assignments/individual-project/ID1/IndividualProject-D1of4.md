# ***Individual Project: TransmuteTxt***

***Deliverable 1***
## ***Project Goals***

***In this project, you will be developing a Java application, transmutetxt, using an agile, test-driven development process across multiple deliverables. For this assignment you will use version 17 of the Java Development Kit. You will receive one grade for the entire project, but each deliverable must be completed by its own due date and all deliverables will contribute to the overall project grade.***
## ***Specification***

`transmutetxt`*** is a command-line utility written in Java with the following specification:***
### ***Summary***

`transmutetxt`*** allows for simple text manipulation of the contents of a file.***
### ***Syntax***

    transmutetxt [OPTIONS] FILE
### ***Description***

***The program transmutetxt performs basic text transformation on the lines of text from an input file. It is invoked as a command-line tool using the syntax described above, after compilation. The program writes the transformed text to the standard output and errors or usage messages to the standard error without modifying the input file. The FILE parameter is required and must be the last parameter as shown above. The only options allowed in the program, which are optional, delimited by the left [ and right ] brackets, may be provided in any order and are described as follows:***
| ***Option*** | ***Description*** |
| --- | --- |
| `-t <num>` | ***Truncate Lines: Truncate each line to at most <num> characters. The parameter <num> must be an integer between 0 and 100 (inclusive).*** |
| `-x` | ***Remove Empty Lines: Remove all empty lines from the input. This option takes no parameters.*** |
| `-r <old> <new>` | ***Replace Text: Replaces the first occurrence of non-empty substring <old> in each line with string <new>. The search is case-sensitive. This option is mutually exclusive with –f.*** |
| `-f <style> <substring>` | ***Format Text: Replaces the first instance of non-empty string <substring> in each line with the formatted version according to <style>. The search is case-sensitive. The <style> parameter can only be one of three case-sensitive string values: "bold", "italic", or "code". This option is mutually exclusive with –r.*** ***The “bold” string parameter adds double asterisks ** at the beginning and end of the substring.*** ***The “italic” string parameter adds a single asterisk * at the beginning and end of the substring.*** ***The “code” string parameter adds a single backtick ` at the beginning and end of the substring.*** |
| `-g` | ***Global Replace: Replaces all occurrences of substring in each line with the formatted version. This option is used with the ***`-f `***flag only. The search is case-sensitive.*** |
| `-n` | ***Add Line Number: Add line numbers at the beginning of each line. Line numbering starts at 1 and increases by 1 for each subsequent line. Print the number as-is, followed by one space, then the line content.*** |

#### ***Order of execution***

***The last command-line parameter provided is always treated as the filename, as shown in the syntax section, while ***`OPTIONS`*** flags can appear in any order and parsed as they appear from left to right. This means that the following two commands are equivalent when executed on the command line:***
| ***Example 1*** | `transmutetxt`*** ***`-x -n input.txt` |
| --- | --- |
| ***Example 2*** | `transmutetxt`*** ***`-n -x input.txt` |

***In the above examples, (Example 1) parses ***`-x`*** first, then ***`-n`***, and finally ***`input.txt`*** while (Example 2) parses ***`-n`*** first, then ***`-x`***, and finally input.txt. These two examples will result in the same output (assuming that the same ***`input.txt`*** is used for both) because the parsing of options is independent of their execution order. The order of execution for each option is given in the diagram below (note that the colors and border lines are there for ease of viewing):***

***The above diagram of the execution order of options can also be described as follows:***
1. ***If –g is present, then –f should be followed, and all substrings are replaced with the formatted string.***
2. ***If -r or –f is present, then each line is modified according to their respective parameters.***
3. ***If -n is present, then line numbers are added to the beginning of each line.***
4. ***If -t is present, then each line is truncated at most the length according to the given parameter.***
5. ***If -x is present, then all empty lines are removed.***
#### ***Requirements***

- ***To keep this application simple, all errors shall result in the display of the standard usage message:***
    Usage: transmutetxt [ -g | -f style substring | -r old new | -n | -t num | -x ] FILE
- ***An empty input file shall produce an empty output. The Examples section below shows a case of an empty input file.***
##### ***Java***

- ***You shall assume that the command line parameter strings will not contain newline characters (***`\r`***, ***`\n`***, ***`\r\n`***) as the behavior of the program would be platform dependent and may result in error during grading. Therefore there should be no test cases using these values as option parameters. Additionally, you may assume that your application will be called with valid ***`String[]`*** args.***
- ***Make sure not to make calls to ***`System.exit()`*** within your tests, as that creates problems for JUnit.***
##### ***Options***

- ***If options are repeated, only their last occurrence is applied. The Examples section below shows a case of repeated options.***

#### ***Program errors***

##### ***FILE errors***

- ***The last line of a non-empty input file must be terminated by a newline. If the non-empty input file does not terminate in a newline, the program shall generate an error.***
- ***The last parameter is always assumed to be a path to the input file. Omitting it shall result in an error otherwise.***
##### ***Option errors***

- ***Parameters are required for any program option that takes parameters. Omitting a required parameter shall result in an error. The Examples section below shows a case of missing option parameters.***
- ***Any unrecognized option shall result in an error.***
***The cases below show scenarios where transmutetxt shall result in an error according to a specific option.***
| ***Options*** | ***Error Cases*** |
| --- | --- |
| `-t` | ***Providing a non-integer as the maximum length.*** ***Providing an integer outside of the inclusive range 0 to 100  as the maximum length.*** |
| `-r` | ***Providing an empty string as the old parameter.*** ***Specifying options –r with –f.*** |
| `-f` | ***Providing a style parameter outside of the allowed values (‘bold’, ‘italic’, or ‘code’).*** ***Providing an empty string as the substring parameter.*** ***Specifying options –f with –r.*** |
| `-g` | ***Specifying options –g without –f.*** |

### ***Examples of Usage***

***The examples described here can also be seen in JUnit 5 form on the ***`MainTest.java`*** file provided to you in the below sections. In the following, "***`↵`***" represents a newline character.***
| ***Example 1*** |
| --- |
| `transmutetxt sample.txt` |
| `input sample.txt` |  |
| `stdout` | `nothing sent to stdout` |
| `stderr` | `nothing sent to stderr` |

| ***Example 2*** |
| --- |
| `transmutetxt -n -t 50 sample.txt` |
| `input sample.txt` | `↵` |
| `stdout` | `1 ↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 3*** |
| --- |
| `transmutetxt -t -10 sample.txt` |
| `input sample.txt` | `Hello, world!↵` `↵` `How are you?↵` |
| `stdout` | `nothing sent to stdout` |
| `stderr` | `Usage: transmutetxt [ -g | -f style substring | -r old new | -n | -t num | -x ] FILE` |

| ***Example 4*** |
| --- |
| `transmutetxt –t 5 sample.txt` |
| `input sample.txt` | `Okay, let’s start counting. ↵` `One and... ↵` `Two and... ↵` `Three and... ↵` |
| `stdout` | `Okay,↵` `One a↵` `Two a↵` `Three↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 5*** |
| --- |
| `transmutetxt -x sample.txt` |
| `input sample.txt` | `Line 1↵` `Line 2↵` `↵` `↵` `Line k↵` |
| `stdout` | `Line 1↵` `Line 2↵` `Line k↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 6*** |
| --- |
| `transmutetxt -r normal special sample.txt` |
| `input sample.txt` | `This is a normal text file.↵` `Perhaps too normal.↵` `Or not Normal at all.↵` |
| `stdout` | `This is a special text file.↵` `Perhaps too special.↵` `Or not Normal at all.↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 7*** |
| --- |
| `transmutetxt -f bold normal sample.txt` |
| `input sample.txt` | `This is a normal text file.↵` `Perhaps too normal.↵` `Or not Normal at all.↵` |
| `stdout` | `This is a **normal** text file.↵` `Perhaps too **normal**.↵` `Or not Normal at all.↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 8*** |
| --- |
| `transmutetxt -g -f italic Hello sample.txt` |
| `input sample.txt` | `Hello World. Hello Java.↵` `↵` `hello World. Hello Java.↵` |
| `stdout` | `*Hello* World. *Hello* Java.↵` `↵` `hello World. *Hello* Java.↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 9*** |
| --- |
| `transmutetxt -n sample.txt` |
| `input sample.txt` | `Line 1.↵` `Line 2.↵` `Line 3.↵` |
| `stdout` | `1 Line 1.↵` `2 Line 2.↵` `3 Line 3.↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 10*** |
| --- |
| `transmutetxt –x -n sample.txt` |
| `input sample.txt` | `Line 1.↵` `↵` `Line 2.↵` `↵` `Line 3.↵` |
| `stdout` | `1 Line 1.↵` `2 ↵` `3 Line 2.↵` `4 ↵` `5 Line 3.↵` |
| `stderr` | `nothing sent to stderr` |

| ***Example 11*** |
| --- |
| `transmutetxt –t 10 –x -f code Hello –g -n sample.txt` |
| `input sample.txt` | `Hello World. Hello Java.↵` `↵` `hello World. Hello Java.↵` |
| `stdout` | `1 `Hello` ↵` `2 ↵` `3 hello Wo↵` |
| `stderr` | `nothing sent to stderr` |

## ***Deliverables Summary***

***This part of the document is provided to help you track where you are in the individual project. This section will be updated in future deliverables.***
### ***Deliverable 1***

***Provided***
- `transmutetxt `***specification (linked in this document above)***
- ***Skeleton of the main class for transmutetxt (linked below)***
- ***JUnit 5 example tests and skeleton of test class to submit (linked below)***
- ***JUnit 5 library (linked below)***
***Expected***
- ***Part I (Category partition)***
  - ***catpart.txt: TSL file you created***
  - ***catpart.txt.tsl: test specifications generated by the TSLCompiler tool when run on your TSL file***
- ***Part II (JUnit tests)***
  - ***MyMainTest.java: JUnit tests derived from your category partition test frames***

### ***Deliverable 2***

***Provided: TBD***
***Expected: TBD***
### ***Deliverable 3***

***Provided: TBD***
***Expected: TBD***
### ***Deliverable 4***

***Provided: TBD***
***Expected: TBD***
## ***Instructions***

***Deliverable 1 is split up in two parts: Part I and Part II. Follow the instructions for each of the parts as described below.***
### ***Part I***

***Your task for this deliverable is to generate 50 to 90 (inclusive) test frames for the transmutetxt utility using the category-partition method presented in lesson P4L2. Make sure to watch the lesson and demo before getting started.***
***When defining your test specifications, your goal is to suitably cover the domain of the application under test, including relevant erroneous input and input combinations. For example, if you were testing a calculator, you may want to cover the case of division by zero.***
***Do not manually generate combinations of inputs as single choices. Instead, use multiple categories and choices with necessary constraints for the tool to generate meaningful combinations. Using the calculator example, you should not offer choices "add", "multiple", and also "add and multiply" in a single category - an example of what not to do can be found in  ***[calculator-manual-combinations.txt](https://gtvault-my.sharepoint.com/:t:/g/personal/stran63_gatech_edu/IQCZAoiJhyEIS5JdPEVNCL5oAVanM9Z5sKqBSaOdoSMGC4E?e=YDHA4U)***. In particular, make sure to use constraints (error and single), selector expressions (if), and properties appropriately, rather than eliminating choices, to keep the number of test cases within the 50 to 90 inclusive range.***
***The domain for this assignment is the Java application, so anything that the shell would reject, such as unmatched double quotes, will not reach the application. This means that you must test for invalid input arguments (such as Example 3 above), but you don't need to test for errors involving parsing the command-line arguments before they're sent to the Java application. In addition, you may assume that main will be called with a valid ***`args`*** array, meaning that values like ***`null`*** will not be passed.***
#### ***Tools and Useful Files***

##### ***TSLCompiler***

***You will use the ***[TSLCompiler](https://github.com/divark/TSLCompiler)*** tool to generate test frames starting from a TSL file, similar to what we did in the demo for lesson P4L2. Versions of the TSLCompiler for Linux, Mac OS, and Windows, together with a user manual, are available at:***
- [TSLCompiler manual](https://github.com/divark/TSLCompiler/blob/main/docs/USER_MANUAL.md)
- [TSLCompiler for Linux (Any distro released since 2022)](https://github.com/divark/TSLCompiler/releases/download/v1.0.10/tslcompiler-ubuntu-22.04.tar.xz)
- [TSLCompiler for macOS](https://github.com/divark/TSLCompiler/releases/download/v1.0.10/tslcompiler-macos-latest.tar.xz)
- [TSLCompiler for Windows](https://github.com/divark/TSLCompiler/releases/download/v1.0.10/tslcompiler-windows-latest.zip)
***We are also providing the TSL file for the example used in the lesson, ***[cp-example.txt,](https://gtvault-my.sharepoint.com/:t:/g/personal/stran63_gatech_edu/IQD1wsNOWJRZQrWifUA7v17KAbdacZcYz9axs2uXtRLFLpg?e=df93NH)*** for reference, as well as an example for explaining ***`<n/a>`*** values, ***[tsl-na-example.md](https://gtvault-my.sharepoint.com/:t:/g/personal/stran63_gatech_edu/IQBekZ80lLNKTJ7pRRfii3x7ATZUOQXmlWIsiuvyjAp957o?e=q9k6k8)***.***
***Since the TSLCompiler is a command-line tool, it must be run from the command line, as we do in the video demo, rather than by clicking on them. The recommended syntax for running the tool is***
    ./tslcompiler [-o outfile] infile
***where ***`infile`*** is the input file to the TSL program, i.e., the catpart.txt file, and ***`outfile `***is an optional name for the name of the output file, i.e., catpart.txt.tsl. To learn more about the tool, please consult the manual referenced above.***
***If you encounter issues while using the tool, please post a public question on Ed Discussion. For reference, Gradescope will execute the tool on a Linux platform.***
#### ***Committing Part I***

1. ***Create a directory "***`IndividualProject`***" in the personal GitHub repo we assigned to you.***
2. ***Add the following two text files to this new directory:***
  1. `catpart.txt`***: TSL file you created.***
  2. `catpart.txt.tsl`***: 50 to 90 (inclusive) test-case specifications generated by the TSLCompiler tool when it processes your TSL file.***
3. ***Commit and push your files to GitHub.***

### ***Part II***

***In this second part of the deliverable, you will create actual test cases implementing the test specifications you created in Part I. As discussed in the lesson on the category-partition method, each test frame is a test specification that can be instantiated as an individual concrete test case. To do so, you should perform the following tests:***
1. ***Download archive ***[individualproject-d1.tar.gz.](https://gtvault-my.sharepoint.com/:u:/g/personal/stran63_gatech_edu/IQCakuGIqPvvSboXYwrBDE_-AQ-Yvlo6lcBaEV8bm_UdTNQ?e=dL7AMw)*** ***
2. ***Unpack the archive in the directory "***`IndividualProject`***", which you created in Part I of the deliverable. Hereafter, we will refer to this directory as ***`<dir>`***. After unpacking, you should see the following structure:***
  1. `<dir>/transmutetxt/src/edu/gatech/seclass/transmutetxt/Main.java`
***This is a skeleton of the ***`Main`*** class of the transmutetxt utility, which we provide so that the test cases for transmutetxt can be compiled. It contains an empty main method and a method usage, which prints, on standard error, a usage message that should be called when the program is invoked incorrectly. In case you wonder, this method is provided for consistency in test results.***
  2. `<dir>/transmutetxt/test/edu/gatech/seclass/transmutetxt/MainTest.java`
***This is a test class with a few test cases for the transmutetxt utility that you can use as an example; it corresponds to the examples of usage of transmutetxt that we provided. In addition to providing this initial set of tests, class ***`MainTest`*** also provides some utility extensions and methods that you can leverage/adapt and that may help you implement your own test cases. We encourage you to use the methods to ease your design process.***
  3. `<dir>/transmutetxt/test/edu/gatech/seclass/transmutetxt/MyMainTest.java`
***This is an empty test class in which you will add your test cases, provided for your convenience.***
  4. `<dir>/transmutetxt/test/edu/gatech/seclass/transmutetxt/OutputCapture.java`
***This is a JUnit 5 extension class to facilitate capturing the standard output and standard error, which are needed to test the transmutetxt application. It is used on the ***`MainTest.java`*** file for reference and provides two methods to capture output from ***`Main`***.***
  5. `<dir>/transmutetxt/lib/junit-platform-console-standalone-1.9.1.jar`
***JUnit 5 library to be used for the assignment.***
3. ***Use the test frames from Part I to generate additional JUnit test cases for the transmutetxt utility, one per frame, and put them in the test class ***`MyMainTest`***. For ease of test design, it's required that you name your test cases transmutetxt***`Test1`***, transmutetxt***`Test2`***, and so on. It's required that each test contains a concise comment that indicates which test frame the test case implements. It should at least have the following comment format:***
    // Frame #: <test case number in file catpart.txt.tsl>
#### ***Designing your tests***

***Your test frames should contain enough information to create relevant test cases. If you cannot implement your test frames as useful JUnit tests (e.g., because the test frames do not provide enough information), you should revisit Part I. Extending the calculator example, if your test frame specified a numerical input, and you realized that you should use both negative and positive numbers in your JUnit test case, you should revise your categories and choices so that this is reflected in your test frames.***
***If you are uncertain what the result should be for a test, you may make a reasonable assumption on what to use for your test oracle. While you should include a test oracle, we will not grade the accuracy of the test oracle itself. Feel free to reuse and adapt, when creating your test cases, some of the code we provided in the ***`MainTest`*** class. ***`MainTest`*** is provided for your convenience and to help you get started. Whether you leverage the ***`MainTest`*** class or not, your test cases should assume (just like the test cases in ***`MainTest`*** do) that the transmutetxt utility will be executed from the command line, as follows:***
    java -cp <classpath> edu.gatech.seclass.transmutetxt.Main <arguments>
***For this deliverable, do not implement the transmutetxt utility, but only the test cases for it. This means that most, if not all of your test cases will fail, which is expected and fine.***

#### ***Committing Part II and submitting the deliverable***

1. ***As usual, commit and push your code to your individual, assigned private repository.***
2. ***Make sure that all Java files are committed and pushed, including the ones we provided.***
3. ***Make sure to also commit and push the provided libraries (***`lib`*** directory). To do so, you may need to force add the jar files (i.e., "***`git add -f lib/*`***"), since they are typically excluded by the "***`.gitignore`***" file.***
4. ***Check that you committed and pushed all the files you needed by doing the following:***
  1. ***Clone a fresh copy of your personal repo in another directory.***
  2. ***Go to directory ***`IndividualProject/transmutetxt`*** in this fresh clone.***
  3. ***Compile your code. One way to do this is to run, from a Unix-like shell1:***
    javac -cp lib/\* -d classes src/edu/gatech/seclass/transmutetxt/*.java test/edu/gatech/seclass/transmutetxt/*.java
  4. ***Run your tests. Again, from a Unix-like shell, you can run:***
    java -cp classes:lib/\* org.junit.platform.console.ConsoleLauncher --select-class edu.gatech.seclass.transmutetxt.MyMainTest2
5. ***Submit on Gradescope a file called submission.txt that contains, in two separate lines, (1) your GT username and (2) the commit ID for your submission. For example, the contents of submission.txt for George P. Burdell could look something like the following:***
***submission.txt***
| `gpburdell1` |
| --- |
| `81b2f59` |

***As soon as you submit, Gradescope will verify your submission by making sure that your files are present and in the correct location, as well as a few additional minor checks.3 If you pass all of these checks, you will see a placeholder grade of 10 and a positive message from Gradescope. Otherwise, you will see a grade of 0 and an error message with some diagnostic information. Please note that:***
- ***a positive response from Gradescope only indicates that you passed the initial checks and is meant to prevent a number of trivial errors;***
- ***if your submission does not pass the Gradescope checks, it will receive a 0, so please make sure to pay attention to the feedback you receive when you submit and keep in mind that you can resubmit as many times as you want before the deadline. Once the assignment closes, we will not be able to regrade assignments that fail these Gradescope checks.***
## ***Gradescope Queries***

***If you need clarification or have questions regarding Gradescope output, please post privately on Ed Discussion (we will make it public if appropriate) and make sure to add a link to the Gradescope results and any information that may be relevant.***
***The bottom line is that, to make the interaction efficient, you should make your posts as self-contained and easy-to-check as possible. The faster we can respond to the posts, the more students we can help.***

## ***FAQ***

1. ***What's in Deliverable 2? What is the workload like?***
***Answer: In fairness to everyone, we cannot discuss future deliverables. You will have to wait to find out the details of deliverable 2 when it’s released.***
2. ***Can I create additional tests not generated by TSL or avoid implementing some of the generated test frames?***
***Answer: No, for part 2 you can only use the test frames that were generated in part 1.***
3. ***Aside from the program options and parameters, should the file be considered as a separate category partition?***
***Answer: Yes, the file is also an input to the program, so it should be considered when testing.***
4. ***Should I test the size limits/capabilities of strings, input files, and others?***
***Answer: Although there are no restrictions on your test suite design, testing the limits of data types and file sizes is out of the scope for this assignment.***
5. ***Is it okay that most of my tests are failing locally?***
***Answer: Yes, that's no problem. This is expected since the main method is empty, so most tests won't pass.***
6. ***Can I re-use the example test cases (input strings, arguments, etc.) or test methods for my own test cases?***
***Answer: Yes, you may (and are encouraged to) use the example test cases to devise your own, in addition to using the structure and test methods provided.***
