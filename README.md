# Kenshi C++ "API" RE_Kenshi + KenshiLib

A single self-contained, offline HTML reference for the reverse-engineered C++ API of **Kenshi** (Steam v1.0.65), for writing plugin mods with the **RE_Kenshi + KenshiLib** SDK.


> 💾 **Offline:** download `ReKenshi_KLIB_kinda_swagger.html` and double-click it — no internet needed.


---

## English

A searchable index of Kenshi's reverse-engineered C++ "API". The data comes from headers reverse-engineered off the game executable (`kenshi_x64.exe`): the reference has the **declarations and addresses** of functions/fields, but not their internal logic — that stays inside the game's closed code.

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

-----------------------------------------------------------------------------------------------------------

## Русский

Поисковый индекс реконструированного C++ "API" Kenshi. Данные получены реверс-инжинирингом игрового исполняемого файла (`kenshi_x64.exe`): в справочнике есть **объявления и адреса** функций/полей, но не их внутренняя логика — она остаётся в закрытом коде игры.

Справочник помогает решать главные задачи C++-моддинга Kenshi: найти нужную функцию/поле, понять её сигнатуру и допустимые значения, увидеть как поставить **хук** (`KenshiLib::AddHook`) и как переходить между классами по указателям. Показаны флаги хукабельности (`V` виртуальный, `_NV_` невиртуальный близнец, `NO_ADDR`), RVA-адреса, **слоты vtable**, домены значений полей и аргументов (наборы enum/bool — ничего не выдумано), связи **поле↔метод** с пометкой **A** (доказано заголовком) или **B** (эвристика по имени), и **реальные примеры кода** из открытых модов (✅) либо структурные шаблоны (⚠️). Интерфейс двуязычный (EN/RU), с deep-link на класс, член, enum, внешний тип и состояние фильтра.

**Достоверность.** Каждое значение имеет источник. Мы **не декомпилируем** скомпилированные DLL сторонних модов. Реальные примеры берутся только из **открытого исходного кода** и цитируются с указанием файла. Что именно делает функция — зашито в `.exe`; имена, связи и домены лишь подсказывают смысл, а окончательная проверка — компиляция в Visual Studio и тест в игре.

### Благодарности и источники

Справочник построен на материалах открытых проектов сообщества Kenshi — **огромная благодарность их авторам**. Без реверс-инжиниринга и SDK от **BFrizzleFoShizzle** и вклада **weisspure** этого документа бы не существовало.

Используемые материалы (реконструированные заголовки, примеры кода, зависимости):

- **RE_Kenshi** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/RE_Kenshi> — **GPL-3.0**
- **KenshiLib** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib> — **GPL-3.0**
- **KenshiLib_Examples** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib_Examples> — **GPL-3.0**
- **KenshiLib_Examples_deps** — © BFrizzleFoShizzle — <https://github.com/BFrizzleFoShizzle/KenshiLib_Examples_deps> — включает **Boost 1.60** (Boost Software License 1.0)
- **re_kenshi-working-solution** — © weisspure — <https://github.com/weisspure/re_kenshi-working-solution> — **GPL-3.0**

> Проекты KenshiLib / RE_Kenshi распространяются под **GPLv3**; согласно KenshiLib, производные работы и плагины также должны быть под **GPLv3**. Поэтому этот справочник распространяется на условиях **GPL-3.0** с сохранением атрибуций выше. Все права на исходные материалы принадлежат их авторам.

### Помогите наполнить примерами — поделитесь исходником мода

Самая ценная часть справочника — **реальные примеры из рабочего кода**. Если вы написали работающий мод на RE_Kenshi / KenshiLib, пришлите его **исходный код**:

- 📧 на почту **u1host@proton.me** — архивом (zip) или ссылкой на репозиторий GitHub;
- или любым другим удобным способом.

**Что будет с вашим кодом:**

- Ваш исходный код **не будет опубликован ни в каком виде** — ни целиком, ни в репозитории, нигде.
- Он будет только **обработан локально**, и из него точечно возьмут отдельные строки-примеры вызовов — так же, как уже сделанные подтверждённые примеры (короткий фрагмент + указание, из какого мода он взят).
- Если не хотите даже упоминания названия мода — просто напишите об этом, уберём атрибуцию.

Так справочник наполнится большим числом проверенных примеров и станет полезнее для всего сообщества модостроителей Kenshi. Спасибо! 🖤

### Как пользоваться
>💾 ** В автономном режиме:** загрузите "ReKenshi_KLIB_kinda_swagger.html" и дважды щелкните по нему - интернет не требуется.
Выберите класс слева, раскрывайте домены → поля/методы → строку. Читайте факты, домены значений и примеры; копируйте RVA, сигнатуру, слот vtable и скелет хука.

### Ограничения

- Внутренняя логика функций недоступна (закрытый код игры).
- У ~369 виртуальных методов слот vtable не восстановлен реверсом (`0x0` в заголовках); из них 329 всё равно хукаются через `_NV_`-близнеца по RVA, по-настоящему слот нужен лишь 33 чисто-виртуальным методам без RVA.
- Примеры кода покрывают часть API и пополняются по мере поступления открытых исходников (см. призыв выше).

### Лицензия

**GPL-3.0**, как производная работа от KenshiLib / RE_Kenshi — см. «Благодарности и источники».

*Целевая среда: Kenshi 1.0.65 Steam · KenshiLib · RE_Kenshi. Проект неофициальный, не аффилирован с Lo-Fi Games.*
