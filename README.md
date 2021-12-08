# Snippets for Snippets

This is a plugin that provides helpful *snippets* for use when **creating local user snippets** or **developing snippet extensions** for [Visual Studio Code](https://code.visualstudio.com/).

The snippets can be inserted while editing a `.jsonc` file (superset of JSON *with comments*). For example, while typing "create snippet" in a valid JSON object (`{<within these curly braces>}`) pressing <kbd>enter</kbd> while `create snippet` is highlighted in the *quick suggestion* menu will generate:

```jsonc

{
    "name of snippet":{
    "prefix": ["prefix for snippet"],
    "body": [
        " body of snippet "
    ],
    "description": "description of snippet",
    "scope": "language(s) of snippet"
   }
}


```

You can then press <kbd>tab</kbd> to traverse through the editable elements in sequence, which in this case would be the values for *prefix*, *body*, *description* and *scope*.

![Demonstration of basic functionality](images/demo1.gif)

## Features

The plugin includes snippets for creating the following:

- Initialisation (`{ }`) of *JSON object* with cursor on new line
- Insertion of *boilerplate snippet* (example above)
- Insertion of *tabstops*, *placeholders*, *variables* and *choices*

Snippet writing requires a specific syntax that can be difficult to recall if you are not writing them frequently (*maybe it's just me*). For example, to create a placeholder with three internal choices the following has to be written:

```jsonc

${1:number}|${2:choice1},${3:choice2},${4:choice3}|}

```

The `choice` snippet will generate the above line and allow you to define the traversal number and choices for the snippet you are writing as you <kbd>tab</kbd> through them.

Details on the use of these different built-in features for creating snippets in VSCode can be found in [this official guide for user-defined snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets).

## Requirements

There are two potential use-cases for using snippets *while writing snippets*:

1. Snippet extension development
2. Local user snippet creation

### Extension Development

You will need to have [NPM](https://nodejs.org/en/), [Yo Code](https://vscode-docs.readthedocs.io/en/stable/tools/yocode/) and [vsce](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#vsce) installed to develop extensions for VSCode.

Initialise a directory for your snippet extension using `yo code` in your terminal. Choose "New Code Snippets" when prompted and enter the relevant information for your plugin. Open the project in VSCode when asked if you want to do so.

This will generate a `snippets.code-snippets.jsonc` in the `snippets` sub-directory. [Snippets for Snippets](https://github.com/edibotopic/snippets-for-snippets) should work in this file. When you are happy with your extension you can package and publish it with `vsce`.

More detail on publishing extensions [can be found here](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).

### Local Snippet Creation

To edit your local snippets type <kbd>cmd</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> to open the command pallette.

Navigate to the relevant language in the dropdown menu that appears. You can then use the snippets as described previously.

## Note: Snippets in Strings (" ")

By default, VSCode doesn't allow snippets to be triggered *from within a string* but there are some simple workarounds and settings that need to consider:

1. Check *spacing* within strings: When attempting to trigger a snippet within *here* `"body": ["<here>"]` it will not work unless there is a space inside each `"` like this: `"body": [" <here> "]`. The boilerplate `create snippet` insertion contains such spaces in the `body` placeholder to facilitate the use of snippets by default.
&nbsp;

2. Ensure you aren't triggering *mid-traversal*: If you <kbd>tab</kbd> to a default placeholder value it will not be possible to trigger snippets while the value is highlighted. You need to first delete the default value with <kbd>backspace</kbd> before you can trigger snippets automatically or manually.
&nbsp;

3. Trigger *automatically*: Enable *quick suggestions* for strings: to achieve this the following will need to be added to your `settings.json` in VSCode:

```json

    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": true //<<<---|this is the important one|
    }

```

4. Trigger *manually*: You can also type <kbd>cmd</kbd>+<kbd>enter</kbd> to trigger the snippet menu, which might be preferable for some people.

## List of Snippets

- initialise a snippet file
- create a snippet
- placeholder
- tabstop
- choice
- variable default
- builtin variables for text and files
- builtin variables for time and date
- builtin variables for randomisation

## Release Notes

### 0.0.1

Initial release with all major snippets included.

## To-do

- [ ] Consider key-binding(s)
- [ ] Consider VSCode commands for Mac

*Snippets for snippets' sake . . .*
