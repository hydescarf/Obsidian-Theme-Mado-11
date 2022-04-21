# Obsidian Theme - Mado 11
 
![](cover.png)
![](cover2.png)

Mado 11 is an Obsidian theme, inspired by Windows 11 UI styling.

This theme aims for a simplified app feel, with bigger buttons to click on the sidebar. Works well for people that prefer easy workflow rather than using everything Obsidian provided.

That being said, feel free to dock anything wherever you want.

## Installation

- Download the file "obsidian.css" and place it inside your Obsidian Snippet Folder. (You may rename the file to your liking)
- Enable it through Settings → Appearance → CSS Snippets.

## Guideline

#### Top Menu

- Back & Forward buttons - hidden, hover to show. Position is at the top-left corner.
- Min/Max/Close buttons - hidden, hover to show. Position is at the top-right corner.
- App Title and Vault Title - hidden.

#### Left Sidebar

- New Note/New Folder/Rearrange buttons - hidden. Recommend to make the buttons first before installing.
- Ribbon-Dock buttons (Settings, Change Vault, etc.) - hidden. Same solution as above.
- Style is set to be buttons-only. Icons are made possible with [Icon Folder Plugin](https://github.com/FlorianWoelki/obsidian-icon-folder)
- To achieve the bottom-left buttons (Settings, etc.), [Buttons Plugin](https://github.com/shabegom/buttons) is required. [See instructions below](#sidebar-buttons).

#### Sidebar

- Dock-Collapse buttons - hidden, hover to show. Position is around the top-left/right corner.
- Tab Menu on the dock - hidden, hover to show. Position is around the top-edge of the dock inner border.

#### Other

- Recommended Font: Segoe UI, Noto Sans JP
- Main Pane has animation activated at each update/enter. Search for "slide-up" in the CSS file if you want to disable it.
- Resize Handle - hidden, hover to show.
- Status Bar - hidden.

## Special class: mado-header
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
   

## Sidebar Buttons 

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
1. Drag the note onto the bottom part of the sidebar.



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


## Update  

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