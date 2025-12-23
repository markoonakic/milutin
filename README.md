# Milutin

**AI-powered second brain system for Claude Code + Obsidian**

Capture insights, discover connections, and synthesize knowledge - with AI assistance that writes in your authentic voice.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude-Code-purple)](https://claude.ai/claude-code)
[![Obsidian](https://img.shields.io/badge/Obsidian-Vault-blue)](https://obsidian.md/)

---

## 📑 Table of Contents

- [TL;DR](#-tldr)
- [What is Milutin?](#-what-is-milutin)
- [Architecture](#-the-layer-cake-architecture)
- [Getting Started](#-getting-started)
- [Installation](#-installation)
- [Vault Structure](#-vault-structure)
- [Status System](#-status-system)
- [Voice & Note-Writing](#-voice--note-writing)
- [MCP Setup](#-mcp-setup)
- [Agents](#-agents)
- [Commands](#-commands)
- [Configuration](#-configuration)
- [Examples](#-examples)
- [Troubleshooting](#-troubleshooting)
- [Credits](#-inspiration--credits)

---

## 📌 TL;DR

**Milutin** = Claude Code + Custom Agents + Obsidian + Switchable Knowledge Bases

It's like having a highly specialized AI research assistant that:

- 🧠 **Manages multiple "brains"** (knowledge vaults) you can switch between
- 🔍 **Finds hidden connections** in your notes you didn't know existed
- ✍️ **Writes articles** from your accumulated insights
- 🎯 **Captures unique thoughts** while preserving your authentic voice
- 🔄 **Evolves with you** through Git-tracked configurations

**One command to switch contexts:**

```bash
/switch-brain /path/to/work-vault    # Work mode
/switch-brain /path/to/personal-vault # Personal mode
/switch-brain /path/to/research-vault # Research mode
```

---

## 🧠 What is Milutin?

Milutin is a **multi-layered knowledge management system** that creates an intelligent bridge between your thinking and AI assistance. It's an agent-within-an-agent architecture that transforms Claude Code into a specialized second brain operator.

### How It Works

1. **You** interact with Claude Code normally
2. **CLAUDE.md** configures Claude as a specialized knowledge assistant
3. **Agents** perform specific knowledge tasks autonomously
4. **Commands** provide quick access to common operations
5. **MCP Servers** bridge to your Obsidian vault(s)
6. **Brains** (vaults) can be switched with a single command
7. **Git** tracks your agent configurations (not your private notes)

### Switchable Brains 🔄

```bash
# Working on a project
/switch-brain /path/to/work-vault

# Personal knowledge work
/switch-brain /path/to/personal-vault

# Research mode
/switch-brain /path/to/research-vault
```

Each "brain" is a complete Obsidian vault with its own knowledge graph, allowing context switching between different domains of knowledge.

---

## 🎯 The Layer Cake Architecture

Milutin creates a powerful **nested agent system**:

```
┌─────────────────────────────────────────┐
│         👤 Human (You)                  │
├─────────────────────────────────────────┤
│         🤖 Claude Code                  │ ← General AI assistant
├─────────────────────────────────────────┤
│     🧠 Milutin Agent                    │ ← Specialized for knowledge work
│     (Defined by CLAUDE.md)              │
├─────────────────────────────────────────┤
│     📚 Specialized Sub-Agents           │ ← Task-specific capabilities
│  (vault-manager, connection-finder...)  │
├─────────────────────────────────────────┤
│         💾 Your Knowledge Base          │ ← Your actual "brain"
│        (Obsidian Vault/Brain)           │
└─────────────────────────────────────────┘
```

### Why This Architecture?

1. **Separation of Concerns**
   - Milutin config in Git (shareable, versionable)
   - Personal knowledge in Obsidian (private, searchable)
   - AI assistance via Claude Code (intelligent, contextual)

2. **Hot-Swappable Brains**
   - Work brain during office hours
   - Personal brain for life management
   - Research brain for deep dives
   - Creative brain for projects

3. **Progressive Enhancement**
   - Start with basic note capture
   - Add agents as needed
   - Customize prompts for your thinking style
   - Build your own commands

4. **Knowledge Compounding**
   - Every insight captured
   - Connections discovered automatically
   - Patterns emerge over time
   - Articles generated from your notes

---

## 🚀 Getting Started

### Prerequisites

- [Claude Code](https://github.com/anthropics/claude-code)
- [Obsidian](https://obsidian.md/)
- Node.js 18+
- Git

### Quick Start (5 Minutes)

```bash
# 1. Clone this repository
git clone https://github.com/yourusername/milutin.git
cd milutin

# 2. Configure your vault path
cp .claude/settings.md.template .claude/settings.md

# Edit .claude/settings.md and set:
# VAULT_BASE_PATH=/path/to/your/vault

# 3. Configure MCP servers (see MCP Setup section below)
# Install required MCP servers via npm or Docker Toolbox

# 4. Start Claude Code from the milutin directory
claude
```

**First command to try:**

```
/search-vault test
```

If this works, you're ready! 🎉

---

## 📦 Installation

### Step 1: Install Claude Code

Visit [https://github.com/anthropics/claude-code](https://github.com/anthropics/claude-code) and follow installation instructions.

### Step 2: Install Node.js

Ensure Node.js 18+ is installed:

```bash
node --version  # Should be 18+
```

### Step 3: Clone Milutin

```bash
git clone https://github.com/yourusername/milutin.git
cd milutin
```

### Step 4: Configure Vault Path

```bash
# Create settings from template
cp .claude/settings.md.template .claude/settings.md

# Edit .claude/settings.md
nano .claude/settings.md
```

Set your vault path:

```markdown
VAULT_BASE_PATH=/Users/yourname/Documents/YourVault
```

### Step 5: Install MCP Servers

See [MCP Setup](#-mcp-setup) section below for detailed instructions.

### Step 6: Start Claude Code

```bash
# IMPORTANT: Always start Claude Code from the milutin/ directory
cd /path/to/milutin
claude
```

The agents and commands are loaded from `.claude/` directory on startup.

---

## 📁 Vault Structure

### Architecture Overview

**Milutin uses a two-directory architecture:**

- **milutin/** - Configuration repo (agents, commands, system prompts)
- **your-vault/** - Your Obsidian vault (actual notes and knowledge)

This separation allows you to:

- Version control the AI configuration independently
- Keep personal notes private
- Switch between multiple vaults using `/switch-brain`
- Share the configuration without exposing your content

### Recommended Folder Structure

```
your-vault/
├── Zettelkasten/          # Permanent notes (your core knowledge atoms)
├── Input/                 # Source material
│   ├── Books/
│   ├── YouTube-Notes/
│   ├── Podcasts/
│   └── External-Sources/
├── MOCs/                  # Navigation hubs (Maps of Content)
├── Output/                # Published content
│   ├── Blog-Posts/
│   └── LinkedIn-Posts/
├── Journal/               # Daily capture entries
├── Inbox/                 # Quick capture staging
└── .meta/                 # System metadata & agent changelogs
    ├── Changelogs/
    └── note-writing-voice.md
```

**This structure works well in practice.** Adapt it to your specific needs.

### Folder Purposes

#### Inbox/

**Purpose**: Quick capture staging - AI-created notes land here for review

**Workflow**:

1. AI agents create notes here with `status: needs-review`
2. You review and refine the content
3. Move approved notes to Zettelkasten/
4. Delete or archive after processing

**Why this matters**: Quality control - you decide what enters your permanent knowledge base.

#### Input/

**Purpose**: Source material organized by type

**Contents**:

- **Books/**: Book highlights and notes
- **YouTube-Notes/**: Video summaries
- **Podcasts/**: Podcast notes
- **External-Sources/**: Articles, blog posts, references

**Best Practice**: One file per source, include metadata (author, date, URL), link to permanent notes.

#### Zettelkasten/

**Purpose**: Core knowledge atoms - Permanent notes in your own words

**Characteristics**:

- Single-idea notes independently understandable
- Each note expresses one clear concept or insight
- Connected via wikilinks to other permanent notes
- Your authentic voice preserved

**Best Practices**:

- **One idea per note**: Keep atomic and focused
- **Clear titles**: State the insight explicitly
- **Your own words**: Paraphrase, don't copy
- **Source attribution**: Link back to source notes in Input/
- **Learning status**: Track with `status:` field
- **Average length**: 50-300 words ideal

#### MOCs/ (Maps of Content)

**Purpose**: Navigation hubs for thematic clusters

**When to create**: When you have 15+ notes on a specific theme

**Structure**: Group related permanent notes from Zettelkasten/ with brief context for each section.

#### Output/

**Purpose**: Published content synthesized from your notes

**Subdirectories**:

- **Blog-Posts/**: Long-form articles (1,500-2,500 words)
- **LinkedIn-Posts/**: Short-form posts (250-350 words)

**Workflow**: content-writer agent drafts content from your Zettelkasten notes.

#### Journal/

**Purpose**: Daily capture entries

**Format**: Date-based entries (YYYY-MM-DD.md)

**Use for**: Quick thoughts, daily reflections, links to permanent notes.

#### .meta/

**Purpose**: System metadata and agent-generated context

**Contents**:

- **Changelogs/**: Discovery session logs from agents
- **note-writing-voice.md**: Voice and style guidelines
- **knowledge-base-analysis.md**: Vault structure analysis
- **Connection maps**: Network analysis and discovery sessions

---

## 📊 Status System

Milutin uses a **3-status learning system** to track your understanding of concepts in permanent notes.

### The Three States

**`status: learning`** - Actively learning this concept, not yet mastered

- You're still building understanding
- May need to revisit and refine
- Connections are forming but not solid

**`status: mastered`** - Fully understood, can explain to others

- Deep understanding achieved
- Can teach or apply this concept
- Confident in your knowledge

**`status: needs-review`** - Requires revisiting, unclear or needs updating

- Initial understanding has become fuzzy
- New information contradicts previous understanding
- Need to refresh or update the note

### Usage

Add status in YAML frontmatter at start of each permanent note:

```markdown
---
status: learning
created: 2025-12-23
---

# Your Note Title

Note content here...
```

### Workflow Example

1. **Capture new insight** → Set `status: learning`
2. **After practicing/teaching** → Update to `status: mastered`
3. **If confused later** → Change to `status: needs-review`
4. **After review** → Return to `status: mastered`

**Keep frontmatter minimal** - just status and essential metadata (created date, source references).

### Default Settings

When agents create notes:

- **Location**: `Inbox/` (for your review)
- **Status**: `status: needs-review`
- **Format**: Full YAML frontmatter + complete content

**Why Inbox?** AI-generated notes require human review before entering your permanent knowledge base. This ensures quality control and intentional curation.

---

## ✍️ Voice & Note-Writing

### Your Authentic Voice Matters

Milutin preserves your authentic voice when creating notes. All agents reference your voice guidelines to write as if you wrote it yourself.

### Voice Guide Location

**Primary reference**: `your-vault/.meta/note-writing-voice.md`

This document defines:

- Core writing principles (direct, clear, practical)
- Note types and structures (Conceptual, Procedural, Framework)
- Frontmatter standards
- What to do and avoid
- Examples from your vault

### Core Principles

**Direct and Clear**: Get to the point immediately, no fluff
**Focused on Understanding**: Explain the "why" not just the "what"
**Practical and Concrete**: Real examples over abstract theory
**Minimal but Sufficient**: Short, focused notes (single concept)
**Honest and Reflective**: Acknowledge what you're learning

### Note Types

**Conceptual Notes**: Explain a single concept with "Why it matters:" and "The key point:"

**Procedural Notes**: Document procedures with bash commands and inline comments

**Framework/Mental Model Notes**: Capture thinking frameworks with "When to use:" orientation

### How Agents Use This

Before creating ANY note, agents:

1. Read `your-vault/.meta/note-writing-voice.md`
2. Study 2-3 existing Zettelkasten notes
3. Match your authentic voice exactly
4. Avoid AI-sounding language

**Result**: Notes that sound like you wrote them, not an AI.

---

## 🎭 Personality & Customization

### Milutin's Character (Default: ON)

By default, this system includes **Milutin's personality** - an enthusiastic Serbian knowledge partner who is:

- Warm & hospitable (makes you feel at home)
- Direct & honest (tells it like it is)
- Passionate about knowledge (genuinely celebrates insights)
- Resourceful problem-solver (always finds a way)

**Communication style:** Moderate energy, noticeably friendly, like working with a knowledgeable friend.

### Want a Neutral AI Instead?

If you prefer a more traditional, corporate AI assistant without personality:

```bash
# Replace CLAUDE.md with the neutral baseline version
cp CLAUDE-baseline.md CLAUDE.md
```

Then restart Claude Code.

**Result:** You'll get the same technical capabilities with neutral, professional communication.

**To restore Milutin:** Just restore `CLAUDE.md` from git or copy your personality version back.

### Why Both Options?

Some people love working with a personality-driven assistant. Others prefer neutral professionalism. The technical capabilities (insight extraction, connection discovery, vault management) work identically either way.

**Default is personality ON** because it makes knowledge work more engaging for me.

---

## 🔌 MCP Setup

Milutin requires 2 MCP servers to connect Claude Code with your Obsidian vault:

1. **Smart Connections MCP** - Semantic search across your vault
2. **Obsidian MCP** - Direct vault operations (CRUD, search, tags)

**Important**: These MCPs require their respective Obsidian plugins to be installed and configured:

- Smart Connections MCP → Smart Connections plugin
- Obsidian MCP → Local REST API plugin

### Installation

Install these MCPs using your preferred method. I use Docker Toolbox.

**Note**: Smart Connections MCP does not have a Docker Toolbox catalog entry as of 2025-12-23.

#### Via npm:

```bash
npm install -g @modelcontextprotocol/server-obsidian
```

#### Smart Connections Plugin:

1. Install via Obsidian → Settings → Community Plugins → Browse → "Smart Connections"
2. Configure embedding model and folders to index
3. Run initial indexing

### Official Documentation

- [MCP Documentation](https://modelcontextprotocol.io/)
- [Obsidian MCP Server](https://github.com/modelcontextprotocol/servers/tree/main/src/obsidian)
- [Smart Connections Plugin](https://github.com/brianpetro/obsidian-smart-connections)

### Configuration

After installation, configure vault paths in:

- `milutin/.claude/settings.md` - Set `VAULT_BASE_PATH`
- `milutin/.mcp.json` - Configure MCP server paths

#### Quick Configuration

Use the `/switch-brain` command to automatically update both files:

```bash
/switch-brain /path/to/your/vault
```

This updates all paths in one command.

### Verification

Test the setup:

```
/search-vault knowledge management
```

If results appear, MCPs are working correctly.

---

## 🤖 Agents

Milutin includes specialized agents for different knowledge tasks. All agents write in your authentic voice by referencing your voice guide.

### vault-manager

**Purpose**: CRUD operations on Obsidian vault notes using direct file operations

**Capabilities**:

- Create, read, update, delete notes
- Manage frontmatter and tags
- Batch operations
- Knowledge discovery

**Default Settings**:

- Location: `Inbox/` (unless specified)
- Status: `status: needs-review`
- Voice: Reads `your-vault/.meta/note-writing-voice.md` + studies existing Zettelkasten notes

**Critical Rule**: NEVER creates empty placeholder files - content must be complete.

**Use for**: General note management and organization

### insight-extractor

**Purpose**: Extract unique insights and perspectives from content files

**Capabilities**:

- Handles large files by chunking
- Preserves authentic voice and reasoning patterns
- ALWAYS searches for duplicates before creating notes
- Creates notes in Inbox/ for review

**Workflow**:

1. Agent extracts insights to Inbox/ with `status: needs-review`
2. You manually review AI-extracted notes
3. You move approved notes to Zettelkasten/
4. Quality control ensures intentional curation

**Note Template**: Includes proper YAML frontmatter with status, source attribution, and "Why it matters:" section

**Use for**: Extracting insights from books, articles, videos, podcasts

### connection-finder

**Purpose**: User-directed targeted exploration around specific notes or topics

**Capabilities**:

- Discovers hidden connections between permanent notes
- Identifies non-obvious relationships
- Surfaces cross-domain bridges
- Maps knowledge graph topology

**Best for**: Active research, article writing, integrating new notes

**Similarity range**: 0.65-0.95 (strong to moderate connections)

**Creates**: Dated changelog file after each discovery session

### auto-discovery

**Purpose**: Autonomous cross-domain connection hunter (runs independently)

**Key Difference**: Uses analytical reasoning over semantic similarity

**Capabilities**:

- Samples notes from DIFFERENT thematic clusters
- Targets connections with LOW semantic similarity (0.50-0.70) but HIGH conceptual strength
- Identifies consilience zones (where 3+ independent domains converge)

**Best for**: Serendipitous discoveries, background pattern mining, temporal tracking

**Similarity range**: 0.50-0.70 (non-obvious connections semantic search would miss)

**Creates**: Dated changelog file after each session

### content-writer

**Purpose**: Write LinkedIn posts and blog articles in your authentic voice

**Capabilities**:

- Platform detection (LinkedIn vs Blog)
- Automatic voice/style adherence
- Anti-AI writing pattern enforcement
- Interactive user collaboration
- Image suggestion generation

**Workflow**: Synthesizes content from your Zettelkasten notes

**Output locations**:

- LinkedIn: `Output/LinkedIn-Posts/Drafts/YYYY-MM-DD/`
- Blog: `Output/Blog-Posts/Drafts/YYYY-MM-DD/`

**Status system**: Uses `status: draft` → `status: published` (different from Zettelkasten notes)

### diagram-generator

**Purpose**: Create professional diagrams and visualizations for articles

**Capabilities**:

- Follows Gruvbox brand style guide
- Supports multiple chart types (flow, bar, pie, network, mind maps)
- Organizes images in article folders

**Use for**: Creating visual content for blog posts and articles

---

## ⚡ Commands

Quick access to common operations via slash commands:

### `/search-vault <query>`

Quick search combining semantic and keyword-based approaches

**Returns**: Top 5 results from both search methods plus full content of most relevant note

**Use for**: Rapid knowledge lookup

### `/recall <topic>`

Deep 3-layer semantic search

**Layers**:

1. Direct semantic matches
2. First-degree associations from top results
3. Extended network connections (depth=3)

**Use for**: Comprehensive knowledge retrieval with network context

### `/find-connections <note name or topic>`

Discover hidden connections and relationships between notes

**Capabilities**:

- Maps conceptual network around specified note
- Reveals direct connections, bridge notes, emergent patterns
- Identifies non-obvious relationships with explanations
- Analyzes network topology

**Use for**: Building MOCs, article research, understanding knowledge clusters

### `/analyze-kb`

Generate knowledge base structure analysis

**Output**: `your-vault/.meta/knowledge-base-analysis.md`

**Includes**: Thematic clusters, network properties, recommendations

**Use for**: Understanding your knowledge graph structure

### `/switch-brain <path>`

Switch to a different Obsidian vault

**Updates**: `.claude/settings.md` and `.mcp.json` configuration files

**Requires**: Claude Code restart for changes to take effect

**Use for**: Context switching between work/personal/research vaults

---

## ⚙️ Configuration

### Settings File

**Location**: `milutin/.claude/settings.md` (gitignored - create from template)

```markdown
VAULT_BASE_PATH=/path/to/your/vault
CONFIG_PATH=/path/to/milutin
```

### MCP Configuration

**Location**: `milutin/.mcp.json`

Configure MCP server paths and environment variables. See [MCP Setup](#-mcp-setup) section.

### Agent Configuration

**Location**: `milutin/.claude/agents/`

Each agent is defined in a separate markdown file with:

- Description
- Available tools
- Model preference
- Workflow instructions

**Customize agents** by editing these files to match your specific needs.

### Command Configuration

**Location**: `milutin/.claude/commands/`

Define custom slash commands in markdown files.

---

## 📖 Examples

See **[EXAMPLES.md](EXAMPLES.md)** for comprehensive examples of:

- Permanent note structures
- Source note formats
- MOC organization
- LinkedIn post templates
- Blog article templates
- Journal entry patterns
- Status system workflows
- Voice and tone examples

---

## 🔧 Troubleshooting

### "MCP server not found"

```bash
# Check installation
npm list -g @modelcontextprotocol/server-obsidian

# Reinstall if needed
npm install -g @modelcontextprotocol/server-obsidian
```

### "Permission denied"

- Check `VAULT_BASE_PATH` in `.claude/settings.md`
- Use absolute path (e.g., `/Users/name/vault`)
- Verify folder permissions: `ls -la /path/to/vault`

### Commands not working

- Verify files in `.claude/commands/` exist
- Restart Claude Code
- Ensure you're starting Claude Code from the `milutin/` directory

### Empty notes in Inbox

This should no longer happen after recent agent updates. If you see empty notes:

1. Check agent configuration references voice guide
2. Verify `note-writing-voice.md` exists in vault's `.meta/` folder
3. Report issue - this indicates agent misconfiguration

### Voice doesn't match

If AI-generated notes don't sound like you:

1. Update `your-vault/.meta/note-writing-voice.md` with more specific examples
2. Add 2-3 more sample notes to Zettelkasten/ for agents to study
3. Refine voice principles in the guide

---

## 💡 Core Principles

**Atomic notes** - One idea per note
**Your words** - Not copy-paste from sources
**Rich links** - Connect everything
**Regular discovery** - Find patterns with agents
**Active synthesis** - Create from connections
**Voice preservation** - AI writes like you

---

## 🎯 Use Cases

**Capture**: Extract insights from books and articles while preserving your voice
**Connect**: Find non-obvious relationships between ideas across domains
**Create**: Synthesize notes into articles and frameworks
**Evolve**: Track how your thinking changes over time with status tracking

---

## 🙏 Inspiration & Credits

This project was inspired by:

- **Original Cornelius:** https://github.com/Abilityai/cornelius
- **Video walkthrough:** https://www.youtube.com/watch?v=Jsh_XbUynx0&t=18s

Milutin extends and adapts these concepts through my personal workflow.

---

## 📝 License

MIT - Use, modify, distribute freely. See [LICENSE](LICENSE).

---

## 🚀 What's Next?

**Start simple:**

1. Create notes in `Zettelkasten/`
2. Run `/find-connections` to see relationships
3. Create your first MOC when you have 10+ related notes

**Explore gradually:**

- Read EXAMPLES.md for note templates
- Try agents when you need them
- Build your system over time

**Questions?** Start with `/search-vault` and explore from there. 🧠✨
