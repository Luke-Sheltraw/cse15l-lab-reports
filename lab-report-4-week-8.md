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
**Description**: VSCode's Previews ``[`google.com]``.

*Tests in `MarkdownParseTest.java`*:
![JUnit tests]()

*Tests on my implementation*:
![Test output on my implementation]()
**Description**: 

*Tests on reviewed implementation*:
![Test output on reviewed implementation]()
**Description**: 

***

### **Snippet 2**

*Expected output*:
![Expected output of snippet](images/snippet2expectedoutput.png)
**Description**: CommonMark shows that the expected output contains three links, which should be the list ``[a.com, a.com(()), example.com]``.

*Tests in `MarkdownParseTest.java`*:
![JUnit tests]()

*Tests on my implementation*:
![Test output on my implementation]()
**Description**: 

*Tests on reviewed implementation*:
![Test output on reviewed implementation]()
**Description**: 

***

### **Snippet 3**

*Expected output*:
![Expected output of snippet](images/snippet3expectedoutput.png)
**Description**: CommonMark shows that the expected output is a single link, which should be the list ``[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]``.

*Tests in `MarkdownParseTest.java`*:
![JUnit tests]()

*Tests on my implementation*:
![Test output on my implementation]()
**Description**: 

*Tests on reviewed implementation*:
![Test output on reviewed implementation]()
**Description**: 

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

***

**Explanation of passed tests**: