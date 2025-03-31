## NTY Cursor Rules Workflow & Directory Structure

This repository contains a designated folder structure and set of rules we use to make the Cursor IDE a viable pair programmer and improve the quality of our code assistant workflows.

The `.cursor/` folder structure contains:

```
├── knowledge/      # knowledge files generated from chat
├── output/         # output files generated from commands
├── rules/          # project-specific rules indexed and available to Cursor
│   ├── commands/   # agent-requested commands tied to specific inputs
│   ├── core/       # core rules for standards, workflows, etc
│   ├── tech/       # tech specific rules for frameworks, libraries, languages, etc
├── specs/          # specification files generated from chat
```

---

## .cursor/rules/commands

- [build-review.mdc](.cursor/rules/commands/build-review.mdc) - runs the npm build process, resolves any errors, and generates a report on build health
- [git-summarize.mdc](.cursor/rules/commands/git-summarize.mdc) - generates a summary of recent git activity (1 month) and respository health

## .cursor/rules/core

- [review-before-submission.mdc](.cursor/rules/core/review-before-submission.mdc) - pre-submission checklist for Cursor to step through when a solution has been generated
- [standards-min-viable-change.mdc](.cursor/rules/core/standards-min-viable-change.mdc) - process for implementing the smallest set of changes needed to solve a problem effectively
- [standards-naming.mdc](.cursor/rules/core/standards-naming.mdc) - naming conventions to use across the codebase when creating files, folders, functions, etc
- [workflow-knowledge.mdc](.cursor/rules/core/workflow-knowledge.mdc) - process for generating a new knowledge document
- [workflow-rule.mdc](.cursor/rules/core/workflow-rule.mdc) - process for generating a new Cursor rule
- [workflow-specification.mdc](.cursor/rules/core/workflow-specification.mdc) - process for generating a new specification document

## .cursor/rules/tech

- [standards-react-development.mdc](.cursor/rules/tech/standards-react-development.mdc) - development standards when working with react code

## Rule-driven Workflows

### **Creating a new knowledge snippet**
As we learn new concepts or solution alternatives to solving a problem, we often want to extract that knowledge for ourselves and to share with the rest of the team.

When this occurs, you can ask Cursor to `"create a knowledge snippet for {topic}"`. An input along these lines will register the `workflow-knowledge.mdc` rule and generate a new knowledge snippet, which will be added to the `.cursor/knowledge` directory.

-----

### **Generating a specification document for application logic**
Cursor has a tendency to modify code without the full context of the application logic, or fix code in one area which may break code in another. Having Cursor generate a specification doc for itself provides a safeguard against breaking changes being introduced without the full context of the application logic.

We have found it best to generate specification documents on a per-feature level, as opposed to having Cursor attempt to generate a specvification document for the entire application.

For example, we would generate specification docs like `user-onboarding-flow.md`, `profile-settings-flow.md`, `object-edit-flow.md`, `following-flow.md`. The narrower and more focused, the better.

You can ask Cursor to `"examine @file entry point for the {topic} flow, including its downstream files of {@additional_files_here}. generate a specification document describing the application logic for this flow."` An input along these lines will register the `workflow-specification.mdc` rule and generate a new specification document, which will be added to the `.cursor/specs` directory.

-----

### **Creating a new rule**
Using Cursor to extend Cursor is a great meta-level tactic to improve the pair programming experience. You should be doing this constantly to refine how Cursor approaches its programming and how it evaluates potential solutions.

When you run into a problem more than once, or finally solve an issue which took some time, or you found an edge case which was causing an error, these are great opportunities to have Cursor create a new rule for itself.

You can ask Cursor to `"create a rule for {topic}"`. An input along these lines will register the `workflow-rule.mdc` rule and generate a new rule, which will be added to the `.cursor/rules` directory. From there, you can move it to the most appropriate subdirectory if needed.