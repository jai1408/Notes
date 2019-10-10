# Markdown Notes
  *  https://github.com
  *  https://facebook.com
  *  You can even [link to Google!](http://google.com "google home page")

*** 
[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../master/Notes1.md)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links. 
http://www.example.com or <http://www.example.com> and sometimes 
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

*** 
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

Here's our logo (hover to see the title text):

Inline-style: 
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style: 
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

- Dashes work just as well
- And if you have sub points, put two spaces before the dash or star:
  - Like this
  - And this
  
  
> Coffee. The finest organic suspension ever devised... I beat the Borg with it.
> - Captain Janeway

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.


There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks: `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return true
    }

GitHub also supports something called code fencing, which allows for multiple lines without indentation:

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language:

```javascript
if (isAwesome){
  return true
}
```

Hey @ jai1408 — love your coding!

But I have to admit, tasks lists are my favorite:

- [x] This is a complete item
- [ ] This is an incomplete item

***

Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the 
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

Id | Name | Age
--- | --- | ---
1 | Jai | 26
2 | John | 43
3 | Kevin | 67
4 | Bob | 23
5 | Jason | 29

___
* **interface Alpha** default implementation of reset().
* **interface Beta** default implementation of reset().
* **class MyClass** implements Alpha   
> Beta Is the version by Alpha or the version by Beta used by MyClass? **Error will occur**
> Consider interface Beta extends Alpha. 
> Which version of the default method is used? **Beta’s version of reset( ) will be used**
> what if MyClass provides its own implementation of the method? **MyClass version is used. Both default methods are overridden by class           > implementation of method**

___
<a href="http://www.youtube.com/watch?feature=player_embedded&v=3TOnJI1BqzU
" target="_blank"><img src="http://img.youtube.com/vi/3TOnJI1BqzU/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>
