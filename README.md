<h1>Creating the Page Template</h1>

In index.html, we include the css, jquery script and js script after the title tag; in the body we have 3 div containers for popup div event.

    div container for loading
    div container for popup background,
    and div container for popup

<h1>The stylesheet</h1>


In the css, if you want scrollbar in the popup just remove comment in line 74.
<h1>The jQuery script</h1>


In the click event we triggered the loading() function and delay 0.5 second and triggered the loadPopup() function and the pop up displays. We add little more for closing the popup, if hover the ‘Close’ the tool tip message will appeared and keyboard event for close.
4. Done

We’re done, we learn one of jquery example on creating our own popup div using jQuery, and you can edit the content of the popup like adding more text, registration form and image. Let’s have a look at what we’ve achieved:

    We create popup div without third party plugin
    Works in old IE browser, IE 7,8
    We add little feature, hover tool tip and keyboard event

If you enjoyed this article, please consider sharing it!
- See more at: http://istockphp.com/jquery/creating-popup-div-with-jquery/#sthash.YFgFleao.dpuf
