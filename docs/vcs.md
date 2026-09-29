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

## WHY
Because git is stupid <!-- .element: class="fragment" -->

Notes:
why do we need a new VCS tool?

---

## Seriously stupid
<img src="./pics/stupid-git.png" class="r-stretch" />

Notes:
Taken directly from the man pages

Git was designed to be extended and built on. It tries to be unopinionated.

---

## :fearful:
<img src="./pics/code-review-diff-stats-534441-additions-spark-reviewer-concern.webp" class="r-stretch" />

Notes:
Did anyone else's chest just get tight suddenly?

---

## The good, the bad, and the ???

- :beaming_face_with_smiling_eyes: AI adoption completed 21% more tasks, merged 98% more pull requests <!-- .element: class="fragment" -->
- :loudly_crying_face: PR review time increased by 91%, average PR size grew by 154% <!-- .element: class="fragment" -->
- :face_with_symbols_on_mouth: Bug counts rose by 9% <!-- .element: class="fragment" -->

[Faros AI](https://www.faros.ai/) 2025 survey

Notes:
- Wikipedia notes optimal code review conditions should expect a couple hundred lines per hour
    - According to wikipedia effective code reviews break down any faster than a few hundred lines of code per hour of review
- 1k line code review should take 5 hours but probably longer
    - with SCM unable to track progress
    - reduced context from the original dev

The Productivity-Reliability Paradox:
Specification-Driven Governance for AI-Augmented
Software Development
by Sabry E. Farrag
School of Architecture, Computing and Engineering
University of East London, London, United Kingdom

quoting Faros AI 2025 survey


-v-

## The good, the bad, and the ???

> AI tools are currently optimizing the minority share of the pipeline while inadvertently increasing the burden on the majority share.

[The Productivity-Reliability Paradox](https://arxiv.org/pdf/2605.01160) - Sabry E. Farrag
University of East London, London, United Kingdom

Notes:

This pattern is consistent with Goldratt’s Theory of Constraints: optimizing a non-bottleneck step (code generation) does not improve system throughput when the bottleneck step (code review and human approval) remains unchanged. Writing and testing code accounts for roughly 25–35% of the total SDLC; the remainder is consumed by review, requirements understanding, debugging, meetings, and documentation. AI tools are currently optimizing the minority share of the pipeline while inadvertently increasing the burden on the majority share.

-v-

## The good, the bad, and the ???

> If your median PR is 50 lines long, you’re probably shipping 40% more total code than your teammate writing 200+ line PRs.

[The ideal PR is 50 lines long](https://graphite.com/blog/the-ideal-pr-is-50-lines-long) - Graphite Blog

Notes:

50-line code changes are reviewed and merged ~40% faster than 250-line changes. They’re 15% less likely to be reverted than 250-line changes and have 40% more review comments per line changed. If your median PR is 50 lines long, you’re probably shipping 40% more total code than your teammate writing 200+ line PRs.

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
- [SCM](https://devops.oci.oraclecorp.com/devops-coderepository/repositories/ocid1.devopsrepository.oc1.phx.amaaaaaacflwtoaaggqdoh5enrop5pmbdifsymreme27wxmsaxva2ruaip4a/pull-requests-tabs/ocid1.devopspullrequest.oc1.phx.amaaaaaacflwtoaalthapjbo3fe6guvqg2x6h4vkdwexjq2qdbevi47qqkxa/information) <!-- .element: class="fragment strike" -->

Notes:
Even SCM has support? Just kidding

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
- But no pressure
- Be kind to reviewers!

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

---
## Further Reading
[Awesome JJ](https://github.com/chawyehsu/awesome-jj)
- [Reviewing large changes with Jujutsu](https://ben.gesoff.uk/posts/reviewing-large-changes-with-jj/)
- [Jujutsu: Managing workspaces](https://pksunkara.com/tech-notes/jujutsu-managing-workspaces/)
- [Jujutsu For Busy Devs](https://maddie.wtf/posts/2025-07-21-jujutsu-for-busy-devs)

---
## References
- [The Productivity-Reliability Paradox: Specification-Driven Governance for AI-Augmented Software Development](https://arxiv.org/pdf/2605.01160)
- [Faros AI](https://www.faros.ai/)
- [Introducing Stacked PRs in Devin](https://devin.ai/blog/introducing-pr-stacks)
- [Code Review](https://en.wikipedia.org/wiki/Code_review)
- [The ideal PR is 50 lines long](https://graphite.com/blog/the-ideal-pr-is-50-lines-long)
