# Pull Requests Policy

## Goals
This policy is intended to make collaborative development for Tau Labs as efficient as possible, while maintaining safe code development as a priority. To achieve this, we try to keep the time from request to resolution as well as the number of open requests as small as possible. This benefits authors, reviewers and users as well. Authors will be encouraged to contribute more and will be able to scope their work easier, reviewers can more efficiently evaluate the relevant changes, and users get new features and bug fixes quicker.

## Philosophy
When you submit code by creating a pull request, it is your obligation to prove that your code is good to merge. **All** changes submitted for merging must be reviewed. It is your obligation as the author to find someone willing to invest time into reviewing your work and discussing and resolving all issues or concerns raised during the review. As author, you are expected to fix anything found during review; it is not the reviewer's responsibility to fix it for you. You should strive to make your code as easy as possible to review.

## Creation
* A pull request should be focused on one specific feature / bug fix / problem. The smaller the scope, the better. The less scope mixing, the better. Try to make commits as atomic as possible to ease merging as well as review. Consider splitting up big features into multiple requests.
* Keep in mind while writing and commenting your code that someone will have to review it. The better job you do at making clear what you are doing, the faster you will get through review.
* Never mix formatting fixes with semantic changes within a single commit.
* Write a proper summary and include potential pitfalls for the reviewer to ease his job.

#### Things we like to see as pull requests
* Bugfixes (one bug per request)
* New features (one feature per request)
* Request for comments (if explicitly stated)

#### Things we don't like to see as pull requests
* I don't like color xyz, so i changed it to abc
* I don't like name of variable abc so i changed it to def
* Changes without proper logical reason

## Review
After submitting a pull request, one or more reviewers will go through your code and write comments. For anything more than trivial changes, at least one reviewer **must** be a core developer. The quicker you respond to those comments by fixing mistakes or clarifying things, the sooner your code will be merged. You can always add commits to a running pull request. Just push them to the branch which is going to be merged.

## Merge or Close
When the review is done, the reviewer will write a summary of his findings and vote for merge or close, sometimes adding conditions (e.g. something has to be fixed before merge).
When there is consensus between author and reviewer that code will not be merged in the current state and has to be redone, the request will be closed. When a simple majority of core developer vote to merge or close, the request will be merged or closed accordingly.

If a pull request has been reviewed and is dormant because issues need to be addressed or the author is not resolving issues, the request will be closed. It can be reopened again later. This keeps the list of pending requests open to actionable items.

Authors will not merge their own pull requests.

## Appeals
Every effort should be made to resolve issues and concerns within the standard review process. If, however, after three months from the date of the pull request opening, an agreement cannot be reached to merge or close the pull request, an appeal to the project governing board can be made. Once an appeal is made, no changes will be allowed on the branch. Board members will be notified and shall have one months from the date of notification to vote merge or close, or explicitly abstain. The board will not discuss technical merit after an appeal is made, but shall only review comments made prior to the appeal. No board member will need to explain their rationale for voting. The majority vote for merge or close shall govern.

This process is intentionally lengthy and should only be a means of last resort.  Again, every effort should be made to resolve issues and concerns within the standard review process.
