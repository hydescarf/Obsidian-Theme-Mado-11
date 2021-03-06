# Obsidian Theme - Mado 11
 
Mado 11 is an Obsidian theme, inspired by Windows 11 UI styling.

This theme aims for a simplified app feel, with bigger buttons to click on the sidebar. Works well for people that prefer easy workflow rather than using everything Obsidian provided.

That being said, feel free to dock anything wherever you want.

(Psst, looking for more minimal theme? Check out [Mado Miniflow](https://github.com/hydescarf/Obsidian-Theme-Mado-Miniflow)!)

![](cover.png)
![](cover2.png)

## Index

- [Installation](#installation)
- [Guideline](#guideline)
- [Special CSS Class: mado-header](#special-css-class-mado-header)
- [Sidebar Buttons Installation](#sidebar-buttons-installation)
- [Changelog](#changelog)

---

## Installation

- Download the file "obsidian.css" and place it inside your Obsidian Snippet Folder. (You may rename the file to your liking)
- Enable it through Settings → Appearance → CSS Snippets.

Or

- Download the theme through Obsidian's theme store!

## Guideline

#### Top Menu

- Back & Forward buttons - hidden, hover to show. Position is at the top-left corner.
- Min/Max/Close buttons - hidden, hover to show. Position is at the top-right corner.
- App Title and Vault Title - hidden.

#### Left Sidebar

- New Note/New Folder/Rearrange buttons - hidden, hover to show. Position is at the top-right corner of the left-sidebar.
- Ribbon buttons (Settings, Change Vault, etc.) - hidden, hover to show. Position is at the bottom-left corner.
- Style is set to be buttons-only. Icons are made possible with [Icon Folder Plugin](https://github.com/FlorianWoelki/obsidian-icon-folder)
- To achieve the bottom-left buttons (Settings, etc.), [Buttons Plugin](https://github.com/shabegom/buttons) is required. [See instructions below](#sidebar-buttons-installation).

#### Sidebar

- Dock-Collapse buttons - hidden, hover to show. Position is around the top-left/right corner.
- Tab Menu on the dock - hidden, hover to show. Position is around the top-edge of the dock inner border.

#### Other

- Recommended Font: Segoe UI, Noto Sans JP
- Main Pane has animation activated at each update/enter. Search for "slide-up" in the CSS file if you want to disable it.
- Resize Handle - hidden, hover to show.
- Status Bar - hidden.

---

## Special CSS Class: mado-header
Turn your headers into buttons, and align all contents to their width and style!
![](header-sample-light.png)
![](header-sample-dark.png)

#### Usage
Just add "mado-header" to the cssclass in the frontmatter of that note and you're done.

Make sure you have the option "Fold Header" enabled in your Settings→Editor section.
~~~
---
cssclass: mado-header
---
~~~

Header H1 will serve as the main button, and the rest will be kept inside of that button.

Copy the following and test it out!
~~~
# Header H1 Title
Contents can be anything.

> Be it Quote

```
Or Code
```

- Or List

---

- [ ] Or Checkbox (with a hidden separator `---` above to separate checkbox from list)
~~~

---


## Sidebar Buttons Installation

1. Install [Buttons Plugin](https://github.com/shabegom/buttons).
1. Create a note and insert a "button" (Ctrl+P, search for "Buttons: Button Maker") that should look like below. You may use an SVG link as Icon in the "name" section
   ~~~
   ```button
   name <svg/> **Insert an SVG link here** </svg> New Note
   type command
   action Create a New Note 
   ```
   ~~~
1. Create another note, and insert an "inline-button" (Ctrl+P, search for "Buttons: Insert Inline Button").
1. Select the button you need to be placed on the sidebar. It should come out something like "\`button-aafl`".
1. Insert a frontmatter cssclass of `mado-side-button` on top of the note. (v0.2.5+)
   ~~~
   ---
   cssclass: mado-side-button
   ---
   ~~~
1. Drag the note onto the bottom part of the sidebar.
1. As of App v0.15.6 update, it is recommended to "pin" the above pane so that during new note creations from it, it will create a new note onto the main pane instead of onto the sidebar.



#### Adjustment for Buttons Plugin
An adjustment to the Buttons Plugin `main.js` file is required as of April 2022, to make the buttons work in the sidebar. See https://github.com/shabegom/buttons/pull/105 for more information.
1. Go to your plugin folders
2. Look for Buttons Folder, and open the file "main.js" inside it 
3. Search for `const clickHandler = async (app, args, inline, id) => {` (around line 1553)  
4. Look for these right below and cut them
   ```js
   if (args.type === "command") {  
   	command(app, args);  
   }  
   // handle link buttons  
   if (args.type === "link") {  
   	link(args);  
   }
   ```
5. Paste them below `const activeView = app.workspace.getActiveViewOfType(obsidian.MarkdownView);` which is just a few lines above them (or one line below the initial search)  

---

## Changelog  

v0.3.2
- Readjusted `titlebar` height style as previous version has disabled the dragging feature.

v0.3.1
- Additional "style-reverting", remove styles on button when it is on focus

v0.3.0
- "Revert" styles that are affected from the App update of v0.15.6.

v0.2.7
- Fixed close/min/max buttons being unclickable during "Translucent Window" mode.
- Adjusted the weird opacity design during "Translucent Window" mode.

v0.2.6
- Fixed close/min/max buttons position for MacOS.

v0.2.5
- Fixed left-sidebar for not properly showing the other plugins' pane.
- Left-sidebar bottom buttons now requires a frontmatter cssclass of `mado-side-button` to allow other custom notes to function.
- Fixed spacing issue for "Banner Plugin".
- Re-remove the background fading gradient on the title block as it blocks the editing path.
- Adjusted style for blockquote.
- Table is reverted to non-full width (only expands based on its content length).
- Table in `mado-header` however has a new styling.

v0.2.4
- Removed and readjusted most of the `!important` in the code to allow custom CSS Snippets to work easily. Some, however, are remained untouched so as to override inline CSS style.
- Various minor style changes

v0.2.3
- Applied hover-to-show for hidden ribbon docks (settings, change vault, etc.) and explorer buttons (new file, reorder, etc.)

v0.2.2
- Applied minor styling to Callout feature

v0.2.1
- Quick Fixes for background colours for codeblock and scrollbar

v0.2.0
- Adjusted various styling, especially for those in dark mode
  - ==Highlight== is now underlined in dark mode
  - **Bold** text is now coloured
  - `Code Colour` is now more readable with a brighter red version
  - Other small changes
- Implemented special CSS class ["mado-header"](#Special-class-mado-header)

v0.1.0
- Release!