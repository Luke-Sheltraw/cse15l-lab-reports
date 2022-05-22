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
**Description**: The test failed. 

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
**Description**: The test failed.

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
**Description**: The test failed.

***

### **Questions**

**Question 1**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**:

***

**Question 2**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**:

***

**Question 3**: Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

**Answer**: