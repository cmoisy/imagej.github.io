---
autogenerated: true
title: Script Editor Auto Import
layout: page
categories: Scripting
description: test description
---

{% include learn content='scripting' %}

Background
==========

The ImageJ script editor originally would automatically import many useful classes. This provided a clear benefit to writing scripts in ImageJ, as any plugins could be used without troubling the writer to know and enumerate the required classes.

However, there were drawbacks to this method as well. As the imports were not transparent, the user could not know what was actually being imported. During the development of Fiji, it was decided that the broad scope of the autoimport functionality was not robust enough, and could lead to clashes between libraries. Further, it could lead to scripts that are un-executable since dependencies may not be explicitly declared. As these could create situations unresolvable by the user, a dark period devoid of automatic imports began.

Today, ImageJ has a flexible and extensible automatic import mechanism: the [ScriptHeader](https://github.com/scijava/scijava-common/blob/181c016330be30861b573b70fb934f0b23c30447/src/main/java/org/scijava/script/ScriptHeader.java).

How ScriptHeaders works
=======================

ScriptHeaders are [SciJava](SciJava) plugins, so they can be distributed with any part of ImageJ or Fiji and will automatically be discovered.

When using the script editor to make a script for a particular language, all ScriptHeaders compatible with that language will add their contents to the beginning of the script.

Added lines may be language-specific imports, `@Parameter` script parameters, comments, or anything else that may be appropriate. For example, in the [JRuby ScriptHeader](https://github.com/scijava/scripting-jruby/blob/9f4b674ea945a0d4960152ec74e0f5de23754fd3/src/main/java/org/scijava/plugins/scripting/jruby/JRubyScriptHeader.java#L70-71) we import an external file. So automatic imports, extra function definitions, etc... are all handled in imagej.rb.

The result is that the script-writer sees exactly what is added. If they need to make changes of any type, they can do so easily within the editor. When a script is complete, it is then able to be run in any context and not just ImageJ where the auto-imports are present.

How to: Activate a Header
=========================

1.  Open the [Script Editor](Using_the_Script_Editor)
2.  Select a language from the Language Menu

That's it! If one or more ScriptHeader(s) exist for the selected language, they will be added automatically to the top of your script.

Limitations
-----------

By default, headers will only be added when switching away from `Language = None`. The ScriptHeader population logic itself can be overridden by providing a higher-priority [ScriptHeaderService](https://github.com/scijava/scijava-common/blob/181c016330be30861b573b70fb934f0b23c30447/src/main/java/org/scijava/script/ScriptService.java).

How to: Add a New Header
========================

A skeleton ScriptHeader is provided below. Simply resolve the marked TODOs and you can distribute your header as appropriate.

-   If you are writing a ScriptHeader general to the core scripting languages, it can be contributed to the [core scripting repositories](https://github.com/scijava?query=scripting).
-   If your ScriptHeader is specific to your project, it can be distributed as part of that project.

Prototype ScriptHeader
----------------------

    import org.scijava.plugin.Plugin;
    import org.scijava.script.AbstractScriptHeader;
    import org.scijava.script.ScriptHeader;
    import org.scijava.script.ScriptLanguage;

    //NB: The @Plugin annotation allows this ScriptHeader to be discovered
    //TODO give this header class an appropriate name

    @Plugin(type = ScriptHeader.class)
    public class MyScriptHeader extends AbstractScriptHeader {

    // -- ScriptHeader Methods --

      @Override
      public String getHeader() {
        // TODO Return the text you would like to enter at the top
        // of scripts of the target language.
        return null;
      }

      // NB: If AbstractScriptHeader is not extended you will not implement this section
      // but instead should override the public boolean supports(T) method.

      // -- AbstractScriptHeader methods --

      @Override
      protected Class<? extends ScriptLanguage> handledType() {
        // TODO return the ScriptLanguage class you would like to
        // receive this header string.
        return null;
      }
    }


