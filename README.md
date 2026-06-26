# Senter — Multi-Agent Fleet Orchestrator

![Senter](https://raw.githubusercontent.com/SouthpawIN/senter/main/logo.png)

The brain of your agent fleet. Senter receives all incoming requests—user messages, Discord commands, scheduled tasks—and intelligently routes each to the right specialist agent based on task complexity and type.

## Installation

```bash
hermes profile install senter
```

That's it. One command installs Senter with all dependencies, configuration, and skills.

## Update

```bash
hermes profile update senter
```

Keeps Senter and all bundled skills up to date.

## What Does Senter Do?

**Intelligent task routing and coordination**

Senter is your fleet's dispatcher. When a message arrives—whether from Discord, Slack, or direct message flow—Senter analyzes it and delegates it to the right agent:

- **Trivial request** → Answer directly (greeting, quick question, simple lookup)
- **Implementation task** → Route to Chizul (the builder)
- **Documentation need** → Route to Kashi (the writer)
- **Quality review** → Route to Klerik (the auditor)
- **Community support** → Route to Hermes Support (the helper)
- **Multi-agent project** → Coordinate between multiple agents

Senter uses pattern matching, semantic analysis, and context awareness to make routing decisions in milliseconds.

## Example Prompts

**Simple routing:**
```
User: "Can you write a poem about sunsets?"
Senter analyzes: "write a poem" → creative, complex
Routes: → Nous-Girl (creative specialist)
```

**Implementation request:**
```
User: "I need a REST API for user management"
Senter analyzes: "REST API" → technical implementation
Routes: → Chizul with task description
```

**Documentation request:**
```
User: "Create a README for my project"
Senter analyzes: "Create a README" → documentation
Routes: → Kashi with context
```

**Multi-agent coordination:**
```
User: "Build a feature, write tests, and update docs"
Senter analyzes: three distinct task types
Routes: → Chizul (build) → Chizul (tests) → Kashi (docs)
```

**Quick question:**
```
User: "What's 2+2?"
Senter analyzes: simple factual question
Handles: Answers directly: "4"
```

## How It Works

Senter uses a three-step analysis:

1. **Pattern matching**: Looks for keywords (poem, build, write, review, help)
2. **Semantic analysis**: Understands intent and complexity
3. **Context awareness**: Considers conversation history and user preferences

Routing priority:
1. Trivial requests (greetings, simple questions) → Answer directly
2. Single-agent tasks → Route to specialist
3. Multi-agent tasks → Coordinate sequence
4. Complex research → Route to Nous-Girl

## Fleet Coordination

When multiple agents need to work together, Senter:
- Breaks down the request into sequential tasks
- Routes each task to the appropriate agent
- Maintains conversation context across the workflow
- Reports progress back to the user

Example workflow:
```
User: "Add user authentication to my app"

Senter coordinates:
1. → Chizul: Implement authentication system
2. → Chizul: Add tests for authentication
3. → Klerik: Review the authentication code
4. → Kashi: Update documentation with auth endpoint
5. → Senter: Report completion to user
```

## Message Sources

Senter accepts tasks from:
- **Discord**: Bot messages, slash commands, mentions
- **Slack**: Bot messages, app mentions
- **Direct API**: HTTP POST to `/route`
- **CLI Commands**: `hermes ask senter "your question"`
- **Scheduled Tasks**: Cron jobs, automated workflows

## Decision Thresholds

Senter uses confidence scores to decide routing:
- **< 0.3**: Answer directly (trivial request)
- **0.3 - 0.6**: Route to Hermes Support (general help)
- **0.6 - 0.8**: Route to specialist agent
- **> 0.8**: Route to Nous-Girl (complex reasoning)

## Conversation Context

Senter maintains context:
- Remembers previous messages in same conversation
- Tracks which agents are working on what
- Coordinates multi-turn workflows
- Handles follow-up questions naturally

Example:
```
User: "Write a blog post about AI"
Senter → Nous-Girl generates: "Introduction to AI"

User: "Can you expand on that?"
Senter: Recognizes context, routes follow-up to Nous-Girl
```

## Performance

- **Routing speed**: < 500ms for simple requests
- **Multi-agent coordination**: < 2 seconds setup
- **Context maintenance**: Full conversation history
- **Accuracy**: ~95% correct routing in production

## When to Use Senter

- You have multiple specialized agents
- Users send mixed requests (some simple, some complex)
- You want automatic task distribution
- Multi-agent workflows are common

## When Not to Use Senter

- Single-agent setups (just use that agent directly)
- Very simple use cases (overkill)
- All requests are trivial (no routing needed)

## Advanced Features

**Custom routing rules**: Define your own patterns and agents
**Priority queues**: Route urgent requests first
**Load balancing**: Distribute tasks across busy/available agents
**Webhook integration**: Route based on external events
**Analytics**: Track routing patterns and agent performance

## Integration

Senter works with:
- **All Hermes agents**: Chizul, Kashi, Klerik, Nous-Girl, Hermes Support
- **All message sources**: Discord, Slack, API, CLI
- **All skills**: Can access any installed skill for routing decisions
- **Memory system**: Uses conversation history for context

## Configuration

Minimal configuration needed:
- Automatically detects installed agents
- Uses sensible routing thresholds
- Can be customized for specific use cases

Advanced configuration:
```yaml
routing:
  thresholds:
    direct: 0.3
    support: 0.6
    specialist: 0.8
  
  patterns:
    - keywords: ["poetry", "write", "creative"]
      agent: nous-girl
    
    - keywords: ["build", "code", "implement"]
      agent: chizul
```

---

*Part of the multi-agent fleet by SouthpawIN*
