# ru-text-skills

🇷🇺 [Русская версия](README.ru.md)

Three skills for working with Russian-language text in [Claude](https://claude.ai) / Claude Code. Each owns its own layer and stays out of the others' — run them separately or chain them into one pipeline.

| Skill | What it does | Layer |
|---|---|---|
| **editor-ru** | Cuts fluff, fixes logic and ordering, untangles phrases, tightens the text | Structure and meaning |
| **humanizer-ru** | Removes signs of AI generation while keeping a living authorial voice | Style |
| **proofreader-ru** | Fixes spelling, punctuation, typos, agreement | Mechanics |

## Why

Default AI text is recognizable in a second: watery intros, clichés like «в современном мире», dash overdose, a perfectly smooth rhythm with no living person audible in it. A single "make it better" prompt fixes everything at once and badly — because "structure", "AI fingerprint" and "commas" are three different jobs with three different lenses.

Hence three separate skills. Each knows its zone and **doesn't touch the others'**: editor doesn't fiddle with commas, proofreader doesn't rewrite style, humanizer doesn't throw out the author's ideas.

## Pipeline

The logical order is from coarse to fine:

```
editor-ru  →  humanizer-ru  →  proofreader-ru
(structure)   (AI fingerprint)  (errors)
```

First put meaning and structure in order, then remove the AI style, finally proofread the mechanics. Each skill is self-sufficient — if you only need one layer, run only that one.

## Skills

### editor-ru — structural editor

The lens of «Пиши, сокращай» / Maxim Ilyakhov. Makes the text dense and clear: removes filler sentences, collapses repeated ideas, fixes logical transitions and ordering, splits overcomplicated sentences, aligns "promised — delivered".

Doesn't touch AI stylistics and doesn't go near spelling — those are the other two skills. Has overshoot protection: won't cut down to telegraph style and won't throw out the author's ideas, examples and numbers.

**When:** «отредактируй», «много воды», «сократи», «структура хромает», «запутанно», «приведи в порядок».

### humanizer-ru — anti-AI for blog content

Removes generation traces from posts and articles (Telegram, vc.ru, Habr): AI vocabulary, bureaucratese, dash overdose, paired constructions, rule of three, mentor tone, dead even rhythm. The goal is text a competent author with their own voice could have written, not a conversational retelling.

Universal and voice-neutral. A separate variant exists for academic and legal texts (`humanizer-ru-legal`, not included in this repository).

**When:** «звучит как ChatGPT», «сделай менее ИИ-шно», «слишком сухо/шаблонно», «выглядит как LinkedIn-пост».

### proofreader-ru — proofreader

Proofreads **mechanics only**: spelling, typos, punctuation, grammar and agreement, capitalization. Preserves the author's voice completely — slang, anglicisms, emojis, markup, line breaks are left alone. Doesn't check English text or typography (dashes/quotes).

The main principle is conservatism: when in doubt, don't touch. Breaking intentional slang is worse than missing a rare typo.

**When:** «проверь на ошибки», «вычитай», «корректура», «опечатки есть?».

## Installation

### Claude (claude.ai)

`Settings → Capabilities → Skills` → upload each skill's folder.

### Claude Code

Put the skill folders into the project's skills directory:

```bash
git clone https://github.com/USERNAME/ru-text-skills.git
cp -r ru-text-skills/editor-ru ru-text-skills/humanizer-ru ru-text-skills/proofreader-ru \
   .claude/skills/
```

The skills are picked up automatically and fire on the triggers from their descriptions.

## Structure

```
ru-text-skills/
├── editor-ru/
│   └── SKILL.md
├── humanizer-ru/
│   └── SKILL.md
├── proofreader-ru/
│   └── SKILL.md
├── LICENSE
├── README.md
└── README.ru.md
```

## License

MIT — do what you want, fork it, adapt it.
