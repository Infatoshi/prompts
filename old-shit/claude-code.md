---
title: how i bring the best out of claude code - part 1
date: 2025-06-15
excerpt: a comprehensive guide to effective claude code usage, context management, and building local multi-agent systems
---

## 1. setup requirements

you need a set of requirements, preferably issues in a repo. take the requirement url and download and save it into an `issues/` folder or have github integration with claude code. then create a file like `<issue_no>.md` or whatever you prefer.

> **note:** your requirements list is very crucial, and you should treat it like a wish list for work to be done.

the more vague you are in describing what you want, the higher the chance you won't get what you wanted. ideally, your instructions should be as unambiguous as a program.

you also want to be aware of what is already known by the model.

## 2. most important thing: context management

a common pattern:
```
[claude code] --> [todo list]
               (fresh context)
```

better approach:
```
well-formalized --> issues/<issue_no>.md (plan)
                --> docs/plan_<issue_no>.md (issue requirement)
```

this `plan_<issue_no>.md` serves as claude's context. the `todo.md` is essentially exactly the same as your to-do list.

> the todo list is nice, but as you consume things in longer context in claude code, it becomes hard to keep up. so we store it inside the `todo.md`.

## 3. parallel claude code usage

if you're using multiple claude code windows in parallel, assign each one an issue and its corresponding docs, todos, and requirements. this way, everything is tracked automatically.

currently, i don't use claude code in parallel much because it tends to create new files for everything, prompt to edit existing files directly, and update code based on outdated or flawed understanding.

that's why i often ask it to detail its plan so i can do smell checks and question intentions like *"oh, you were aiming to do xyz. then why modify abc?"*

additionally, claude might start running commands unknowingly and fill context with needless output tokens.

> i avoid this by running it manually myself, providing a snippet of the error so it can best debug it.

## 4. execution strategy

once you're going through each item, do it step by step while enforcing quality standards. you decide how frequently to execute and ensure there are no blindspots.

> personally, i avoid diving into thousands of loc i haven't written or understood.

## 5. iteration and updating context

as i implement and ensure smooth execution, i iterate with errors and debug, then go back and update crucial observations in the planning docs.

> this allows the model to build better understanding of the issue and what is already known.

## 6. working compactly

in an ideal world, you work on one issue end-to-end in one session.

but usually, context fills out faster and faster. you'll find yourself using "compact" more often.

if you ever run out of context during execution, claude auto-compacts or asks you to go back to a previous node.

> this is useful when i see a model ignoring feedback and going in loops. in such cases, i jump to a clean node where i was satisfied, compact, generate a summary, and start fresh.

## 7. integrating claude code into tooling

now that claude code sdk exists, you can add it to your tools.

i've been using it in shell scripts and proto files. my protocols reflect opinionated views of deep research methodologies and how i debug or visit the ecosystem.

for instance, my ecosystem has `issues/` and `todo.md` folders. i use a shell script to invoke tasks in specific ways and let claude interact with other claude instances.

> essentially, i'm building a local multi-agent system of my own.

## 8. final thoughts

what are these systems? what protocols are being enforced? how is multi-agent design different? what gives it an edge over standard usage?

these are things i'd like to cover in part 2.

---

until then, be well everyone!
