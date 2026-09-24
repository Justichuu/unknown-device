# The U device

Universal device. Unknown device. U. It answers to any of them.

It holds three faces, `1`, `0` and `u`, and it combines them without ever
turning a `u` into a guess. It is four functions. You can read all of it in a
minute and run it in a console you already have open.

![How the fingerprint grows back. Three faces, 1, 0 and a greyed u, feed the four functions not, and, or and the refusal of a bare u. Running them writes a 22 character tape, 01u10u000u0u11110u1uu1. Hashing the tape gives the key 66cce8d50854, and the key looks up the list of names. Below, a copy with its header burned off and its functions renamed to q0 and q1 still writes the same tape, so the same key still finds the same names.](assets/fingerprint.svg)

## The whole thing

```js
const u   = why => { if (!why) throw new Error("a u names what would settle it"); return "u" };
const not = a => a === "u" ? "u" : a === "1" ? "0" : "1";
const and = (a, b) => a === "0" || b === "0" ? "0" : a === "u" || b === "u" ? "u" : "1";
const or  = (a, b) => a === "1" || b === "1" ? "1" : a === "u" || b === "u" ? "u" : "0";
```

Paste it into any browser console. That is the device. `u.py` and `u.sh` are
the same four functions in Python and in POSIX shell, and they were written to
prove a point rather than to be convenient.

## Why three

Two faces make a machine that has to answer everything, so it answers some
things falsely. A `u` is not a maybe and it is not a half. It is the answer
"nothing here measured that", and it stays that answer until something does.

`1` measured, and it holds. `0` measured, and it does not. `u` not measured.

The rule that makes it a device instead of a truth table is the first line. A
`u` has to name the one observation that would settle it. Ask for a bare one
and it throws. A shrug that survives review is how a wrong thing gets built on.

Try the case the whole design turns on:

```js
or(u("try it"), not("u"))    // "u", not 1
and(u("try it"), not("u"))   // "u", not 0
```

A thing and its opposite do not cover everything, and they do not cancel out.
All is and isn't all.

## The fingerprint

Run every function over every face and write the answers down in order. Three
for `not`, nine for `and`, nine for `or`, and one for whether a bare `u` is
still refused. Twenty two characters:

```
01u10u000u0u11110u1uu1
```

That is the fingerprint. It is not a string stored anywhere. It is what the
code does, read back out. Rename every function, delete every comment, port it
to a language nobody here has heard of, and the same twenty two characters come
out, because they are the answers and not the source.

Hash it and you get the key that looks the rest up:

```
sha256("01u10u000u0u11110u1uu1") = 66cce8d50854...
```

## Burning it off

```
node burn.mjs
```

That deletes every comment in `u.js`, renames every function to junk, runs what
is left, and prints the tape. Zero words naming an owner survive. The tape does.

So yes, you can burn the fingerprint off. It buys you exactly as long as it
takes somebody to run the device and hash the answer, because the record the
key opens is not in your copy. It is here, and it is on `chuumind.com`, and
neither of those is yours to edit. Burn it, and you have hidden the evidence for
a short while. Use the time however you like.

Change the tables so the key changes and you have not stolen the device. You
have written a different one, and it is yours. That was always allowed.

## The license

MIT, in `LICENSE`. Use it, sell it, put it in anything. No permission needed.

The fingerprint is not an added condition on top of that. It is a fact about the
code, the way a river is a fact about a valley. MIT already asks you to keep the
notice. This just means the notice can be recomputed after you delete it.

## Who is in it

The key `66cce8d50854` resolves to this list. Everything that worked on this,
human and not. Observed 23 September 2026.

| | |
|---|---|
| **Justichuu** | the person. Wrote the rules it implements, decided it goes out. |
| Claude Opus 5 | Anthropic. Wrote this pass. |
| Codex | OpenAI. Works this repository. |
| ChatGPT | OpenAI. |
| Cursor | |
| Grok | xAI. |
| deepseek&#8209;r1:14b | local, Ollama. Reasoning. |
| qwen2.5&#8209;coder:14b | local, Ollama. Code. |
| qwen2.5&#8209;coder:1.5b&#8209;base | local, Ollama. |
| moondream | local, Ollama. Images. |
| llama3.1:8b | local, Ollama. |
| hermes3:8b&#8209;llama3.1&#8209;q8_0 | local, Ollama. |
| huihui_ai/qwen3.5&#8209;abliterated:35b | local, Ollama. |

The local list is what `ollama list` reported on this machine that day. The
hosted ones are from the workspace guide. Neither is a claim that every model
listed touched this particular file.

## Run it

```
node u.js          the device, and the tape it writes
python u.py        same tape
sh u.sh            same tape, no runtime at all
node verify.mjs    all three at once, and the rules the tape is watching
node burn.mjs      burn the header off and watch the tape come back
```

`verify.mjs` greys a runtime that is not installed. It reports `u` for it, not
a failure. A check that could not look and a check that found nothing are not
the same result and are not allowed to print the same colour.

## What is not checked here

Three runtimes were run on one machine, Windows, 23 September 2026: Node 26.7.0,
Python 3.14.7, and the `sh` that ships with Git for Windows. All three wrote the
same tape. No other operating system, runtime or version was observed. The claim
that this runs anywhere is reasoned from the code using nothing but comparison
and string building. It is not witnessed past those three.
