# Whispr Journal · Implementation choices

The main custom logic is lifecycle handling around Apple’s speech and persistence APIs, rather than a self-trained speech model.

## 1. Session identities prevent stale speech callbacks

Starting and stopping dictation changes a session UUID. Permission checks and recognition callbacks capture the active session. Before applying a result, the manager compares the captured UUID with the current one.

Example: the user stops recording, edits the draft and immediately starts again. A late callback from the first recognition task should not replace text in the new session. The identity check gives those callbacks a way to recognize that they are obsolete.

The manager also prevents overlapping starts with `isRecording` and `isStarting`, and cancels the recognition task/removes the microphone tap on stop.

## 2. Partial transcription appends to a stable draft prefix

At the start of a dictation session, existing draft text becomes `baseTranscript`. Each partial recognition result replaces the session’s recognized portion and is joined to that base.

This avoids repeatedly appending the entire partial transcription as it grows. A user can stop and continue dictation while retaining the text already entered.

## 3. A simple audio activity meter

The microphone tap computes the mean absolute sample amplitude. A scaled and clamped value drives the activity display. This is visual feedback for recording, not a calibrated sound-level measurement or frequency analysis.

## 4. Lightweight book-mode pagination

The reader walks through words, accumulating approximate character count. When the next word would exceed the 700-character target, it starts another page. Words remain intact, and a final partial page is retained.

The pass is linear in text length. The character target is a presentation heuristic; it does not measure glyphs against the actual viewport. Scrollable page content handles text that exceeds the visible area.

## 5. Search over the local entry collection

Search checks a case-insensitive substring against entry titles, content and tags, optionally combined with the favorite flag. It is a straightforward filter over fetched entries, not a full-text search index or semantic/vector search service.

## 6. Save and lock lifecycle

Saving first stops dictation, normalizes the title/content and inserts the entry. If the explicit save fails, the draft stays on screen. For access control, moving to the background relocks the app when enabled; successful device-owner authentication releases the lock overlay.

[Architecture](ENGINEERING.md) · [Local data model](DATA_MODEL.md)
