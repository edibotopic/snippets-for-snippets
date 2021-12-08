# Snippets for Snippets

This is a plugin that provides helpful snippets for use when **editing snippet files** when creating snippet extensions for [Visual Studio Code](https://code.visualstudio.com/).

The snippets can be inserted while editing a JSON object in a `.json` file. For example, while typing "create snippet" in a valid JSON object (`{}`) pressing <kbd>enter</kbd> while `create snippet` is highlighted in the popup menu will generate:

```json

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

You can then press <kbd>tab</kbd> to navigate through the editable elements in sequence, which in this case would be the values for *prefix*, *body*, *description* and *scope*.

## Features

The plugin includes snippets for creating the following:

- Initialisation (`{ }`) of *JSON object* with cursor on new line
- Insertion of *boilerplate snippet* (example above)
- Insertion of *tabstops*, *placeholders*, *variables* and *choices*

The developer benefits from useful features like tabstops and variables while writing snippets for users that include the same useful features🤯.

Details on the use of these features when creating snippets can be found in [this official guide for user-defined snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets).

## Requirements

There are two potential use-cases for using snippets *while writing snippets*:

1. Snippet extension development
2. Local user snippet creation

This plugin is primarily intended to aid in the development of snippet extensions (case 1). In initial testing the plugin does not work for creating local snippets in `Preferences: Configure User Snippets`. VSCode has a built-in snippet called `empty snippet` that generates a boilerplate when editing local user snippets in this way; other than this example there seems to be limited snippets available for this purpose.

### Extension Development

You will need to have [NPM](https://nodejs.org/en/), [Yo Code](https://vscode-docs.readthedocs.io/en/stable/tools/yocode/) and [vsce](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#vsce) installed to develop extensions for VSCode.

Initialise a directory for your snippet extension using `yo code` in your terminal. Choose "New Code Snippets" when prompted and enter the relevant information for your plugin. Open the project in VSCode when asked if you want to do so.

This will generate a `snippets.code-snippets.json` in the `snippets` sub-directory. The [Snippets for Snippets](https://github.com/edibotopic/snippets-for-snippets) should work in this file. When you are happy with your extension you can publish it with `vsce`.

More detail on publishing extensions [can be found here](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).

<!-- ### Local Snippet Creation

To edit your local snippets press <kbd>cmd</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> to open the command pallette.

Navigate to `JSON` in the dropdown menu that appears. You can then use the snippets as described previously. -->

## Note: Snippets in Strings (" ")

By default, VSCode doesn't allow JSON snippets to be added within a string. When attempting to invoke a snippet within *here* `"body": ["<here>"]` it will not work unless there is a space inside each `"`. The boilerplate `create snippet` insertion contains such spaces in the `body` placeholder to facilitate the use of snippets; however, you need to delete the placeholder with <kbd>backspace</kbd> before this will work.

To see quick suggestions for strings the following will need to be added to your `settings.json`:

```json

    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": true
    }

```

If quick suggestions are not enabled for strings you can also press <kbd>cmd</kbd>+<kbd>enter</kbd> to trigger the popup menu, which might be preferable for some people.

## Release Notes

### 0.0.1

Initial release with all major snippets included.

## To-do

**Is this useful? Let me know!**
