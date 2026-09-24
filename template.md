---
apiVersion: learnx/v1
kind: Topic
metadata:
  id: com.example.my-topic          # unique, stable, never reused
  version: 1                        # raise by 1 whenever you change the content
  labels:                           # optional, free-form, for grouping
    level: A2
spec:
  language: de-DE                   # the language that gets spoken
  translationLanguage: en-US        # only if you write translations
  settings:                         # optional, all keys optional
    repetitions: 3                  # 1…5
    examplesPerItem: 1              # 0…3
    echoPause: 2.0                  # 0.5…5.0 seconds
    speechRate: 0.85                # 0.5…1.2
    loopSection: true
---

# My topic

One or two sentences about what this topic teaches. Shown before anyone downloads it.

## First section

### das Wort

*the word*

eine einfache Erklärung in der Sprache des Themas

> Eine Notiz. Wird angezeigt, aber nie vorgelesen.

- Das Wort steht im Satz.
  *The word is in the sentence.*
- Ich kenne dieses Wort.
  *I know this word.*

### Ein ganzer Satz kann auch ein Eintrag sein.

*A whole sentence can be an item too.*
