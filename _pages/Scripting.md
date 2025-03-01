---
autogenerated: true
title: Scripting
layout: page
categories: Scripting
description: test description
---

{% include learn content='scripting' %}ImageJ allows you to write scripts in several different languages.

Getting started
===============

-   Read the [ImageJ tutorial notebooks](https://imagej.github.io/tutorials) to learn how to write ImageJ scripts.
-   Press the {% include key content='\[' %} key to open the [Script Editor](Script_Editor) (or {% include key content='Shift' %}-{% include key content='\[' %} to open the [Script Interpreter](Script_Interpreter)).
-   Optionally, choose a template from the *Templates* menu to get you started.
-   Otherwise, choose your language from the *Language* menu.
-   Grab code snippets for common tasks from the [Scripting toolbox](Scripting_toolbox).
-   See [Scripting comparisons](Scripting_comparisons) for a side-by-side comparison of scripting languages.
-   See [:Category:Scripting](Category_Scripting) for a list of all scripting-related pages on this wiki.

Supported languages
===================

ImageJ's [Script Editor](Script_Editor) supports many different languages. The following table summarizes the possibilities.

<table><tbody><tr class="odd"><td style="white-space: normal !important"><p>Recommended options</p></td><td></td></tr><tr class="even"><td><p><a href="Groovy_Scripting" title="wikilink">Groovy</a></p></td><td><p> {% include wikipedia title='Groovy (programming language)' text='Groovy'%} is a flexible and powerful scripting language, Java-like but less verbose and dynamically typed. Learn this, and using Java later (if needed) will become easier.</p></td></tr><tr class="odd"><td><p><a href="Introduction_into_Macro_Programming" title="wikilink">ImageJ Macro</a></p></td><td><p> The <a href="ImageJ_1.x" title="wikilink">ImageJ 1.x</a> macro language is less powerful than the other scripting languages, but is designed to be easy to learn and use.</p></td></tr><tr class="even"><td style="white-space: nowrap"><p> <a href="Jython_Scripting" title="wikilink">Python (Jython)</a></p></td><td><p> {% include wikipedia title='Python (programming language)' text='Python'%} is a popular choice among scientists.</p></td></tr><tr class="odd"><td><p><a href="Javascript_Scripting" title="wikilink">JavaScript</a></p></td><td><p> {% include wikipedia title='JavaScript' text='JavaScript'%} is a popular choice among web developers.</p></td></tr><tr class="even"><td><p><a href="JRuby_Scripting" title="wikilink">Ruby (JRuby)</a></p></td><td><p> {% include wikipedia title='Ruby (programming language)' text='Ruby'%} is another popular choice among web developers.</p></td></tr><tr class="odd"><td><p><a href="Clojure_Scripting" title="wikilink">Lisp (Clojure)</a></p></td><td><p> {% include wikipedia title='Lisp (programming language)' text='Lisp'%} is a popular choice among computer scientists.</p></td></tr><tr class="even"><td><p><a href="Renjin_Scripting" title="wikilink">R (Renjin)</a></p></td><td><p> {% include wikipedia title='R (programming language)' text='R'%} is a popular choice among scientists and statisticians.</p></td></tr><tr class="odd"><td><p>Other options</p></td><td></td></tr><tr class="even"><td><p><a href="Java" title="wikilink">Java</a></p></td><td><p>You can code Java plugins in the Script Editor. This is the most difficult path, but also the most powerful.</p></td></tr><tr class="odd"><td><p><a href="MATLAB_Scripting" title="wikilink">MATLAB</a></p></td><td><p>ImageJ can interface bidirectionally with MATLAB. See the <a href="MATLAB_Scripting" title="wikilink">MATLAB Scripting</a> page for details.</p></td></tr><tr class="even"><td><p><a href="Beanshell_Scripting" title="wikilink">BeanShell</a></p></td><td><p> {% include wikipedia title='BeanShell' text='BeanShell'%} is an old script language, maintained mostly for backwards compatibility. It is nearly 100% compatible with Java syntax, but so is <a href="Groovy" title="wikilink">Groovy</a>.</p></td></tr><tr class="odd"><td><p><a href="Scala_Scripting" title="wikilink">Scala</a></p></td><td><p> {% include wikipedia title='Scala (programming language)' text='Scala'%} support is currently experimental, and has bugs.</p></td></tr></tbody></table>

Script parameters
=================

There is a universal `@parameter` notation available across all scripts for declaring inputs and outputs. This approach is preferred to using ImageJ 1.x `GenericDialog` because it is totally agnostic to the user interface, allowing such scripts to run in a variety of contexts.

See the [script parameters](Script_parameters) page for details.

Using an interpreter
====================

All scripting languages use the same basic interpreter, with the following common features.

General key bindings
--------------------

-   {% include key content='up' %}: bring the previously typed command.
-   {% include key content='down' %}: bring the next typed command.
-   {% include key content='enter' %} or {% include key content='return' %}: execute the contents of the prompt.

Multiline editing and keybindings
---------------------------------

You can enlarge the prompt by dragging the middle bar.

-   {% include key content='Shift\|\|Enter' %}: create a new line within the prompt.
-   {% include key content='Shift\|\|Up' %}: move to the line above within the prompt.
-   {% include key content='Shift\|Down' %}: move to the line below within the prompt.

Selecting and executing text from the screen
--------------------------------------------

On selecting text, a popup offers to:

-   copy
-   execute
-   save to a new file

Using the script editor
=======================

You can create, edit and run scripts using the built-in [Script Editor](Script_Editor). For details, please see [the Script Editor documentation](Using_the_Script_Editor).

Adding scripts to the Plugins menu
==================================

For the script to appear in the ImageJ menus, the following must apply:

{% include box text='".txt" is not a supported script extension' width='30%' float='right' %}

1.  The script file is saved in the `ImageJ.app/scripts` or the `ImageJ.app/plugins/Scripts` directory (or a subdirectory thereof).
2.  The script name ends in a supported script extension. For example
    -   ".groovy" for groovy,
    -   ".js" for javascript,
    -   ".py" for jython,
    -   ".rb" for jruby,
    -   ".clj" for clojure,
    -   ".bsh" for beanshell, and
    -   ".ijm" for ImageJ 1.x macros.
3.  The script name contains a '\_' (underscore) character, e.g. "MyScript\_.ijm".

{% include fiji content='Replace `ImageJ.app` with `Fiji.app`' %}

The extension will be stripped and any underscores will be turned into spaces before the script is added to the menus.

Scripts in the top-level `ImageJ.app/plugins` directory will appear at the bottom of the *Plugins* menu. Scripts can be placed in other menus by nesting subdirectories, for example placing a script in the `ImageJ.app/scripts/File` directory will add it to the *File* menu.

If you aren't able to find your script, you can always run the [Command Finder](Using_the_Command_Launcher) to verify its location (or absence).

Commands added to the menu in the described way can be called from other scripts. Use the [macro recorder](Macro_recorder) to get the required code for doing so.

Adding JAR-packaged scripts to the menu
---------------------------------------

Scripts can be packaged in a JAR file for easier distribution to your colleagues and via \[Update Sites\]. For this purpose, [example-script-collection](https://github.com/imagej/example-script-collection) can be used as the template Maven project.

Inside the example-script-collection jar, the scripts are in `./resources/scripts.` and therefore get added to the menu when the JAR is on the classpath (i.e. in `./plugins/` or `./jars/`).

ImageJ2 (and therefore Fiji) looks for scripts in subfolders of `./scripts/` as it is already described in the previous section, and for jars in `./jars/`. ImageJ1 recognizes plugins and scripts in `./plugins/`

Running scripts in headless mode
================================

See the [Scripting Headless](Scripting_Headless) page for instructions on executing scripts headlessly.


