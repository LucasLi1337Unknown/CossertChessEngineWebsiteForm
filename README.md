# Cossert Chess Board AI — v0.2.1 FIXED

This build fixes the catastrophic disappearing-king / disappearing-piece bug.

## What was broken

The AI simulated one candidate move, then called the legal-move generator while
that simulation was still active. The legal-move generator performed more
simulations using the SAME global undo variables. Those nested simulations
overwrote the saved board state, so the outer undo could restore the wrong
pieces. That is why a king could disappear.

## Fix

The AI now completely finishes and undoes each candidate simulation before any
other move-generation pass can overwrite its undo state. The engine also gets
basic development bonuses so equal-material moves do not make it mindlessly
push whichever pawn happens to occur first.

## Chess correctness already enforced

- kings are never captured
- a move that leaves your own king in check is illegal
- check is detected from enemy attacks
- checkmate/stalemate are distinguished by whether the side with zero legal
  moves is currently in check
- queen promotion is supported

## Still NOT complete yet

Castling and en passant are NOT in this build. I am deliberately not claiming
otherwise. Those require persistent move-history state (king/rook moved flags
and the immediately previous double-pawn move) and should be implemented as
real Cossert engine state rather than faked in JavaScript.

All files stay in the repository root for GitHub Pages.
