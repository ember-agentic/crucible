# Effective prompts and patterns.

How to get the most out of Crucible. Copy any prompt and use it directly.

## Starting a session

The first thing you say sets the tone. Start by getting the agent oriented with its tasks and the project context.

- `Review your Crucible tasks, load them to your todo, and work on them systematically.`
- `Check your task queue and start with the highest priority item.`
- `Search the knowledge base for context on this project, then check your open tasks.`

## Planning & requirements

Be specific about what you want built. Ask the agent to search existing docs before creating new ones.

- `I want to build [feature]. Create a requirements document with user stories and acceptance criteria. Search existing requirements first.`
- `Break down [goal] into user stories with clear acceptance criteria. Check what already exists before creating anything new.`
- `Audit the current requirements and identify any gaps or missing acceptance criteria.`
- `Review the requirements for [feature] and create design tasks for each user story.`

## Project health & assessment

Use these to get a big-picture view of where things stand.

- `Audit the documents, code, and open tasks and assess if this project is on track to achieve [goal].`
- `What's the current state of the project? Summarize open tasks, blockers, and recent completions.`
- `Review all open tasks and identify which ones are blocked. What needs to unblock them?`
- `Run a gap analysis -- compare the requirements against what's actually been implemented and tested.`

## Design & architecture

- `Review the requirements for [user story] and create a design spec. Search the architecture docs for relevant patterns.`
- `What are the architectural implications of [change]? Check existing ADRs and create a new one if needed.`
- `Review the design spec for [feature] and create implementation tasks with clear scope.`

## Implementation

Point agents at specific tasks and remind them to use the knowledge base.

- `Work on task [ID]. Read the related design spec and requirements before starting. Use the knowledge base.`
- `Implement [feature] following the design spec. Create tests as you go. Link all artifacts.`
- `Continue working on your current task. Check the acceptance criteria and make sure each one is met.`
- `I've made changes to [file]. Create a task to test these changes and hand off to testing.`

## Testing & quality

- `Review the implementation for [task]. Run the tests and validate against each acceptance criterion.`
- `Do a fresh-view gap analysis on [feature] -- don't assume the implementation is correct, verify independently.`
- `What's our test coverage for [feature]? Identify any untested acceptance criteria.`

## Knowledge & context

- `Search the knowledge base for everything related to [topic]. Summarize what you find.`
- `What decisions have been made about [topic]? Check the ADRs and design specs.`
- `Before starting on [task], search for any related existing work. Don't duplicate effort.`

## Handoff & coordination

- `You've completed your work on [task]. Create a handoff to [persona] with full context.`
- `Review the handoff from [persona]. Is the context complete enough to proceed?`
- `What tasks are waiting for handoff? Prioritize and process them.`

## Housekeeping

- `Update all your in-progress tasks with current status.`
- `Complete any tasks that are actually done but haven't been marked complete.`
- `Review your completed tasks from today and make sure all artifacts are linked and documented.`
- `Create a summary of what was accomplished this session.`

## Questioning & decision-making

Don't just accept what the agent produces. Ask questions. Challenge decisions. The best results come from dialogue, not one-shot prompts.

- `Why did you choose that approach? What alternatives did you consider?`
- `What are the tradeoffs of this design? What are we giving up?`
- `Present the options, pros and cons of each, and your recommendation -- summarized clearly.`
- `What could go wrong with this approach? What are the risks?`
- `How does this decision affect the rest of the system? What depends on it?`
- `I'm not convinced. Make the case for why this is better than [alternative].`
- `Walk me through your reasoning step by step.`
- `What assumptions are you making? Are any of them risky?`

> **When presented with a decision without enough context**, ask: "Give me the options, pros and cons of each, and your recommendation -- summarized clearly in a table." This forces the agent to structure its thinking and gives you what you need to decide.

## Steering & redirection

When the agent is going off track or not using the tools.

- `Stop. Before you do that, search the knowledge base for existing decisions about [topic].`
- `Use the Crucible MCP tools to create that task, don't just describe it.`
- `Remember to search before creating -- check if this already exists.`
- `Mark that task complete using the MCP tools and create a handoff to testing.`

## Common mistakes

**Being too vague.** "Build the feature" gives the agent nothing to work with. Instead: "Implement the API endpoints from DS-042 and write tests for each acceptance criterion."

**Not reminding agents to use MCP tools.** Agents sometimes try to do things manually instead of using Crucible's tools. Nudge them: "use the Crucible MCP tools to create that task."

**Skipping the knowledge base.** If the agent doesn't search first, it may duplicate existing work or contradict prior decisions. Always: "search the knowledge base before starting."

**Completing tasks without handoffs.** Work isn't done when code is written. Create handoffs with context so the next persona can pick up without guessing.

**Starting implementation without requirements or design.** The workflow exists for a reason. Requirements before design. Design before implementation. Skipping steps leads to rework.

## Tips

> **Treat each agent like a capable new team member.** They'll do good work, but they need direction. Ask questions. Give feedback. Push back on decisions you disagree with.

> **Start small.** Pick one feature or user story. Walk through the full workflow -- requirements, design, implementation, testing -- before scaling up.

> **The more you document, the smarter the system gets.** Every requirement, design decision, and test result feeds the knowledge graph. Don't skip the docs.

> **Be specific with task descriptions.** "Create an authentication module" is weak. "Implement OAuth2 login with Google and GitHub providers per DS-042, including token refresh and session management" gives the agent what it needs.
