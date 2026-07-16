# Kenshi C++ API Browser (RE_Kenshi / KenshiLib)

A single self-contained, offline HTML reference for the reverse-engineered C++ API of **Kenshi** (Steam v1.0.65), for writing plugin mods with the **RE_Kenshi + KenshiLib** SDK.

> 🌐 **Online (GitHub Pages):** `https://regulareverydaynormalmazaf.github.io/ReKenshi_KenshiLib_Swagger/` — opens right in the browser.
>
> 💾 **Offline:** download `ReKenshi_KLIB_kinda_swagger.html` and double-click it — no internet needed.
>

---

## English

A searchable index of Kenshi's reverse-engineered C++ API — **484 classes, ~3900 fields, ~11900 methods, 134 enums**. The data comes from headers reverse-engineered off the game executable (`kenshi_x64.exe`): the reference has the **declarations and addresses** of functions/fields, but not their internal logic — that stays inside the game's closed code.

It helps with the core tasks of Kenshi C++ modding: find a function/field, read its signature and allowed values, see how to install a **hook** (`KenshiLib::AddHook`), and how to navigate between classes by pointers. It surfaces hooking flags (`V` virtual, `_NV_` non-virtual twin, `NO_ADDR`), RVA addresses, **vtable slots**, value domains for fields and arguments (enum/bool sets — nothing invented), **field↔method** accessor links marked **A** (proven by the header) or **B** (name heuristic), and **real code examples** cited from open mods (✅) or structural templates (⚠️). The interface is bilingual (EN/RU), with deep-links to a class, member, enum, external type and the current filter state.

**Confidence.** Every datum is sourced. We do **not** decompile compiled third-party mod DLLs. Real examples come only from **open-source** mods and are cited by file. What a function actually does is compiled into the `.exe`; names, links and domains only hint at meaning — the final check is compiling in Visual Studio and testing in-game.

### Credits & sources

This reference is built on open community projects — **huge thanks to their authors**. It would not exist without the reverse-engineering and SDK by **BFrizzleFoShizzle** and the contribution of **weisspure**.

Materials used (reconstructed headers, code examples, dependencies):

- **RE_Kenshi** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/RE_Kenshi> — **GPL-3.0**
- **KenshiLib** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib> — **GPL-3.0**
- **KenshiLib_Examples** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib_Examples> — **GPL-3.0**
- **KenshiLib_Examples_deps** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib_Examples_deps> — bundles **Boost 1.60** (Boost Software License 1.0)
- **re_kenshi-working-solution** — © weisspure — <https://github.com/weisspure/re_kenshi-working-solution> — **GPL-3.0**

> The KenshiLib / RE_Kenshi projects are **GPLv3**; per KenshiLib, derivative works and plugins must also be **GPLv3**, so this reference is likewise released under **GPL-3.0** with the attributions above. All rights to the source materials belong to their respective authors.

### Help improve the examples — share your mod's source

The most valuable part of this reference is **real examples from working code**. If you've built a working RE_Kenshi / KenshiLib mod, please share its **source code**:

- 📧 email **u1host@proton.me** — as a zip archive or a link to your GitHub repository;
- or any other convenient way.

**What happens to your code:**

- Your source **will not be published in any form** — not in full, not in a repo, nowhere.
- It is only **processed locally**, and individual call-site lines are extracted as examples — exactly like the existing verified examples (a short snippet + a note on which mod it came from).
- If you'd rather not have your mod named, just say so and we'll drop the attribution.

This lets the reference grow with many more verified, illustrative examples for the whole Kenshi modding community. Thank you! 🖤

### Usage

1. Open it online via the Pages URL **or** download `index.html` and double-click it (no internet needed).
2. Pick a class on the left, expand domains → members → a row; read the facts, value domains and examples; copy the RVA, signature, vtable slot and hook skeleton.

### GitHub Pages

To serve it by link: repo → **Settings** → **Pages** → under *Build and deployment* choose **Deploy from a branch**, branch **main**, folder **/ (root)** → **Save**. In ~1–2 minutes the `https://<user>.github.io/<repo>/` URL serves `index.html`.

### Limitations

- Function internals are unavailable (closed-source game).
- For ~369 virtual methods the vtable slot wasn't reconstructed (`0x0` in headers); 329 of them are still hookable via the `_NV_` twin (RVA), only 33 pure-virtual methods without RVA truly need it.
- Code examples cover part of the API and grow as open sources arrive (see the call above).

### License

**GPL-3.0**, as a derivative work of KenshiLib / RE_Kenshi — see “Credits & sources”.

*Target: Kenshi 1.0.65 Steam · KenshiLib · RE_Kenshi. Unofficial project, not affiliated with Lo-Fi Games.*
