# Contributing a book

Anyone can add their custom *Book of Tales* supplement to this registry. Books
appear in the Community Books section of the
[Book of Infinite Tales](https://github.com/RobMcA/Book-of-Infinite-Tales)
reader app.

## Before you submit

1. **Host your book in a public GitHub repo.** It must contain either:
   - A `book.json` at the root (single book), or
   - A `books.json` at the root (collection of books in subdirectories).

   `book.json` holds the book's metadata and passages. If your book uses the encounter picker (Ages, Characters, Locations, Milieus, Quests), also include a components file (e.g. `components.json`) and declare it in `book.json` as `"components": "components.json"`. Multiple books in a collection can share the same components file.

2. **Test it in the app** by pasting your repo URL into the reader at
   [book-of-infinite-tales.github.io](https://book-of-infinite-tales.github.io)
   (or `owner/repo` shorthand). The book must load without validation errors.

3. **Check for copyright.** Do not include any official *Tales of the Arthurian
   Knights* text, images, or other copyrighted material. Fan-created content
   only.

## How to submit

Open a pull request that adds one entry to `registry.json`:

```json
{
  "repo": "your-github-username/your-repo-name",
  "title": "Your Book Title",
  "author": "Your Name",
  "description": "One sentence describing your book.",
  "tags": ["optional", "tags"]
}
```

For a **collection** (multi-book repo using `books.json`), omit `path`.

For a **specific book inside a collection**, add the subdirectory as `path`:
```json
{
  "repo": "your-github-username/your-repo-name",
  "path": "path/to/book",
  "title": "...",
  ...
}
```

The CI workflow will automatically fetch your book and verify it is reachable
and well-formed. Your PR cannot be merged until CI passes.

## Registry fields

| Field | Required | Description |
|---|---|---|
| `repo` | Yes | `owner/repo` on GitHub |
| `path` | No | Subdirectory path if not at repo root |
| `title` | Yes | Display title shown in the app |
| `author` | Yes | Your name or handle |
| `description` | No | One sentence shown beneath the title |
| `tags` | No | Array of freeform strings (e.g. `["quest", "forest"]`) |
