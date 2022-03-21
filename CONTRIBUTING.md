# Contributing to NCC Knowledge Base

👍🎉 First off, thanks for taking the time to contribute! 🎉👍

The following is a set of guidelines for contributing to NCC knowledge base, website or any other repository by NCC, which are hosted in [NCC](https://github.com/NevadaCyberClub)'s GitHub. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document or any other in a pull request.


#### Table Of Contents
[Code of Conduct](#code-of-conduct)   
[Contributing Procedure](#contributing-procedure)   
   - [Communication](#communication)
   - [Help Maintain](#help-maintain)

## Code of Conduct

This project and everyone participating in it is governed by the [Nevada Cyber Club Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [nevadacyberclub@gmail.com](mailto:nevadacyberclub@gmail.com).


## Contributing Procedure

To contribute:
   1. Fork
   2. Edit
   3. Create Pull Request
   4. Wait for approval from a maintainer
      - Ping us over discord for a faster review process   

For a more detailed procedure on how to submit your edits, please review [Creating a pull request from a fork
](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork) document.

### Communication
Feel free to ping us over discord with any questions regarding contributing.  Asking for help is also encouraged. You can find the server link in the [NCC's website](https://www.nevadacyberclub.com/) at the bottom of the page.

### Help Maintain
If you desire to help maintain, please contact a club officer over discord. 


## Stuff 
NCC's repositories/files are made to be as cross-platform as possible, consistency makes it easier on everyone. 

### File Structure
Use best judgement

### Code
Avoid hacky/clever code that you will forget what it does in two weeks, i.e. document strange/non-trivial code. Explain if you can.

#### Line Endings
Uni-style line endings will be used. Every line should end in LF (aka `\n`, line feed), not CRLF (aka `\r\n`, carriage return line feed ). You can change your text editor to have this behabiour, consult with your editor's documention. You can also setup `git` to do it with `git config --global core.autocrlf input`.

#### File endings
Add a newline at end of file. If the file is of type `plaintext` (for example markdown, HTML, c++, etc..) then the last line should include a new line (LF/`\n`). 

Bad example:
```
# Bad example
No line feed here --->
```
Good example:
```
# Good example
Line feed here    --->LF

```
## How often should I commit?
"You shouldn't commit based on a time basis, but on a feature basis. Whenever you add a new feature that's worth committing, commit. You added a working method? Commit. You fixed a typo? Commit. You fixed a file's wrong indentation? Commit. There's nothing wrong committing small changes, as soon as the commit is relevant.

What is wrong is committing a huge number of changes, with no relations between each others. It makes it very hard to detect the commit source of a given regression.

Sometimes, I make twenty commits in an hour, and sometimes I commit once a day, depending of the amount of code that was modified.

Making small commits allows you to use very powerful tools like `git-bisect`.

Don't forget the rule n°1 of the committer: never break the trunk. If you need to make several commits that are likely to break the trunk, create a branch instead." - from [here](https://softwareengineering.stackexchange.com/a/74893)

As for not breaking the repos/branches, you can always test locally. Don't be afraid to ask for help. 

