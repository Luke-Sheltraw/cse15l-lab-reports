# Lab Report 4 - _Week 8_
## Markdown Parser Test Snippets

***

**`markdown-parse` repository links**:

*My repository*: [https://github.com/Luke-Sheltraw/markdown-parser](https://github.com/Luke-Sheltraw/markdown-parser)

*Reviewed repository*: [https://github.com/mrreganwang/markdown-parser](https://github.com/mrreganwang/markdown-parser)

***

### **Snippet 1**

*Expected output*:
![Expected output of snippet](images/snippet1expectedoutput.png)
**Description**: VSCode's Preview shows that there are three links, which would form the list ``[`google.com, google.com, ucsd.edu]``.

*Test in `MarkdownParseTest.java`*:
![JUnit test](images/snippet1test.png)
*(Using a helper method I wrote previously)*

*Tests on my implementation*:
![Test output on my implementation](images/snippet1mytest.png)
**Description**: The test failed. As illustrated in the screenshot, my implementation of markdown-parser included `url.com` in the list, when it should not have. 

*Tests on reviewed implementation*:
![Test output on reviewed implementation](images/snippet1theirtest.png)
**Description**: The test failed. Similar to my implementation, it included the `url.com` url, when it should not have. 

***

### **Snippet 2**

*Expected output*:
![Expected output of snippet](images/snippet2expectedoutput.png)
**Description**: VSCode's Preview shows that there are three links, which would form the list ``[a.com, a.com(()), example.com]``.

*Test in `MarkdownParseTest.java`*:
![JUnit tests](images/snippet2test.png)
*(Using a helper method I wrote previously)*

*Tests on my implementation*:
![Test output on my implementation](images/snippet2mytest.png)
**Description**: The test failed. As illustrated in the screenshot, my implementation of markdown-parser included `b.com` in place of `a.com` for the first link.

*Tests on reviewed implementation*:
![Test output on reviewed implementation](images/snippet2theirtest.png)
**Description**: The test failed. As illustrated in the screenshot, their implementation of markdown-parser dropped the final two closing parentheses from the second link, meaning it returned `a.com((` instead of `a.com(())`.

***

### **Snippet 3**

*Expected output*:
![Expected output of snippet](images/snippet3expectedoutput.png)
**Description**: VSCode's Preview shows that there is one link, which would form the list ``[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]``. There are two other "links," however that is because VSCode automatically interprets anything of the form https://... as a link (as illustrated by them having no title). In the scope of this project, then, we would not consider those two to be expected output. 

*Test in `MarkdownParseTest.java`*:
![JUnit tests](images/snippet3test.png)
*(Using a helper method I wrote previously)*

*Tests on my implementation*:
![Test output on my implementation](images/snippet3mytest.png)
**Description**: The test failed. As illustrated in the screenshot, my implementation of markdown-parser included `https://www.twitter.com` (surrounded by white space) when it should not have.

*Tests on reviewed implementation*:
![Test output on reviewed implementation](images/snippet3theirtest.png)
**Description**: The test failed. Similar to my implementation, it included the `https://www.twitter.com` (surrounded by white space) link when it should not have. 

***

### **Questions**

**Question 1**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**: Yes; the correct behavior is to ignore anything within a pair of backticks, but any starting backtick within parentheses should not be counted. Therefore, I could add an if-statement at the start of the while-loop that checks if the next backtick is before the next opening parenthesis, and if it is then remove all the contents of markdown between that and the next backtick. One issue this could have would be that it would remove content between backticks spread over multiple lines (which shouldn't happen, as inline code must be inline). However, this would be accounted for if the change in Question 3 was implemented as well.

*** 

**Question 2**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**: Yes; to account for nested brackets, I could add to the if-statement within the while loop I have to check for layered brackets: if the character after a closed bracket is an opening parenthesis, that should replace the current closed bracket and break. This would find the "first" closed bracket, and thus the inner-most one. To account for escaped brackets, all it would take is an extra conditional in any if statement that checks for brackets (ensuring that the previous character is not a backslash). Finally, to account for nested parentheses, I could implement a while-loop similar to what I had before for nested brackets—counting each opening and closing bracket and only setting the closing parenthesis to be the final one which terminates the nesting (e.g. the balance hits 0). This would probably be a total of about 10 lines.

***

**Question 3**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**: Yes; the proper behavior of the program should be to not accept any link that is broken over multiple lines IF there is a blank line. That is, if two lines are "touching," they are considered one. At the beginning of the program, I could split the markdown into an array of entries using two back-to-back newlines as the separator. I could then loop through and process each array item as if it was its own file. This would ensure that each "section" of text separated by a blank line is treated as its own entity.