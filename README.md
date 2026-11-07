# ¡Conoce a Colombia! — Spanish Vocabulary Games

Browser-based vocabulary games for high-school **Spanish 1** and **Spanish 2** classes, built around a Colombia unit. Each level has **26 game modes** that all run from one shared vocabulary list, so adding a word adds it to every game at once.

Built by [Wade Swede](https://wswede1.github.io/), Spanish teacher and computational linguist.

## Play

Open `index.html` from the published site and pick a level:

| Level | Page | Vocabulary |
|---|---|---|
| Spanish 1 | `span_1/unidad_colombia/Colombia_Vocab_Review_Spanish1.html` | Colombia & culture, -ER/-IR verbs, *gustar*, *estar* + location, *ir* + places, classroom vocabulary |
| Spanish 2 | `span_2/unidad_colombia/Colombia_Vocab_Review_Spanish2.html` | Travel, regular and spelling-change preterite, *-y-* preterites, stem-changing and irregular preterites |

No account, no sign-in, no analytics. Built for school Chromebooks, tablets and phones.

## Game modes

| Group | Modes |
|---|---|
| Vocab | Flashcards, Quiz, Match, Scramble, Hangman, Whack-a-Word, Memory, Word Search, Crossword, Chain |
| Listen | Listen, Echo (record and compare), Odd One Out |
| Read | Fill in the Blank, True/False |
| Grammar | Conjugation Blitz, Sort It, Build a Sentence, Gender |
| Write | Translation, Prompt Response, Mad Libs |
| Arcade | Falling Words, Quiz Race, Boss Battle |
| Culture | Dialogue |

## How it works

- **One data file per level** (`unidad_colombia/student_site_assets/data/colombia-vocab-sp1.js`, `…-sp2.js`) holds `{ es, en }` pairs grouped into themes. The page builds an **All unit** deck by merging the themes and dropping duplicates, ignoring accents.
- **Every game reads from the active deck.** Students can pick one or more themes. Some modes use extra structure: *Gender* uses nouns with *el/la*, *Conjugation Blitz* uses infinitives (present tense in Spanish 1, preterite in Spanish 2), and *Sort It* uses the theme labels.
- **Answer checking ignores accents and capitals** (`montana` matches *montaña*), so typing on a Chromebook isn't punished, while the correct spelling is always shown in the feedback.
- **Audio:** each word plays a pre-generated neural-TTS recording (`audio/vocab-sp1-<slug>.mp3`). If there's no recording, the game falls back to the browser's Spanish speech synthesis.
- **Optional adaptive mode** (`?adaptive=1`): a spaced-repetition (FSRS) and knowledge-tracing (BKT) layer stored in the browser's IndexedDB. Without a local student profile it stays off and the full deck is used.
- **No build step or framework:** plain HTML, CSS and JavaScript. The only third-party files are Google Fonts and Dexie (IndexedDB wrapper) from a CDN.

## Privacy

Progress lives only in the student's own browser (localStorage / IndexedDB). Nothing is sent to a server operated by this project. *Build a Sentence* and *Prompt Response* were designed to optionally use an AI model for feedback. That is **turned off in this deployment** (no API key is ever shipped in a public page), so those two modes show students their own answer back without grading it.

## Run locally

The pages load the vocabulary over HTTP, so serve the folder instead of opening the file directly:

```bash
python3 -m http.server 8890
```

Then open http://127.0.0.1:8890/.
