# darkMode
Dark Mode for GoogleSheets
How to Create Dark Mode in Apps Script
We’ll create four functions, one for each style mode. Each of our functions will do the following:

Set background color
Set font color
Set font family
Set border color and style
Let’s walk through how to create a darkMode function in Apps Script. We'll define each function with the function keyword, followed by whatever we’ll name it.

Because the functions take no arguments (they just run without needing more info from us). That is, we have open and closed parentheses with nothing inside them followed by an open curly brace.

All of our code for the function goes between the darkMode function's curly braces:

function darkMode() {
  SpreadsheetApp.getActive().getRange('A1:Z')
    .setBackground("#333333")
    .setFontColor("white")
    .setFontFamily("Google Sans")
    .setBorder(false,false,false,false,true,
     true,"#444444",SpreadsheetApp.BorderStyle.SOLID)
}
To select all the cells, we used the built-in methods from the SpreadsheetApp class: getActive() and getRange(). These select the active sheet as well as a given range.

In our case, we’ll plug in A1:Z as the range, but you can extend this further if you’d like. For instance,  A1:AZ, would add columns AA:AZ and then apply our styling to them.

The four lines that follow are simply dot notation extensions telling what styles to apply. You can write this on one line if you’d like, but it’s good practice to have line breaks to make the code easy to read.

How to Set Colors and Fonts
You'd notice that we used both setBackground(#333333) and setFontColor("white") in the code. This is because we can use CSS notation colors in either hex format or by using the color’s name.

Using setFontFamily("Google Sans"), we gave it the font family name within quotations. Being a Google product, you can use any of the Google Fonts as well as Google’s own Google Sans font as I found out making this project.

How to set the Border
The setBorder(false,false,false,false,true, true,"#444444",SpreadsheetApp.BorderStyle.SOLID) function let’s you enter true or false values for the top, left, bottom, right, vertical, or horizontal borders, in that order, followed by the color and style.

To set the style, we had to invoke a built in Enum Attribute — BorderStyle — to change the style of the border.

How to Create the Style Menu
To be able to select any of the styles we’re making from the actual spreadsheet, we need a menu.

To add the menu, we'll create a new function called  onOpen() that runs as soon as the spreadsheet opens and then the built-in methods from the getUi() to build our custom menu.

We can create the menu with .createMenu() and then add each of our functions to the menu with the addItem() function.

Here's the code:

function onOpen(){
  SpreadsheetApp.getUi()
    .createMenu('Style')
    .addItem("Dark","darkMode")
    .addItem("Papyrus","papyrusMode")
    .addItem("Light","lightMode")
    .addItem("Synth","synthMode")
    .addToUi();
}
Google Apps Script automatically integrates with Google Workspace apps (like Google Sheets) so the functions we've added in the code will make the functionalities accessible in your Google Sheets.
