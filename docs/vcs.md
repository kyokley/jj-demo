---
slides:
    title: JJ FTW
    separator_vertical: ^\s*-v-\s*$
plugins:
    - name: RevealMermaid
      extra_javascript:
          - https://cdn.jsdelivr.net/npm/reveal.js-mermaid-plugin/plugin/mermaid/mermaid.min.js
---

# Jujutsu
#### aka
# Fat (Commit) Stacks
#### YO <!-- .element: class="fragment" -->

---

## What
Jujutsu is a git-compatible VCS with advanced features

---

## :fearful:
<img src="./pics/code-review-diff-stats-534441-additions-spark-reviewer-concern.webp" class="r-stretch" />

---

## Enter stacked diffs
Stacked diffs (also known as stacked pull requests or stacked branches) are a Git workflow that breaks large features into a chain of small, dependent pull requests, where each PR targets the previous one rather than main

---

## Why
- Smaller PRs
- Merge Order
- Parallel Review

Notes:
- Smaller individual PRs
- Merge Order: Stacks must be merged bottom-up (base to top) to maintain valid dependency chains and avoid conflicts.
- Parallel Review: Reviewers can evaluate small, focused changes independently, while developers avoid idle time waiting for approvals.

---

## Example
- [Github](https://github.com/kyokley/jj-demo/pull/4)
- [SCM](https://devops.oci.oraclecorp.com/devops-coderepository/repositories/ocid1.devopsrepository.oc1.phx.amaaaaaacflwtoaaggqdoh5enrop5pmbdifsymreme27wxmsaxva2ruaip4a/pull-requests-tabs/ocid1.devopspullrequest.oc1.phx.amaaaaaacflwtoaalthapjbo3fe6guvqg2x6h4vkdwexjq2qdbevi47qqkxa/information)

---

## Some code
_awesome.py_
```python
def main():
    pass

def db():
    pass

def ui():
    pass
```

---

## Anatomy of a change
<img src="./pics/initial-code.png" class="r-stretch" />

Notes:
- Draw attention to Commit and Change IDs but greater detail later

-v-

## Anatomy of a change
<img src="./pics/initial-graph.png" class="r-stretch" />

---

## Doing the splits
<img src="./pics/split-main-cli.png" class="r-stretch" />

-v-

## Doing the splits
<img src="./pics/split-main-code.png" class="r-stretch" />

-v-

## Doing the splits
<img src="./pics/split-db-code.png" class="r-stretch" />

-v-

## Doing the splits
<img src="./pics/split-ui-code.png" class="r-stretch" />

-v-

## Doing the splits
<img src="./pics/split-main-graph.png" class="r-stretch" />

---

## Parallelizificator
<img src="./pics/parallelize-cli.png" class="r-stretch" />

-v-

## Parallelizificator
<img src="./pics/parallelize.png" class="r-stretch" />

Notes:
- Differences between change and commit IDs
- It's possible to do this with git but I promise it's not as slick
- JJ creates a git commit before and after all changes

---

## Just Kidding
<img src="./pics/undo-cli.png" class="r-stretch" />

---

## Branches? We don't need no stinking branches
<img src="./pics/bookmarks-cli.png" class="r-stretch" />

-v-

## Branches? We don't need no stinking branches
<img src="./pics/bookmarks.png" class="r-stretch" />

---

## Do a code review
DB looks wrong. Fix it!

---

## Refresher
<img src="./pics/bookmarks.png" class="r-stretch" />

---

## Apply fixes
<img src="./pics/post-bookmark-new-commit.png" class="r-stretch" />

-v-

## Apply fixes
<img src="./pics/code-review-change-graph.png" class="r-stretch" />

-v-

## Apply fixes
<img src="./pics/code-review-change-code.png" class="r-stretch" />

---

## Dude, Where's my rebase?
<img src="./pics/post-bookmark-new-commit2.png" class="r-stretch" />

---

## Is that it?

---

## Gotta keep them separated
<img src="./pics/pre-absorb-code.png" class="r-stretch" />

Notes:
This image got cut off

-v-

## Gotta keep them separated
<img src="./pics/pre-absorb-graph.png" class="r-stretch" />

-v-

## Gotta keep them separated
<img src="./pics/absorb-cli.png" class="r-stretch" />

-v-

## Gotta keep them separated
<img src="./pics/post-absorb-main-code.png" class="r-stretch" />

-v-

## Gotta keep them separated
<img src="./pics/post-absorb-db-code.png" class="r-stretch" />

-v-

## Gotta keep them separated
<img src="./pics/post-absorb-ui-code.png" class="r-stretch" />

-v-

## Gotta keep them separated
<img src="./pics/post-absorb-empty-graph.png" class="r-stretch" />

---

## Takeaways
- Jujutsu is pretty great
- But no pressure!
- Be kind to reviewers! Small targeted code reviews are best

Notes:

- But no pressure! Anything JJ can do, can be done with git

Some other highlights are:
- Change abstraction allows for powerful actions
- Revsets

-v-

## Other Takeaways
Unlike git, jujutsu has no
- branches
- index/staging area
- conflicts <!-- .element: class="fragment" -->
    - ...kinda <!-- .element: class="fragment" -->
- NO MERGE!?!? :exploding_head: <!-- .element: class="fragment" -->

-v-

## Other Takeaways
Other cool jujutsu stuff:
- parallelize
- absorb
- undo/redo
- duplicate
- split
- squash
