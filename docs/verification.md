URL of the channel:
https://www.twitch.tv/danielduel

URL of repository:
https://github.com/Duelsik/beatsaber-request-ui

Table of contents:
* 0 - Changelog
* 1 - Motivation
* 2 - Main functions
  * 2a - Expand/Unexpand
  * 2b - Searching
* 3 - Code verification tips

0. Changelog

18 March 2021 (latest) - Add expand/unexpand and searching functionality

1. Motivation

I've created this piece of software to make it easier to search for beatsaber maps
without opening another browser tabs or tutorials on how and where to get key for
map request.

So in short - it should make user life easier and serve as an easy-to-use tool.

2. Main functions

2a. Expand/Unexpand

Users can hide and show the extension panel.

Hiding:
Click the cross icon in the top right segment of the extension.
The extension pane should hide.

Showing:
Hover over the very left part of the extension container.
Chevron should appear, click it.
The extension pane should appear.
(this also is resetting the state of deeper elements like Search state)

2b. Searching

Search is using https://beatsaver.com/ as a dataset and backend.

Users can search for maps using input and the "Search" button.
The extension is showing the result of the search as a list with different data fields.
Fields such as key and "!bsr {key}" are magnified when hovering over them to make
copy-pasting easier.
While searching - the extension should communicate that to the user.
In case of no results - the extension should communicate that to the user.

3. Code verification tips

Hi another developer.

Generally, this is an ejected react app.
I've ejected that because I had to inject twitch scripts and do changes to allow
testing it locally (and I think there were more problems, but I don't remember).

I think you should start by a quick look in `/public/index.html` and see that twitch
script is interpreted before everything else.

And then...

See `/src` folder:
`/src/App` is where things basically start.
`/src/common/LayoutRow` is a common component for rendering rows.
`/src/Header/Header` is header rendered at the top of the app.
`/src/SearchPage/SearchPage` is searching "view".

Note:
I use `/src/SearchPage/mock` while developing to not hit API rate limits during
HMD reloads and this is not a part of the final build.

Also:
I am looking into styled-components and using typescript in the future, just wanted to make a quick start.