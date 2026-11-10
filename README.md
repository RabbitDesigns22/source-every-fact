# source-every-fact

**Every price, phone and name on a post comes from a source, or it does not go on the post.**

`source-every-fact` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Agents fill gaps on client work: "shipping not included", "one-time payment", an old phone number, a discount nobody asked for. Or they write a true price in a way that reads as another number. The client sees it first.

With the skill, the agent builds a fact sheet before any copy or layout (fact, exact value, source, date). Only those facts go on the piece, and nothing the source did not say is added. It reads the finished piece the way a customer scrolling past would, checks phones and prices character by character in the exported file, counts the digits, opens every WhatsApp link, and ends with a fact / source / match table.

## See the difference

> **Client:** "Put 700 pesos and my WhatsApp."
> **Draft on the image:** "From 2 pcs 500 each · One-time payment · Shipping extra · $700"

**Without the skill:** it removes the extra lines because they contradict the 700. It does not notice that "2 pcs 500" reads as "2500" to a customer, and it gives no source for each fact.

**With the skill:** it removes the three lines (no source), flags the "2500" misreading, keeps "$700" and the WhatsApp number checked digit by digit, and ends with:

| Fact | On the piece | Source | Match |
|---|---|---|---|
| Price | $700 | client message, 8 Nov | ok |
| WhatsApp | 55 1234 5678 | same message | ok, 10/10 digits, link opened |
| "from 2 pcs 500 each", "one-time payment", "shipping extra" | removed | none | removed |

**Skip it if** the piece has no hard facts (no price, number, name, date or terms).

**Status:** new. Built from four real complaints in the author's own setup. Tested with and without the skill on 3 cases: 5.5/6 with it, 4.5/6 without. Plain instructions, no scripts, no network calls. MIT. Issues and suggestions welcome.

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills add RabbitDesigns22/source-every-fact
```

Or manually: copy `skills/source-every-fact/` into `~/.claude/skills/` for all your projects, or into `.claude/skills/` for one project.

## Works well with

- [`published-vs-planned`](https://github.com/RabbitDesigns22/published-vs-planned): after the post goes out, checks it is really live.
- [`proposal-pdf`](https://github.com/RabbitDesigns22/proposal-pdf): proposals with every price checked against its source.

## Español

**Cada dato con su fuente.** Antes de diseñar, el agente arma una tabla con cada precio, teléfono, nombre y condición, y de dónde salió. En la pieza solo va lo que está en la tabla: nada de "desde", "pago único" o "envío aparte" si el cliente no lo dijo. La lee como la leería un cliente ("2 piezas 500" se lee "2500"), revisa los teléfonos dígito por dígito y abre el enlace de WhatsApp.

Instalar: `npx skills add RabbitDesigns22/source-every-fact`

## More skills from the same setup

These come from one real workflow: a small agency run with 15+ Claude Code sessions in parallel. Each skill fixes one problem that kept happening there.

| Skill | What it fixes |
|---|---|
| [one-pass](https://github.com/RabbitDesigns22/one-pass) | get it right the first time; stop paying tokens for rework |
| [hora-exacta](https://github.com/RabbitDesigns22/hora-exacta) | real date and time in every message, so nothing lands on the wrong day |
| [hands-on](https://github.com/RabbitDesigns22/hands-on) | the agent does what it can and only asks you for codes, keys and payments |
| [easy-for-them](https://github.com/RabbitDesigns22/easy-for-them) | steps people actually follow: direct link, one action per line |
| [one-answer](https://github.com/RabbitDesigns22/one-answer) | one thought-through answer instead of plan, fix, new plan |
| [never-twice](https://github.com/RabbitDesigns22/never-twice) | a shared error log so no session repeats a known mistake |
| [sort-me-out](https://github.com/RabbitDesigns22/sort-me-out) | one ordered list of what is urgent, waiting and forgotten |
| [in-the-loop](https://github.com/RabbitDesigns22/in-the-loop) | a live board so parallel sessions know what the others changed |
| [study-first](https://github.com/RabbitDesigns22/study-first) | reads everything in full and answers point by point, no invented details |
| [session-watchdog](https://github.com/RabbitDesigns22/session-watchdog) | wakes the sessions that got stuck mid-task, leaves the rest alone |
| [skill-harvest](https://github.com/RabbitDesigns22/skill-harvest) | reads your sessions and finds the skills you are missing |
| [small-budget-ads](https://github.com/RabbitDesigns22/small-budget-ads) | Meta Ads rules for 1-5 USD a day ad sets |
| [whatsapp-closer](https://github.com/RabbitDesigns22/whatsapp-closer) | evidence-ranked rules for a WhatsApp sales assistant that closes |
| [whatsapp-number-onboarding](https://github.com/RabbitDesigns22/whatsapp-number-onboarding) | connect a number to the WhatsApp Cloud API in the safe order |
| [proposal-pdf](https://github.com/RabbitDesigns22/proposal-pdf) | short PDF proposals with every price checked against its source |
| [published-vs-planned](https://github.com/RabbitDesigns22/published-vs-planned) | says "published" only for what it saw live on the public page, Facebook and Instagram checked apart |
| [source-every-fact](https://github.com/RabbitDesigns22/source-every-fact) | every price, phone and name on a post traced to its source, nothing added |
| [only-what-was-asked](https://github.com/RabbitDesigns22/only-what-was-asked) | "pause only Google Ads" pauses only Google Ads, and proves the rest did not move |
| [model-per-chat](https://github.com/RabbitDesigns22/model-per-chat) | the right model for each chat: top model where mistakes cost money, cheap or none where it only runs often |

If one of them saved you a redo, a star helps other people find it.

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
