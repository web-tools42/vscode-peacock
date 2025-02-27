---
title: Changelog
# We can even add meta tags to the page! This sets the keywords meta tag.
# <meta name="keywords" content="my SEO keywords"/>
description: Changelog for the Visual Studio Code Peacock extension
meta:
  - name: keywords
  - content: vscode "visual studio code" peacock theme extension changelog
---

# Change Log

All notable changes to the code will be documented in this file.

## 4.0.1

- Badges udpates to use <https://shields.io/> in readme and docs

## 4.0.0

- Deprecated - minimal risk
  - Migration To Version < 4.0.0
    - Version 3+ of Peacock stores the color in the settings `peacock.color`. When migrating from version 2.5, the peacock color was in a memento. When migrating from version < 2.5, the color was not stored, but can often be derived through a calculation by grabbing the color from one of the `workbench.colorCustomizations` that Peacock uses. Once the color is determined, peacock removes the memento, and writes the color to the settings `peacock.color`. Fixes [#230](https://github.com/johnpapa/vscode-peacock/issues/230) and addresses [#258](https://github.com/johnpapa/vscode-peacock/issues/258). This is an aggressive approach, as it is possible to have a color customization that peacock uses, and if it sees this, it will set Peacock up to use it. This logic is marked as deprecated but will not be removed until version 4.0 is released and enough time has passed reasonably for people to migrate. That time is now.
  - If anyone has not yet migrated in the 2 years the migration existed, then Peacock will not set a color. This is easily fixed by the user using a Peacock command to set the color.

## 3.11.0

- [Granular control over accent borders](https://github.com/johnpapa/vscode-peacock/issues/472#issuecomment-945950855)
  - Thanks to [@superole](https://github.com/superole) for the issue
  - Removed the `affectAccentBorders` setting and replaced it with 4 settings:
    - `affectEditorGroupBorder` - Specifies whether Peacock should affect the editorGroup border - default to false
    - `affectPanelBorder` - Specifies whether Peacock should affect the panel border - default to false
    - `affectSideBarBorder` - Specifies whether Peacock should affect the sideBar border - default to false
    - `affectSashHover` - Specifies whether Peacock should affect the sash border - default to true
  - Added tests for the 4 new settings
  - Adjusted test for old setting

## 3.10.1

- Updated to VuePress v2 (beta), changing for dark and light themes, fixing links

## 3.10.0

- Added `sash.hoverBorder` to the Accent Borders

  - Changed default value for setting `affectAccentBorders` to true. Accent borders in vs code were clashing contrasts, since the introduction of [sash.hoverBorder](https://code.visualstudio.com/updates/v1_52#_sash-hover-border-color).

- Added support for Peacock as a VS Code web extension [PR 461](https://github.com/johnpapa/vscode-peacock/pull/461)

  - The VS Code team recently launched VS Code for the web with [github.dev](https://docs.github.com/en/codespaces/developing-in-codespaces/web-based-editor)! You can read the full guide for extension authors creating and migrating extensions here: [Web Extensions
    ](https://code.visualstudio.com/api/extension-guides/web-extensions). Changes were made to make Peacock work on the web and these include: - Modify webpack bundling to create web and desktop friendly versions of your extension - Add the necessary dependencies for web bundling - Add the `browser` entry point to your `package.json` to link to the web-friendly compiled extension - Add some folders/files to ignore in your `.gitignore` and `.vscodeignore` - Add launch configuration for launching your extension in a web extension host
    - Tested with a launch configuration or `vscode-test-web`. [Learn more on the docs.](https://code.visualstudio.com/api/extension-guides/web-extensions#test-your-web-extension)
    - Added `npm run open-in-browser` for testing
    - Thanks to [@tanhakabir](https://github.com/tanhakabir) for the core contribution!

- Set border of remote status bar [PR 451](https://github.com/johnpapa/vscode-peacock/pull/451)
  - Thanks to [@ndrake](https://github.com/ndrake) for the core contribution!

## 3.9.1

- Updated links to resources

## 3.9.0

- Added support for coloring the status bar while debugging based on the peacock color. [#271](https://github.com/johnpapa/vscode-peacock/issues/271)
- Added new setting **Affect Debugging Status Bar**, which defaults to **false**. [#271](https://github.com/johnpapa/vscode-peacock/issues/271)
- Updated vscode engine to 1.49.0

## 3.8.0

- Added new property **Affect Status and Title Borders**, which defaults to **false**. [#397](https://github.com/johnpapa/vscode-peacock/pull/397)
- merged npm audit fixes for packages

## 3.7.2

- Removed keyboard shortcut for **Surprise Me with a Random Color** command. Was using wrong key combo!

## 3.7.1

- Updated docs site to <https://www.peacockcode.dev>
- Added keyboard shortcuts to the docs

## 3.7.0

- Added statusBar.border to be colored the same as statusBar.background [#381](https://github.com/johnpapa/vscode-peacock/pull/381)
- Added titleBar.border to be colored the same as titleBar.activeBackground [#381](https://github.com/johnpapa/vscode-peacock/pull/381)
- [Updated sinon](https://github.com/johnpapa/vscode-peacock/issues/356)
- [Updated mocha types](https://github.com/johnpapa/vscode-peacock/issues/344)
- removing remnants of tslint, since peacock moved to eslint months ago
- added husky and pretty-quick for running prettier pre-commit [#366](https://github.com/johnpapa/vscode-peacock/pull/366)
- Refactored how settings are written to workspace. Peacock tries to preserve the sequence in which the settings are written. However, VS Code seems to cache these values so some of this is out of Peacock's control.

## 3.6.0

- [`activitybar.activeBackground` is now set the same as the activity bar's background](https://github.com/johnpapa/vscode-peacock/issues/345)
- Fixed [broken links in changelog](https://github.com/johnpapa/vscode-peacock/issues/362)
- Fixed typos in [functions and comments](https://github.com/johnpapa/vscode-peacock/pull/361)

## 3.5.0

- [Reduced favorites](https://github.com/johnpapa/vscode-peacock/issues/358)
- [default faves won't appear in user settings.json until they are modified](https://github.com/johnpapa/vscode-peacock/issues/354)

## 3.4.0

Color Adjustments

- Added Svelte color to built-in favorites
- Adjusted React and Angular colors based on their official logos

## 3.3.1

Fixes

- doc links to contributions, code of conduct, and changelog from the guide are now fixed
- removed notification when writing the favorites list to the settings.json file. it was confusing to see this when first installing peacock, as there is nothing for the user to do.

- Adopt the new 'extensionKind' format. As per [Erich Gamma](https://github.com/egamma) from [PR #314 and Issue #313](https://github.com/johnpapa/vscode-peacock/pull/314)

> As of VS Code 1.40 the `extensionKind` attribute in the `package.json` of the extension can be an array, pls see the documentation. We will be deprecating the string type for `extensionKind` property in favour of string array type. The `extensionKind` attribute should be set to `["ui", "workspace"]`. Indicating that the extension can run both as a UI extension and as a workspace extension (e.g. in the browser).

Maintenance

- merged npm audit fixes for packages
- updated several packages as devDependencies to keep up with security updates

## 3.2.0

Features

- October 2019 release of VS Code added `activityBar.activeBorder` color. It was using a color that often clashed, so it now uses the accent color from the badge color. this color setting is available in October 2019 release of vs code as shown here. https://code.visualstudio.com/updates/v1_40

## 3.1.6

Fixes

- npm audit fix

Minor Changes

- Node version compat updates
- Added badges to the docs
- Added version to home page of docs

## 3.1.5

Fixes

- npm audit fix
- pointer to the changelog in the docs
- fixed broken doc link

## 3.1.4

Fixes

- Migration occurs when colors are in user settings but not in workspace.
  - Fixes [263](https://github.com/johnpapa/vscode-peacock/issues/263)
  - During migration, Peacock is checking if the current workspace has a color set in the old style. This could be a `activityBar.background`, `titleBar.background`, or `statusBar.background`. VS Code's API merges default settings, users settings and workspace settings. Therefore, this migration logic was sometimes getting migrated, and it should not. Peacock should only migrate to the new `peacock.color settings (which makes it much easier to determine what the color is definitively) if there is a color in the workspace settings. The fix for this was to write logic that gets the workspace colors only. This is done in a new function named`getWorkspaceColorIfExists`.

Changes

- Writing less but clearer messages to the output channel for Peacock
- Added more migration and FAQ to the guide/docs
- Refactored migration logic to a single file.
- Function refactorings
  - `getWorkspaceColorIfExists` --> get (and calculate for adjustments) a single color from the workspace settings if one exists. Ideal for migration when peacock.color did not exist in < v3.
  - `getOriginalColor` --> if a non color is passed in, then pass the same thing back out. This protects against having a undefined or empty string passed in and #000 being passed out.
  - `getElementColors` --> allows both `vscode.workspaceConfiguration` type AND `ISettingsIndexer`, since sometimes we have one or the other

## 3.1.1

Migration

- Version 3+ of Peacock stores the color in the settings `peacock.color`. When migrating from version 2.5, the peacock color was in a memento. When migrating from version < 2.5, the color was not stored, but can often be derived through a calculation by grabbing the color from one of the `workbench.colorCustomizations` that Peacock uses.
  - Once the color is determined, peacock removes the memento, and writes the color to the settings `peacock.color`. Fixes [#230](https://github.com/johnpapa/vscode-peacock/issues/230) and addresses [#258](https://github.com/johnpapa/vscode-peacock/issues/258)
  - This is an aggressive approach, as it is possible to have a color customization that peacock uses, and if it sees this, it will set Peacock up to use it.
  - See more details in the readme/guide

Fixes

- Upgraded to typescript-eslint 2 plugin and parser. This caused some rules to kick in from recommended list that were not previously firing. Fixed all linting issues related to this.

  ```json
  "@typescript-eslint/eslint-plugin": "^2.0.0",
  "@typescript-eslint/parser": "^2.0.0",
  ```

## 3.1.0

Fixes

- Added a command to show the Peacock documentation web site <https://www.peacockcode.dev>
- Writing Favorites - For now we'll just add the starter set of favorites one time. If there are favorites, do not write new ones. We'll revisit this later so we do not overwrite favorites.

## 3.0.1

Fixes

- When settings.json doesn't exist, and surprise me on startup is true, Peacock was writing an empty file for settings.json. It shouldn't. So it now checks if it is trying to write an empty object AND there is no workbench.colorCustomizations section already, it won't write.

## 3.0.0

Migration

- Version 2 of Peacock stored the peacock color in a memento. Version 3 of Peacock stores the color in the settings. If the v2 memento exists, Peacock gets the color, removes the memento, and writes the color to the settings. Fixes [#230](https://github.com/johnpapa/vscode-peacock/issues/230)

Features

- Commands
  - `Copy the Current Color to the Clipboard` - Shows the current color and copies it to the clipboard
    - This command can be executed from the command palette or by clicking the statusBar item for peacock's color
  - `Peacock: Reset Workspace Colors` - Removes any of the color settings from the `.vscode/settings.json` file. If colors exist in the user settings, they may be applied
    - This used be named `Peacock: Reset Colors` and was renamed for clarity
  - `Peacock: Remove All Global and Workspace Colors` - Removes all of the color settings from both the Workspace `.vscode/settings.json` file and the Global user `settings.json` file.

New Settings

- Removed remote colors and live share colors from mementos and instead created user settings for these. Mementos are best for values the user cant see, while settings make it easier for the user to see them and modify them directly. This feels right for these colors.

- Peacock now separates when colors will be applied (workspace color customizations) from when the `peacock.color` is saved. When a user applies Peacock colors, applyColor is called and we also update `peacock.color`. When the color just needs to be applied, but not written, we just called applyColor.

* New settings are as follows:

  - `peacock.color` - The Peacock color that will be applied to workspaces

    - currently selected local color. this replaced the workspace memento for the current/recent color, which may solve reported problems with mysterious colors changing (because workspace settings are visible, get removed by peacock commands, and users can manually edit them).

  - `peacock.remoteColor` - The Peacock color that will be applied to remote workspaces

    - currently selected remote color. color for all types of remote environments (ssh, wsl, containers). this consolidates the 3 into 1.

  - `peacock.vslsShareColor` - Peacock color for Live Share Hosting
  - `peacock.vslsJoinColor` - Peacock color for Live Share Joining

Breaking Changes

- Remove commands for remotes as we now just use the other commands to change the color while you are in a remote.
  - `Change Remote Color (SSH)` - prompts user to select a color for the SSH remote context from the Favorites
  - `Change Remote Color (Containers)` - prompts user to select a color for the Containers remote context from the Favorites
  - `Change Remote Color (WSL)` - prompts user to select a color for the WSL remote context from the Favorites
- Remove the existing current color memento (replace with peacock.color)
- Remove the existing remote color settings/mementos (replace with peacock.remoteColor)

DevOps

- [Adding code coverage and test reporting to Azure Pipelines](https://github.com/johnpapa/vscode-peacock/pull/219)
- Added several new tests for testing the `peacock.color` and `peacock.remoteColor`

Bug Fixes

- When trying the favorites out in the quick pick list, continually selecting a new one, but not selecting one, Peacock would start looping thru colors in a rapid fashion and never stop. This has been corrected.
- Peacock used to copy any extra workbench.colorCustomizations in the global user settings.json to the workspace, because the get configuration API in vs code get a merged set of settings. This has been refactored to only get the colors that are in the workspace and the Peacock uses. This now uses `read-configuration.ts`'s `getColorCustomizationConfigFromWorkspace` function

## 2.5.2

Bug Fixes

- Reverting 2.5.0. This feature seems to have adverse effects as per user reporting. It was applying Peacock on projects that didn't have Peacock colors yet, as per feedback in issues.
  - The intended code should have only applied Peacock if there were already colors in the workspace settings.json file. Further testing will be done before putting this back.

## 2.5.1

Bug Fixes

- We now apply peacock colors on startup, in case user level settings change outside the scope of this workspace. example: accent is enabled, but this project you are opening doesn't have colors for it yet. peacock should add them on startup. example: you turned off titlebar, then open a project. peacock should remove titlebar colors.

## 2.5.0

Features

- VS Code Remote
  - Peacock now detects when the [VS Code Remote](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extension is installed and adds commands that allow the user to change color depending on the remote context (container, ssh, wsl). Credit to [Erich Gamma for this PR](https://github.com/johnpapa/vscode-peacock/pull/187_)
  - New Commands
    - `Change Remote Color (SSH)` - prompts user to select a color for the SSH remote context from the Favorites
    - `Change Remote Color (Containers)` - prompts user to select a color for the Containers remote context from the Favorites
    - `Change Remote Color (WSL)` - prompts user to select a color for the WSL remote context from the Favorites
- Surprise Me
  - Created a new setting for `surpriseMeFromFavoritesOnly`. Defaults to false for backwards compatibility.
  - When false, a color is chosen purely randomly.
  - When true, a favorite color is selected randomly
- Status Bar
  - Added setting for `showColorInStatusBar` setting (defaults to true).
- New elements can be colored
  - Added new elements that can be affected by Peacock's coloring. Each is colored with the same lighten/darken adjustments as activityBar
  - `peacock.affectAccentBorders` Specifies whether Peacock should affect the accent borders (panel, sideBar, editorGroup) Defaults to false.
  - `peacock.affectTabActiveBorder` Specifies whether Peacock should affect the active tab's border. Defaults to false.

Security

- [Bumped lodash version](https://github.com/johnpapa/vscode-peacock/pull/195)

Logging

- Added more logging to the output of mementos and favorites
- Added logging on startup if "surprise me on startup" is set. One if the color is changed. A different message if the color was not changed because one already existed.

Refactoring

- Created a `mementos.ts` file with mento functions for getting and saving mementos. This consolidates some of the code Peacock has for mementos
- Created constants for the peacock core mementos, the vsls mementos, and the remote mementos. Each are in their respective folders and modules
- Recent Color State vs Peacock Color Memento
  - Recent Color is the most recently used color.
  - If you want the original Peacock color, then use getPeacockColorMemento() in mementos.ts
  - Example:
    - Peacock may be using #fff and Peacock Remote is using #000.
    - When using remote, recent color may represent
    - the remote color #000 while the memento will always be the original #fff
- Split the setup and teardown calls out to make them easier to read.
- Fix places where async/await calls were being used incorrectly
- Created a timeout function constant for use in tests
- Moved the extension context state to the State static class
- All commands now return extension context for use in tests
- Made getRandomFavoriteColor not return same color as the current color

Linting and Formatting

- Added prettier
- Added eslint and removed tslint (using eslint for ts)

DevOps

- Refactored tests after the new yo code generated test model.
- Added code coverage
- Refactored how Azure DevOps runs the pipelines
- Added tests for remote features
- Created a npm script for `test-all` which compiles and tests the 2 test groups. Note that that CI only runs the npm script for `test` which covers the core tests only due to vsls not working under test in CI currently
  - core peacock & remote tests
  - peacock vsls tests

## 2.4.0

Features

- added `Peacock: Darken` to the commands. Currently darkens the current color by the `darkenLightenPercentage` setting
- added `Peacock: Lighten` to the commands. Currently lightens the current color by the `darkenLightenPercentage` setting
- added `peacock.darkenLightenPercentage` to settings. Indicates the percentage to darken or lighten the color (defaults to 10%)
- added key bindings for lighten `alt+cmd+=` and for darken `alt+cmd+-`

Breaking Changes

- default values for new installations are to colorize all three affected areas: titleBar, activityBar, and statusBar. new users were sometimes confused why Peacock was only coloring the titlebar. While the settings are explained in the README, this should help people see the possibilities better.

Bug Fixes

- fixed broken test that added and removed an extra setting

## 2.3.0

Features

- Added _Go Cyan_ `#5dc9e2` to favorites for Go
- Changed to v 2.3.0 as a minor or major will add new favorites

Bug fixes

- fixes the issue when after canceling the ">Peacock: Change to a Favorite Color" command, the color of the workspace is set to black and adds the appropriate test.

## 2.2.2

Features

- Added [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) integration.
- Updated README for Live Share and Remote Development integrations
- added `Peacock: Change Live Share Color (Host)` to the commands
- added `Peacock: Change Live Share Color (Guest)` to the commands

## 2.1.2

Features

- Added _Java Blue-Gray_ `#557c9b` to favorites for Java
- Added "extensionKind": "ui"` to support remote development features in VS Code (see [#141](https://github.com/johnpapa/vscode-peacock/pull/142/))

## 2.1.1

Features

- Added _C# Purple_ `#68217A` to favorites for .NET Core

## 2.1.0

Enhancements

- Extension as API: Added color parameter to enterColor handler which allow the developer to call the extension programmatically without prompting user input

## 2.0.1

Maintenance

- Refactored to remove a dependency on a testing file
- Removed `helpers` file, since I don't feel that was descriptive or helpful (pun intended)
  - Moved functions in that file to better existing modules

## 2.0.0

Features and Breaking Changes

- Added settings which allow the user to override the dark and light foreground colors
  - _darkForegroundColor_ setting (defaults to `15202b`) which can override the dark foreground on what is calculated as a light background
  - _lightForegroundColor_ setting (defaults to `e7e7e7`) which can override the light foreground on what is calculated as a dark background
- `Add recommended favorites` is now a command
- Recommended favorites are now being saved when a new version is installed. Avoid using the same names.
  - Recommended favorites are a list of constants found in `favorites.ts`. These are alphabetized.
  - Recommended favorites are a starting point for favorites. They will be installed whenever a new version is installed. They will extend your existing favorites, so feel free to continue to add to your local favorites! However be careful not to change the color of the recommended favorites as they will be overridden when a new version is installed.
  - This list may change from version to version depending on the Peacock authoring team.
- Built-in colors for Angular, React and Vue have been removed in favor of "favorites"
- One Built-in color exists: Peacock Green. This gives a user an easy color choice :)

## 1.3.1

Bug fixes

- fix issue where surprise me message shows up anytime a surprise me command is run.

## 1.3.0

Features

- _Surprise Me On Startup_: When enabled, Peacock will automatically apply a random color on startup when opening any workspace that does not already have color customizations defined. It will also show an information dialog in case the user forgot this setting is enabled.

Other Changes

- Added logging to an output channel for diagnostics
- Refactored internal state to be a static class, to make it easy to log when state changes
- Added [webpack bundling](https://code.visualstudio.com/api/working-with-extensions/bundling-extension)
- Fixed tests to wipe out the extra setting that was added during one test

## 1.2.1

Bug Fixes

- Resolved error for "command peacock.\* not found". Was due to a missing file and function for `isObjectEmpty`. The code was in the test folder and thus worked locally, in debug mode, and in CI for testing (which is why CI was green). This is now resolved bu moving the file and function to the `src` folder.

## 1.2.0

Features

- _Preview Your Favorite_: When opening the Favorites command in the command palette, Peacock now previews (applies) the color as you cycle through them. If you cancel (press ESC), your colors revert to what you had prior to trying the Favorites command

Bug Fixes

- When entering a color and canceling, or when entering an empty string, an error is no longer thrown

Other Changes

- When resetting colors, Peacock wasn't removing the old `workbench.colorCustomizations` if it was empty. It now does

## 1.1.0

Features

- Added Save current color as a favorite color
- When a setting is changed, Peacock should update the colors appropriately based on the most recently used color during the active VS Code instance's session

Breaking Changes

- Renamed commands and settings from 'preferred' to 'favorite'

## 1.0.0

Other Changes

- Added colorization of items in the status bar on hover to better fit with the color that Peacock applies.
- Added colorization of the Activity Bar badge based on the background color applied by Peacock to improve readability
- Refactored inactive element coloring to better match default behavior of VS Code and most themes.
- Added azure devops CI process to test on macos, linux and windows with Node 8 and 10

## 0.7.0

Features

- Added `peacock.keepForegroundColor` setting, which specifies whether Peacock should change affect colors (see [Keep Foreground Color](./README.md#keep-foreground-color))

Other Changes

- Added and updated all tests to respect the `keepForegroundColor` setting
- Refactored some functions to remove redundant code
- Added more setup and teardown code to the test suites
- Refactored tests to use arrow functions
- Refactored prepareColors function to collect the element settings using sub-functions for readability
- Created ISettingsIndexer to help indexing settings properties using enums

## 0.6.0

Features

- New setting for `peacock.elementAdjustments` that allows for slight value adjustments of affected elements to visually distinguish them from one another.
- Activity Bar icons now reflect current active state with the current activity in the foreground color and inactive activities indicated.
- Color entry now supports a larger variety of formats with more flexible entry restrictions (see [input formats](./README.md#input-formats) in [README](./README.md) for more information)

Other Changes

- Removed settings for dark and light foregrounds. Now defaults to DarkForeground = '15202b' and LightForeground = 'e7e7e7'. The value of these felt low vs the overhead of yet another setting
- Introduced the [tinycolor](https://www.npmjs.com/package/tinycolor2) library to handle color input validation, color conversion, and color manipulation
- Refactored much of the internal color library
- Added several unit tests for color input entry, affected elements, and element adjustments
- Updated README

## 0.5.0

Breaking Changes

Instead of an array, there are three separate configuration properties for the affected element settings:

```json
    "configuration": {
      "properties": {
        "peacock.affectTitleBar": {
          "type": "boolean",
          "default": true,
          "description": "Specifies whether Peacock should affect the title bar."
        },
        "peacock.affectActivityBar": {
          "type": "boolean",
          "default": false,
          "description": "Specifies whether Peacock should affect the activity bar."
        },
        "peacock.affectStatusBar": {
          "type": "boolean",
          "default": false,
          "description": "Specifies whether Peacock should affect the status bar."
        }
      }
    }
```

Other changes

- Refactored the constants, enums, and interfaces into a `models` folder in the code with a barrel for access

## 0.4.0

Features

- Refactored Preferred Colors to display the user-defined name of a color and the color value in a quick pick list.

The preferred colors require a custom name (`name`) and a value ( `value` ), as shown in the example below. See the README.md for details.

```javascript
  "peacock.preferredColors": [
    { "name": "Gatsby Purple", "value": "#639" },
    { "name": "Auth0 Orange", "value": "#eb5424" },
    { "name": "Azure Blue", "value": "#007fff" }
  ]
```

Bug Fix

- fixed bug where 3 character hex values were not working

## [0.3.0]

Features

- New setting for `peacock.preferredColors` that stores an array of strings for color names and hex values
- User can select `Peacock: Change to a Preferred Color` which prompts with the list from `peacock.preferredColors` from user settings

Other Changes

- Refactor modules to be clearer
- Refactor changeColor to enterColor for internal names of the command

## [0.2.1]

Features

- Updated Peacock logo
- Added support for [HTML color names](https://www.w3schools.com/colors/colors_names.asp).

Other Changes

- Implemented reset for each settings that isn't selected
- Added unit tests
- Updated README

## [0.1.1]

Features

- Added properties in settings for `peacock.lightForeground` and `peacock.darkForeground`
- Added defaults for light foreground `#e7e7e7` and dark foreground `#15202b`

Breaking Changes

- Renamed the property in settings from `peacock.affectedSettings` to `peacock.affectedElements`
- When there are no settings for `peacock.affectedElements`, the default is `titleBar`

Other Changes

- Refactored code in different modules
- Updated README

## [0.0.7]

Features

- Added ability to color the activityBar, statusBar, and titleBar
- Added the property `peacock.affectedElements` to allow affecting one or more of the following:
  - activityBar
  - statusBar
  - titleBar

Refactor

- Refactored all utility functions to `utils.ts`

## [0.0.5]

Features

- Added menu command to reset all colors (clears the workspace settings for the affected colors)
- Revised the prompt to guide on RGB format for hex values

Bug fixes

- Prompt for color now works when a file is not open.

## [0.0.4]

- Named **peacock**
- Allow changing to user defined color
- Allow changing to random color
- Allow changing color to angular, vue, or react primary colors
- Saves colors to your workspace
- Sets the foreground to white or black based on the contrast for the background color
- Add peacock icon
- Added README.md
- Made commands use `peacock:` prefix
