jQuery Tokeninput: A Tokenizing Autocomplete Text Entry
=======================================================

Overview
--------
Tokeninput is a jQuery plugin which allows your users to select multiple items from a predefined list, using autocompletion as they type to find each item. You may have seen a similar type of text entry when filling in the recipients field sending messages on facebook.

Changes from original jquery-tokeninput
---------------------------------------

This is a forked version of jquery-tokeninput blending vdepizzol's and loopj's versions, plus updating the search-by-function behavior to actually work and to be similar to JQuery UI Autocomplete's behavior.

In this version, in addition to merging loopj's 1.5 version with vdepizzol's improvements, the main change is that in addition to providing a URL or inline data for the first parameter, you can provide a search function to handle the lookups for you.  This function can construct whatever type of request you like, such as:

<pre><code>
  $("#element").tokenInput(
    function(query, response) {
      $.ajax({ url: "your url here",
               data: { q: query, extra: "stuff" },
               dataType: "json",
               success: function(data) { response(data) }
             });
    },
    {
      preventDuplicates: true,
      onAdd: function(list,item) { alert("You added " + item.name) }
    });
</code></pre>

These changes are somewhat incompatible with the latest merges to the head of loopj's tree where a patch was accepted to have just a simple URL formatter function (instead of the "perform the search for you" function that I wrote a la JQuery UI Autocomplete).

