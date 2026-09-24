# learn-x-data

Topics for [LearnX](https://github.com/tugbayatilla/learn-x). One Markdown file per topic.
The app reads this repository, ignores any file that is not a topic, and downloads the ones you pick.

Start from [`template.md`](template.md).

## The file

Two parts: YAML front matter for what the app needs to know, Markdown for the content.

```yaml
---
apiVersion: learnx/v1
kind: Topic
metadata:
  name: loyalitaetserklaerung-nrw
  version: 1
  labels:
    level: B1
    region: nrw
spec:
  language: de-DE
  translationLanguage: en-US
---
```

| Key | Required | Meaning |
|---|---|---|
| `apiVersion` | ✔ | Always `learnx/v1`. A file without it is ignored. |
| `kind` | ✔ | Always `Topic`. |
| `metadata.name` | ✔ | Unique **in this repository**. Identity is repository + name, so another repository may use the same name. |
| `metadata.version` | – | A whole number. **Raise it by 1 every time you change the content**, or the app will not re-download. |
| `metadata.labels` | – | Free-form pairs for grouping: `level`, `region`, whatever you need. |
| `spec.language` | ✔ | What gets spoken, e.g. `de-DE`. Picks the voice. |
| `spec.translationLanguage` | – | The language your translations are in. Needed only if you write any. |
| `spec.settings` | – | Playback defaults for this topic: `repetitions` 1–5, `examplesPerItem` 0–3, `echoPause` 0.5–5.0, `speechRate` 0.5–1.2, `loopSection`. Anything else is ignored and reported. |

## The content

```markdown
# Loyalitätserklärung

Wörter und Konzepte aus der Loyalitätserklärung für die Einbürgerung in NRW.

## Grundbegriffe

### das Grundgesetz

*the Basic Law*

die deutsche Verfassung

> Nicht „Grundgesetzt" — ohne t am Ende.

- Das Grundgesetz gilt seit 1949 in Deutschland.
  *The Basic Law has been in force in Germany since 1949.*
```

| You write | It becomes |
|---|---|
| `# Heading` | the topic's title |
| the paragraphs under it | what the topic is about, shown before downloading |
| `## Heading` | a **section** — playback repeats one section at a time |
| `### Heading` | an **item** — this is the text that gets spoken and repeated |
| `*italic line*` under an item | that item's translation |
| a plain paragraph under an item | a simple explanation, in the topic's own language |
| `> quoted line` | a note — shown on the card, never spoken |
| `- bullet` | an example sentence |
| an indented `*italic*` line under a bullet | that example's translation |

Order matters: translation, explanation, note, examples. Everything except the `###` line is optional.

## Rules

- **One topic per file.** The file name is yours to choose; `metadata.name` is what identifies it here.
- **Raise `version` when you change anything.** That is the only signal the app has that a topic moved on.
- Write the explanation in the topic's own language, simply. It is for a learner, not a dictionary.
- Keep an item to one idea. A three-sentence passage is fine as an item, but do not stack unrelated ones.
- Files that are not topics — this README, notes, drafts — are ignored. Nothing needs a list of what exists.
- Anything the app does not understand is skipped and named, never silently dropped.
