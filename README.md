# Cossert Chess Board AI

A graphical browser chess game powered by the Cossert chess engine.

## Architecture

- `index.html` — graphical 8x8 chess board, click controls, animation/state display
- `interpreter.js` — runs Cossert in the browser
- `chess.cos` — chess rules, legal move generation, king safety, check/checkmate, evaluation, and AI move selection
- `README.md` — this file

The browser UI sends your selected FROM/TO square IDs into the Cossert program. The Cossert program updates the position and chooses Black's move. The UI reads the board state printed by Cossert and redraws the pieces.

If `chess.cos` is removed or broken, the AI cannot play.

## Play

You are White. Click a White piece, then its destination. The Cossert AI responds as Black.

## Current engine limitations

This build is based on the Cossert chess engine v0.1:
- normal legal moves
- check/checkmate/stalemate
- self-check filtering
- material evaluation
- mate-in-one detection
- automatic queen promotion

Not yet implemented:
- castling
- en passant
- underpromotion

## GitHub Pages

Upload all four files to the repository root, then enable GitHub Pages.

For local testing:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
