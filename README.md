# Snippets for Snippets

<!-- todo: record and add gifs then release -->
<!-- !: need to actually test if a snippet made by this method works, so need to create a .vsix first and check -->
<!-- ?: need to record gif of user snippets being created REQUIRES VSIX -->

This is a plugin that provides helpful snippets for use when **editing snippet files** in [Visual Studio Code](https://code.visualstudio.com/).

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

You can then press <kbd>tab</kbd> to navigate through the editable elements in sequence, in this case the values for *prefix*, *body*, *description* and *scope*.

## Features

The plugin includes snippets for creating the following:

- Initialisation (`{ }`) of *JSON object*
- Insertion of *boilerplate snippet* (example above)
- Insertion of *tabstops*, *placeholders*, *variables* and *choices*

The developer benefits from useful features like tabstops while writing snippets for users that include the same useful features (*you might have to think about that one*).

Details on the use of these features when creating snippets can be found in [this official guide for user-defined snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets).

## Requirements

There are two use-cases for this plugin:

1. Snippet extension development
2. Local snippet creation

### Extension Development

You will need to have [NPM](https://nodejs.org/en/), [Yo Code](https://vscode-docs.readthedocs.io/en/stable/tools/yocode/) and [vsce](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#vsce) installed to develop extensions for VSCode.

Initialise a directory for your snippet extension using `yo code` in your terminal. Choose "New Code Snippets" when prompted and enter the relevant information for your plugin. Open the project in VSCode when asked if you want to do so.

This will generate a `snippets.code-snippets.json` in the `snippets` sub-directory. The [Snippets for Snippets](https://github.com/edibotopic/snippets-for-snippets) should work in this file. When you are happy with your extension you can publish it with `vsce`.

More detail on publishing extensions [can be found here](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).

### Local Snippet Creation

To edit your local snippets press <kbd>cmd</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> to open the command pallette.

Navigate to `JSON` in the dropdown menu that appears. You can then use the snippets as described previously.

## Note: Snippets in Strings (" ")

By default, VSCode doesn't allow JSON snippets to be added within a string. If attempting to invoke a snippet within *here* `"body": ["<here>"]` it will not work unless there is a space inside each `"`. The boilerplate `create snippet` insertion contains such spaces in the `body` placeholder to allow the use of snippets; however, you need to delete the placeholder with <kbd>backspace</kbd> before this will work.

In addition, quick suggestions for strings will probably need to be added to your `settings.json`:

```json

    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": true
    }

```

If quick suggestions are not for strings you can also press <kbd>cmd</kbd>+<kbd>enter</kbd> to trigger the popup menu, which might be preferable for some people.

## Release Notes

### 0.0.1

Initial release with all major snippets included and doubt regarding whether this is a good idea intact.

## To-do

**Is this useful? Let me know!**
