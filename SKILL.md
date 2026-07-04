---
name: cinema-prompt
description: Генерирует промпты для динамичного промо-ролика одежды по фото шмотки + описанию бренда. Вход — изображение вещи (куртка, штаны, аксессуар, луки) ± brand-DNA (своя марка / референс-бренды / mood). Скилл сам триангулирует «шмотка × бренд → мир» через brand-archetype matrix (16 архетипов: dark streetwear / techwear / western / goth / couture-avant / sportcore / heritage / pastoral / cyber / biker / hip-hop / bohemian / Y2K / domestic-soft / mountaincore / skater) и подбирает локацию из 9 семейств миров (city-grit · nature-grit · sacred-decay · industrial-isolated · subculture-sport · domestic-intimate · liminal-dreamcore · historic-decay · cultural-specific · climate-extreme). Выход — констелляция из 6 кадров одного мира с готовыми Midjourney + Kling промптами в эстетике «снято, не отрендерено» — НЕ глянцевая каталожная съёмка. Ядро — WOW-доктрина: каждый кадр строится на коллизии двух несовместимых миров, снятой deadpan (как хроника/CCTV/гейм-движок), с эскалацией невозможного от кадра к кадру и тестом пересказа ≤5 слов. Use this skill whenever the user uploads/links a clothing item or full look and asks for promo video ideas, lookbook scenes, brand campaign frames, Kling prompts, MJ prompts, или просит сцены / раскадровку / промо ролик / клип под одежду. Skill is pushy — trigger on ANY garment image with intent to make video content, even if the user не говорит «Kling» или «промпт».
---

# /cinema-prompt — Промпт-генератор fashion-промо (gritty city, not glossy studio)

Скилл превращает **фото одежды** в **констелляцию из 6 кадров одного мира** для динамичного промо-ролика (TikTok/Reels/Shorts/IG-ролик/lookbook-видео). Эстетика — **снято, не отрендерено**: уличный гранж, жёсткий флэш, низкий угол, тело как манекен под шмотку. **НЕ** студийная каталожка, **НЕ** парфюм-реклама, **НЕ** luxury-кампания.

Главная аудитория — US/EU стрит-сцена + русскоязычная fashion-молодёжь. Бренд по умолчанию — ORISS / ERROR SYSTEM (dark avant-streetwear, post-Y2K, HK-dystopia DNA), но скилл универсален под любую стрит-марку.

---

## 🧬 ДНК референсов (выучено наизусть)

Эталонная пятёрка задаёт визуальный закон скилла. Каждый кадр на выходе обязан быть из этой ДНК.

| Реф | Что несёт | Что брать |
|---|---|---|
| **HK low-angle shirtless w/ chain-mesh** | Низкий угол снизу, тело-монумент, бетонный каньон high-rise сзади, прямой флэш, цепи на полу | Vertical-tilt низкий угол, frontal flash, dense urban backdrop, body-as-vessel |
| **HK split shirtless w/ all-over print pants** | Split-композиция, штаны как герой кадра, мокрый асфальт, неон в глубине | Garment-fills-lower-frame, two-pose diptych, wet street, neon depth |
| **FF13 warrior in fur coat + storm** | Грозовое небо, столбы и провода, грязная фактура шерсти, статуарная поза с оружием/предметом | Post-apoc grit, weather as character, prop-as-symbol, low-mid hero shot |
| **Y2K Japan alley w/ fur hood** | Плоский cool daylight, узкий бэк-аллей, кирпич + железная решётка, три фигуры в разных pose-rhythms, candid-doc framing | Overcast cool day, alley geometry, multi-figure non-posed, naturalistic |
| **Paris crew on Haussmann** | Group power-stance, низкое солнце с глубокой тенью, urban architecture, hand-signs, bicycle prop, all-over print denim | Crew shot, low warm sun + deep shadow, hand language, prop in frame |

### Канон раскадровок (12 папок References — миллионы просмотров, из них извлечена WOW-доктрина)

| Реф | Что в кадре | ВАУ-механика (чему учит) |
|---|---|---|
| **Bandit** | Маски целятся В КАМЕРУ через лобовое; распятие из золотых автоматов в соборной нише | Зритель = участник кадра (POV-мишень); sacred × оружие как объект-коллизия |
| **Burnin** | Силуэт волка с цепью на фоне стены огня; волчья стая как night-vision статуи | Зверь — протагонист без человека; стихия = задник для силуэта |
| **Desert** | Кони в прибое в синий час; могила в пустыне с ботинками и голубыми цветами | Икона без человека; memento-mori натюрморт вместо «модель стоит» |
| **Heze** | Женщина в белом на коне сквозь ночной прибой, контровой луч | Один свет + одна фигура + стихия = плакат; religion × hip-hop |
| **Monashki** | Доберман РЫЧИТ В ЛИНЗУ в бабушкиной гостиной с монахиней; пацан в короне и золотых грилзах ржёт в waffle house | Коллизия «домашнее × хищное»; лицо ломает модельную нейтральность (ржач/оскал) |
| **Robot** | Хром-робот в ковбойской шляпе за крэпс-столом среди живых людей | ОДИН невозможный гость в будничной сцене, все ведут себя нормально |
| **Spike3** | Спортбайк припаркован НА барочном кресле в облезлой комнате; пистолет среди ложек | Объект не в своей комнате — deadpan-натюрморт, пересказывается одной фразой |
| **Horse** | Конь в стропах висит под вертолётом над ночным хайвеем | Невозможный масштаб, снятый как новостная хроника |
| **Knight** (видео) | 90% кадра — чистый чёрный; один луч; лицо/рука едва выступают из тьмы; вуайер-кадр через окно | Радикальная недосказанность: один читаемый элемент на кадр, тьма = роскошь |
| **Coridor** (видео) | POV-проход по обшарпанным японским коридорам; толпа молча смотрит вниз в пролёт | Found-footage POV-волкинг; жуть нарастает по кадрам (эскалация) |
| **ps2 Skull** | Фейковая PS2-игра: скелет-водитель от первого лица, ядерный гриб, водонапорка-паук, каменный колосс | «Игра, которой не существует»: low-poly движок = deadpan-медиум; эскалация нормально→странно→невозможно |
| **ps2 AltGirl** | Шмотка (кожанка, лоу-райз, чокер) на PS2-персонаже на станции московского метро | ГАРДЕРОБ через фейк-игру: вещь читается, мир невозможен — прямой fashion-регистр |
| **SURREAL** (12 кадров, сюрреал-регистр) | Порше в советской хрущёвке с тремя собаками; RAM пробивает потолок над кроватью, модель не реагирует; стелс-бомбер с граффити «NEED MONEY FOR PAGANI»; огненный дракон за самураем; god-колосс со светящимися глазами в тумане; профиль-двойная-экспозиция с неон-городом внутри; девушка бежит по светящемуся полю цветов; 3 световых меча сквозь тело (Таро) | 6 новых приёмов: (a) double-exposure/композитинг как медиум; (b) god-scale силуэт в тумане + человек как scale-маркер; (c) стихия принимает форму мифо-зверя (огонь=дракон); (d) gravity-defying вторжение объекта + frozen debris + НЕреагирующий герой; (e) рукописный culture-scrawl на объекте (не логотип!); (f) glow-природа/celestial event (комета, биолюм-поле) |

**Сквозные гены, обязательные в каждом кадре:**
1. **Шмотка читается** — силуэт, текстура, deco прописаны словами в промпте.
2. **Город, не студия** — реальная локация (alley / boulevard / rooftop / underpass / wet street / market), не белый seamless.
3. **Один практический источник света** — флэш / натрий / неон / луна / гроза. Никогда «soft studio key».
4. **Низкий или дикий угол** — fisheye / wide / низкий tilt-up. Eye-level 50mm = ноль присутствия.
5. **Тело как ремень доставки шмотки** — модель не позирует красиво, а **занимает агрессивное пространство** (lean, lunge, hard stance, mid-step, hand thrust).

---

## ⚡ ЗАКОН 0 — Captured, not rendered (ГЛАВНЫЙ, перекрывает всё)

Эта догма унаследована из крим-версии скилла и работает на fashion ещё сильнее: глянцевый каталог = смерть. Все референсы выглядят как **снятое реальной камерой**, а не как AI-CGI.

Эталоны выглядят как:
- **Прямая фотовспышка на компакт** (жёсткий плоский флэш, ободранный фон, бытовуха) — HK chain, HK split, fashion-снэп
- **Плёнка 35мм на улице** (зерно, halation, выцветший цвет) — Paris, Y2K Japan
- **Кадр из видеоигры PS3-эры / FMV** (диффузный гроз-свет, грязный grade) — FF
- **Документальный candid** (плоский cool day, кривое кадрирование) — Y2K Japan

У них **грязь, зерно, пот, мокрый асфальт, бетон, ржавчина, жёсткая вспышка, несовершенный фокус.** Это выглядит как **слитый бэкстейдж со съёмки или украденный кадр**, а не как «AI-fashion lookbook».

### ❌ Антипаттерны — категорически запрещены
| Что НЕ делать | Почему |
|---|---|
| Чистый seamless backdrop / студия | Каталог = скролл |
| `cinematic, luxury, pristine, immaculate, 8k, hyperdetailed, octane, polished, glossy, masterpiece` | Глянцевый AI-CGI = смерть |
| `editorial, vogue, glamour, beauty light, soft key` | Reads as perfume ad |
| Soft beauty-light на лицо / equal fill | Убивает грит |
| Идеальная симметричная композиция | Каталог-постер |
| Чистая модель «красиво стоит», eye-contact, лёгкая улыбка | Стоковая модель = провал |
| Симметричный full-figure eye-level | Манекен в витрине |
| Розовый/коричневый soft grade, instagram-aesthetic, teal-grade | Tourist-tier |

### ✅ Слова-друзья (тяни в каждый промпт)
`harsh on-camera flash, expired 35mm film, halation, faded washed-out color, grain, motion blur, imperfect focus, candid documentary, wet asphalt, concrete texture, neon spill, found footage, low-angle wide, fisheye distortion, snapshot, bodycam POV`.

### Правило Закона 0
Перед выдачей каждого кадра: **«Это выглядит как реальный уличный фотоснэп / бэкстейдж / FMV-still — или как глянцевый AI-рендер?»** Если второе — переписать с capture-формат + грязь + жёсткий свет.

---

## 💥 ЗАКОН WOW — формализация эмоции «я такого не видел» (равен Закону 0 по силе)

Целевая эмоция зрителя: **«ВАУ, я до этого такого не видел — лайк»**. Она не берётся из «красивой локации + крутой модели + дождя + неона» — это уже само по себе AI-клише, которое лента видела тысячу раз. ВАУ раскладывается на 10 правил. Нарушение любого из первых пяти = банальный кадр, переписать.

### W1 — Правило пересказа (≤5 слов) — ГЛАВНЫЙ ФИЛЬТР
Каждый кадр должен пересказываться чужому человеку одной фразой до 5 слов, и фраза должна вызывать «ЧТО?!»: «конь висит под вертолётом», «мотоцикл припаркован на кресле», «распятие из золотых автоматов», «скелет ведёт машину». Если пересказ звучит как описание фотосессии («модель в куртке идёт под дождём в неоне») — кадра нет. Пересказ-фраза выводится пользователю как заголовок кадра.

### W2 — Правило коллизии
Носитель ВАУ — **столкновение двух миров, которые в реальности не встречаются**: мотоцикл × бабушкина гостиная, робот × казино, доберманы × монахиня, кутюр × советский подъезд. Локация, погода и «вайб» сами по себе ВАУ не дают — они лишь сцена для коллизии. Самые мощные пары (из канона):
- **sacred × street** (распятие-автоматы, монахиня, храм × техвир)
- **домашнее × хищное** (доберман в гостиной, волк на кухне)
- **детское/наивное × криминальное** (пацан в короне с грилзами, милый маскот в аду)
- **музейное/антикварное × утилитарное** (спортбайк на барочном кресле)
- **масштабно-невозможное × будничная документация** (конь под вертолётом как новостной кадр)

### W3 — Правило deadpan (камера И герой не реагируют)
Невозможное снимается так, будто это обычная хроника: CCTV, гейм-движок, home video, news footage, phone snap. **Камера не удивляется — удивляется зритель.** Никаких «эпичных» ракурсов вокруг чуда, никакого подчёркивания. Робот за крэпс-столом снят так же скучно, как остальные игроки.

**Герой тоже не реагирует (ген SURREAL):** пикап пробивает потолок над кроватью — модель лениво лежит в очках; за спиной стена огня в форме дракона — самурай спокойно идёт; Порше в бабушкиной квартире — собаки просто лежат. **Non-reaction — сильнейший множитель ВАУ:** будничная реакция на невозможное говорит зрителю «в этом мире так нормально», и это страшнее/круче любого экшена. Прописывать явно: `does not react, calm, bored expression, treats it as ordinary`. Deadpan — то, что отличает «фильм-вселенную» от «AI-фэнтези-каши».

### W4 — Правило соучастия зрителя
Минимум 1 кадр из 6 делает зрителя участником сцены, а не наблюдателем: POV-руки на руле/в кадре, оружие/зверь/взгляд направлены прямо В линзу, субъект вторгается в личное пространство камеры (пасть добермана в 10 см от объектива). Это кадр, который физически дёргает при скролле.

### W5 — Правило эскалации
6 кадров = лестница «нормально → странно → невозможно». Кадр 1 цепляет динамикой и намёком, но **самая мощная невозможность стоит на позиции 3–5**, не в начале — зритель должен досмотреть и получить удар, когда уже вовлечён (ps2 Skull: сигарета → скелет → ядерный гриб → колосс). Кадр 6 — послевкусие, не пик.

### W5b — Правило динамики интенсивности (ант-«всё на максимуме»)
Боевой провал, вылезший дважды (склеп-версия и панельки-версия): скилл делает ВСЕ 6 кадров на максимальной громкости — герой орёт/скалится/бросается в линзу в каждом, и один тип клоуз-апа съедает роспись. Плоский максимум = ноль эскалации: зрителю нечему нарастать, всё бьёт одинаково, и парадоксально тише, чем один точный крик среди тишины. Квоты:
- **≥2 из 6 кадров — тихие/deadpan-биты** (non-reaction, неподвижность, спокойный взгляд мимо линзы, пустой мир). Тишина продаёт следующий крик.
- **≤2 кадра одного типа крупности+эмоции.** Три «оскал-в-фишай» подряд = брак, оставить один сильнейший, остальные пересобрать в другие роли.
- **Пик громкости — ОДИН, на позиции 3–5** (совпадает с пиком невозможного W5). Не размазывать крик по всей россыпи.
- Особый случай: если найдена сильная deadpan-коллизия (герой не реагирует на невозможное) — она обычно и есть COLLISION ICON; не переделывай её в крик, крик убивает non-reaction (W3).

### W6 — Правило одного нового элемента
ВАУ = **одна невозможность на кадр**, документированная бытовыми деталями (пыль, провода, мусор, прохожие). Две+ невозможности = фэнтези-каша, ноль = каталог. Остальное в кадре — максимально обычное: обычность продаёт невозможность.

### W7 — Правило иконы (thumbnail test)
Минимум 2 кадра из 6 работают как стоп-кадр-обложка: один читаемый силуэт/объект, композиция держится на паузе, кадр хочется заскринить. Это кадры, которые расходятся отдельно от ролика.

### W8 — Правило смелой темноты
Разрешено (и поощряется) 90% чистого чёрного кадра с одним лучом и одним читаемым элементом (канон Knight). Недосказанность сильнее освещённости. Не бояться терять деталь — бояться показать всё.

### W9 — Правило сломанного лица
Если лицо в кадре — оно НЕ позирует: рычит, ржёт в голос, орёт, застыло в жути, смотрит как зверь. Модельная нейтральность и «смелый взгляд в камеру из лукбука» запрещены. Эмоция на лице должна быть неприлично сильной для fashion-съёмки.

### W10 — Правило свежего клише
Перед выдачей спроси себя: **«Я уже видел этот кадр в AI-лентах?»** Запрещённые от частого повторения AI-клише: модель идёт сквозь неоновый дождь; худи-силуэт на фоне заката; голуби взлетают в slow-mo; капюшон + смог + небоскрёбы; волк просто стоит рядом с героем; змея/питон на плече dark-модели (дежурный реквизит гот-съёмок); модель сидит/позирует в склепе при свечах. Если кадр совпадает с клише — заменить коллизию или медиум (например, переснять то же в PS2-движке или в radical-noir тьме). Тотем-животное спасает от клише только ФУНКЦИЯ: питон, лежащий на плече = клише; питон, бросающийся в линзу из мехового воротника = кадр.

### Как коллизия работает НА шмотку (два режима, оба в каждой констелляции)
- **Mode A — «Шмотка нормальная, мир сошёл с ума»**: вещь = точка опоры зрителя, единственное «нормальное» в кадре невозможного (герой в куртке спокойно стоит, пока за спиной колосс/потоп/пожар). Даёт максимальную читаемость вещи.
- **Mode B — «Шмотка = невозможный гость»**: мир подчёркнуто будничный (waffle house, бабушкина гостиная, советский подъезд, ночной супермаркет), а одетый герой в нём — коллизия. Обычный мир делает шмотку ГРОМЧЕ, чем любой спецэффект.
- Квота: минимум 2 кадра Mode B в каждой констелляции. Полная россыпь в Mode A = фэнтези-клип, где шмотка тонет.

---

## 🎯 Единица генерации — констелляция, не нарратив

Скилл выдаёт **не сцены сюжетного ролика**, а **6 разных кадров одного визуального мира**, объединённых:
- **Шмоткой** (vehicle of the campaign — сквозной герой кадров, см. Lock ниже)
- **Миром/локацией** (HK rooftops / Paris alley / Tokyo arcade / post-apoc highway)
- **Style anchor** (capture-формат + grade, дословно копируется во все 6)
- **Героем(ями)** — character lock (см. L4)

Зритель должен видеть в 6 кадрах **один фильм-вселенную**, в каждом — новый удар. **НЕ 6 ракурсов одного манекена в позе.**

---

## 👕 ШМОТКА-ЛОК — что делать с фото на входе (КРИТИЧНО)

Когда пользователь даёт фото вещи, ты ОБЯЗАН:

### Шаг 1. Визуально разобрать вещь
Запиши в виде блока `GARMENT DNA`:
- **Тип:** (puffer / chain-mesh top / wide-leg cargo / all-over print denim / fur-hood parka / mesh-tank / patch-denim wide pants ...)
- **Силуэт:** (oversized / cropped / floor-sweeping / wide-leg / boxy / fitted-to-chest)
- **Цвет/материал:** (matte black knit / iridescent vinyl / washed indigo / weathered black with grey patches / chain-link metal)
- **Deco / уникальные маркеры:** (woven evil-eye pattern всё-over / silver hardware на поясе / D-rings / quilted diamond / shredded hem / cross-stitch патч-работа / иероглифы / каллиграфия)
- **Visual hook:** одна фраза-формула, ради которой шмотку запомнят (`chain-mesh skirt-tail dragging on wet concrete` / `pant-leg pooling around boot` / `evil-eye print covering full leg`).

### Шаг 2. Прописать garment в каждом промпте дословно
Все 6 кадров должны содержать **идентичную короткую формулу шмотки** в первой трети промпта. Это и есть garment-lock: модель MJ не помнит вещь между генерациями — поэтому форма повторяется слово-в-слово.

```
GARMENT LOCK (copy verbatim into every shot):
> "<тип> with <силуэт + deco>, <цвет/материал>, <visual hook>"
> e.g. "chain-mesh knitted tunic with floor-sweeping skirt, matte iron-black, hand-knotted texture dragging on wet concrete"
```

### Шаг 3. Лок через текст + ручную сборку
**В тело MJ-промпта НИКОГДА не подставлять `--cref`, `--sref`, `--cw`** — пользователь сам подкрепит референсы в интерфейсе Midjourney через drag-and-drop. Скилл выдаёт ТОЛЬКО текстовый промпт + базовые параметры (`--ar 4:3 --style raw --s 50 --v 8.1`).

Лок шмотки и героя держится через:
- дословную GARMENT LOCK формулу в каждом кадре (см. ниже)
- 3 идентичных character-маркера в каждом кадре с героем (L4)
- идентичный Style anchor (L3)

### Шаг 4. Минимум 4 из 6 кадров — шмотка ПОЛНОЦЕННО видна
- Кадр-портрет крупно (где шмотки нет в кадре) — максимум 1.
- Atmospheric тотал-силуэт где фактура не читается — максимум 1.
- Остальные 4+ — **garment dominates lower 2/3 frame** или **garment frames the subject**.

---

## 🌍 СЛОЙ 0 — Мир, который ВЫНОСИТ шмотку

Не «концепция». Не «настроение». **Мир.** Мир = локация + социальная плотность + время суток + погода + один практический источник света. Этот мир должен **усиливать** шмотку, а не конкурировать с ней.

### Принцип: shape × world
| Силуэт шмотки | Идёт с миром |
|---|---|
| **Floor-sweeping / wide-leg / oversized** | HK rooftop wet concrete · Tokyo neon alley · underpass с лужами · grimy parking deck · ruined cathedral nave · salt flats — нужен пол + перспектива для silhouette |
| **Chain/metal/heavy hardware** | Бетонные high-rise каньоны · кирпичные fire-escape лестницы · ржавая warehouse · scrapyard · oil rig · ship graveyard — твёрдые поверхности |
| **All-over print / loud deco** | Paris Haussmann · Tokyo arcade · plaza на закате · marble metro · empty palace ballroom · опера в распаде — нужен «нейтральный богатый фон» чтобы принт читался |
| **Y2K puffer / fur / techwear** | Холодный cool day · бэк-аллея · sub-zero parking · gas station ночью · alpine ski lift · frozen lake · ice cave — нужна температура и сырость |
| **Mesh / cropped / тело наружу** | Низкий угол под high-rise · rooftop при флэше · neon-lit залив · boxing gym · jungle clearing после ливня — нужна вертикаль + флэш |
| **Patch / DIY / distressed** | Vacant lot · skate park · railway tracks · трэшовые back yards · abandoned waterpark · scrapyard · trailer park — нужна культура потёртости |
| **Leather / biker / utility** | Desert highway shoulder · biker bar parking · MX dirt pit · oil-stained garage · Mojave gas station — нужна жара, грязь, мотоиконика |
| **Silk / drape / flowing / sheer** | Black-sand beach · empty marble palace · abandoned pool · misty pine forest · mountain treeline at dawn · ruined chapel — нужна ткань-в-ветре, негатив-простор |
| **Tactical / cargo / military / techwear-utility** | Concrete bunker · abandoned factory floor · quarry · radar station · soviet sanatorium · helipad on rooftop — нужна функциональная геометрия |
| **Western / fringe / suede / hat** | Big-sky plains · Texas honky-tonk · gravel rodeo lot · dirt road с telephone poles · cornfield at dusk · highway diner — нужна horizon + dust |
| **Knit / cosy / earth-tone / heritage** | Misty pine forest · rocky atlantic coast · fishing village dock · stone cottage interior · sheep pasture at golden hour — нужна natural fibre context |
| **Couture-avant / sculptural / architectural** | Brutalist civic plaza · empty opera foyer · ruined Roman bath · industrial wind tunnel · salt flats · obsidian volcanic field — нужен monumental space |
| **Streetwear-clean / sportcore / mall-core** | Empty mall after-hours · 24h laundromat · arcade · bowling alley · public pool deck · highway truck stop — нужна Americana-liminal |
| **Goth / occult / heavy black** | Catacombs · cemetery at dusk · ruined monastery · candle-lit chapel decay · stormy moor · black lake at full moon — нужна sacred-decay |
| **Beach / swim / minimal** | Black-sand volcanic beach · tropical storm coast · cliff-side rocks · ruined coastal hotel · jellyfish-lit night surf — НЕ stock-beach, всегда грит-coast |
| **Ethnic-fusion / global-craft / kaftan** | Moroccan medina alley · Mongolian steppe yurt · Vietnamese rice paddy at dawn · Lagos market · Cuzco stone street — нужна real cultural texture, не «travel ad» |

### Меню миров — РАСШИРЕННОЕ (если пользователь не задал — выбирать через brand-matrix ниже)

Все имеют **реальную фактуру + sub-cultural читаемость + grit**. Сгруппировано по семействам — внутри каждого 5–10 конкретных локаций. **НЕ использовать стоково** — каждая локация снимается грязно, с практическим светом, low-angle.

#### 🏙️ CITY-GRIT (дефолт под dark streetwear / ORISS / Y2K / hip-hop)
- **HK dystopia** — Choi Hung / Mong Kok каньоны, мокрый бетон, неон на кантонском, low-angle на high-rise · дефолт под ORISS/ERROR SYSTEM
- **Tokyo back-alley / Shibuya night** — izakaya проулки, vending machines, fluo на красном кирпиче, дождь
- **Paris streetwear crew** — Haussmann фасады, late afternoon long shadow, кафе-террасы, метро Père Lachaise grit
- **NYC subway / Brooklyn rooftop** — graffiti tunnels, J/M/Z elevated tracks, rooftop под молнией
- **Berlin techno / industrial** — бетонные U-Bahn платформы, Spree quays, S-Bahn под дождём, kebab counters
- **Seoul backstreet** — neon kanji vertical signs, wet ground, cigarette smoke, basement noraebang
- **São Paulo / Rio favela edge** — concrete stairs, motorbike on cobblestone, kite-strung sky
- **LA Eastside / Boyle Heights** — palm tree shadow, blue-tile diner, motel parking, neon liquor sign
- **Y2K Japan low-fi suburb** — concrete stairs, vending corridor, train crossing, residential brick (флэш + cool day)

#### 🌲 NATURE-GRIT (НЕ инстаграм-пейзаж — всегда weather + grit + одинокая фигура)
- **Misty pine forest** — moss, fallen trunks, fog crawling through trees, single shaft of cold light
- **Mountain treeline at dawn** — alpine wind, exposed rock, low cloud rolling, lone figure on ridge
- **Stormy moor / Scottish highland** — wet heather, no trees, sideways rain, dramatic flat overcast
- **Black-sand volcanic beach** (Iceland / Bali Lovina) — обsidian sand, white surf, lone basalt stack, storm light
- **Tropical storm coast** — palm trees in horizontal wind, sideways rain, sodium streetlamp на pier
- **Rocky atlantic coast** — cliffs, gulls, fishing nets, salt spray, lighthouse silhouette
- **Cornfield at dusk** (Midwest) — backlit stalks, low warm sun, telephone wires, gravel road
- **Mojave / Joshua Tree** — yucca silhouettes, lavender dusk, lone gas station, dust devils
- **Salt flats / desert playa** — endless white, cracked surface, single figure, blown-out sky
- **Jungle clearing after rain** — wet leaves, mist, root system, exposed mud, dappled cold light
- **Mongolian steppe** — yurt, livestock, big sky, dust, horseman silhouette
- **Frozen lake / glacier** — cracked ice, blue-black water below, lone figure, breath visible
- **Mangrove / swamp** — knee-deep water, knee roots, dragonflies, single fishing boat, hot diffuse haze

#### 🛐 SACRED-DECAY (для goth / dark avant / occult / heritage)
- **Ruined chapel / abandoned monastery** — broken stained glass, candle pools, pigeon shit, stone arches
- **Catacombs / ossuary** — bones-as-architecture, single candle, narrow stone corridor
- **Cemetery at dusk** — wrought iron, ivy, broken angel statues, ground fog
- **Ruined Roman bath** — empty pool, marble cracked, vines, single shaft of light through hole in roof
- **Empty Orthodox church** (Балканы / Грузия) — frescoes peeling, incense smoke, single old woman in black far back
- **Cyber-monk temple** — torn paper sutras, candle pools, stone wall, smoke
- **Witch's hut interior** — herbs hanging, fire glow, animal skulls, kerosene lamp

#### 🏭 INDUSTRIAL-ISOLATED (для tactical / techwear / heavy hardware / military)
- **Concrete bunker** — fluorescent strip, water on floor, single pipe drip, echo
- **Abandoned factory floor** — rust beams, shafts of light through broken roof, machinery skeletons
- **Quarry** — terraced rock, yellow excavator, dust haze, vertigo wide
- **Scrapyard / car graveyard** — stacked crushed cars, golden hour rust, dog barking somewhere
- **Oil rig / offshore platform** — orange paint, ocean fog, helipad, single worker in coverall
- **Soviet sanatorium / abandoned spa** — peeling pastel walls, empty pool tiles, broken chandelier
- **Radar station / abandoned military** — dish, barbed wire, concrete bunker, salt wind
- **Power plant cooling tower** — concrete giant, fog inside, vertigo up

#### 🥊 SUBCULTURE-SPORT (для leather / utility / patch / athletic)
- **Boxing gym** (Brooklyn / Havana) — sweat-stained ring, single bulb, peeling posters, tape-wrapped hands
- **Motocross dirt pit** — dust haze, RV in background, helmet on tire, fans on chain-link
- **BMX dirt jump** — wooden ramps, summer dust, kid silhouette mid-air
- **Skate park concrete bowl** — graffiti, busted board, sodium light, kid pushing
- **Equestrian stable / horse barn** — hay, leather tack, single bulb, breath in cold air
- **Motorcycle garage** — chrome parts on workbench, oil-stained concrete, single bike up on lift
- **Lowrider meet** — chrome hydraulics, gold-flake paint, fenced-off parking lot at golden hour
- **Drag strip / illegal street race** — heat shimmer, tire smoke, headlights at vanishing point
- **Underground rave / warehouse party** — laser, fog, strobe, sweat, crushed cans

#### 🛏️ DOMESTIC-INTIMATE (для cropped / silk / sleepwear / soft-grunge)
- **Cheap motel room at 3am** — sodium street light through curtains, tube TV glow, unmade bed
- **Bathroom tile / shower stall** — fluorescent overhead, condensation, single bulb, tile reflection
- **Kitchen at dawn** — kettle steam, single window light, cigarette in ashtray, peeling lino
- **Bedroom with curtains blowing** — single bedside lamp, white curtain in night wind
- **Empty hotel corridor** — endless carpet pattern, fluorescent flicker, one open door spilling light
- **Suburban garage** — single bare bulb, beer fridge, dartboard, motorcycle covered with tarp
- **Diner booth 2am** — fluorescent, formica, single coffee, neon spilling through window

#### 🎢 LIMINAL / DREAMCORE (для clean / minimal / sportcore / Y2K-revival)
- **Abandoned waterpark** — drained slides, kid-toy bright colors faded, weeds through tiles
- **Empty mall after-hours** — escalator off, single security light, fountain dry, mannequins
- **24h laundromat** — fluorescent, single washer spinning, plastic chairs, beige tile
- **Bowling alley** — neon scoreboard, ball returns clinking, brown carpet, beer signs
- **Public pool deck (off-season)** — drained pool, fall leaves on tiles, single lifeguard chair
- **Highway truck stop / gas station** (3am) — fluorescent canopy, single semi truck, moths on lights
- **Arcade after-hours** — single CRT glow, cigarette haze, sticky carpet, faded poster
- **Abandoned shopping plaza** — empty parking lot, vacant store signs, weeds через bins

#### 🏛️ HISTORIC-DECAY / COUTURE-SETTING (для silk / drape / sculptural / avant)
- **Empty palace ballroom** — chandelier with broken crystals, parquet warped, dust motes
- **Ruined opera foyer** — marble staircase, peeling murals, single chandelier on floor
- **Brutalist civic plaza** — Béton brut, concrete benches, single figure, raking light
- **Decommissioned theatre** — red velvet seats faded, stage dark, single bulb upstage
- **Stately decay (Versailles-tier in ruin)** — gilt mirror cracked, parquet flooded, weeds через окно
- **Old library / archive** — dust on books, single green lamp, leather chair, brass

#### 🌍 CULTURAL-SPECIFIC (для ethnic-fusion / craft-heritage / global)
- **Moroccan medina** — narrow blue alley, brass lanterns, single tagine smoke
- **Tokyo onsen town** — wooden buildings, lantern light on wet stone, sake bottles
- **Hong Kong fishing village** (Tai O) — stilt houses, dried fish on lines, sampan, low tide mud
- **Mexico City rooftop** — water tanks, telenovela aerial, golden hour pollution
- **Cuban Havana street** — peeling pastel walls, 1950s car, laundry overhead, single old man
- **Vietnamese rice paddy at dawn** — conical hats, water buffalo, mist on water
- **Indian palace courtyard in decay** — marble, jaali screens, monkeys, single saffron robe
- **Lagos market** — fabric stalls, motorbike taxi, plastic crates, harmattan dust
- **Tbilisi old quarter** — wooden balconies, peeling paint, stray dogs, wine pour

#### ❄️ CLIMATE-EXTREME (для technical / outerwear / utility)
- **Alpine ski lift fog** — gondola swinging in white-out, frost on cable
- **Frozen quarry** — ice cracked, blue-black water below, single figure
- **Sub-zero gas station** — frost on pumps, breath visible, single bulb halo
- **Sandstorm desert** — visibility 5 meters, headlights, lone tower
- **Volcanic crater rim** — sulfur steam, basalt, lone figure против wind
- **Equatorial monsoon** — sideways rain on banana leaves, mud road, conical hat

### Анти-меню (НЕ использовать)
- Студия / seamless / cyclorama / cyc / soft beauty key
- Чистый «Beach sunset» / «desert dunes with no detail» / «mountain peak» как открытка — туристский постер. (Можно делать desert/beach/mountain ТОЛЬКО с грязью, погодой, фигурой, low-angle — см. NATURE-GRIT.)
- Luxury-ad: Dubai marina · yacht · sports car interior · penthouse infinity pool · champagne magnum
- Instagram aesthetic: cherry blossom path · lavender field · pastel cafe · pink desert · «aesthetic» café latte art
- Generic fantasy: эльфы · киберпанк-город из стока · cosplay-зал · zombie apocalypse костюм

---

## 🎭 BRAND ARCHETYPE — автоопределение мира (КРИТИЧНО)

Если пользователь даёт описание бренда / референсы / соц-сеть / тэглайн — **сначала декодируй brand archetype**, потом подбирай мир. Это важнее, чем silhouette: один и тот же oversized puffer в брендах Patagonia и Vetements живёт в разных мирах.

### Шаг: BRAND DNA decoder
Если пользователь упоминает бренд (свой или референс), запиши:
- **Tribe:** (dark streetwear · technical-outdoor · clean minimal · western-americana · couture-avant · sportcore · goth-occult · heritage-craft · global-fusion · y2k-revival · cyber-dystopia · bohemian · biker-punk)
- **Decade DNA:** (Y2K 99–04 · early-10s Tumblr · late-10s techwear · 70s biker · 90s grunge · 80s power · timeless folk)
- **Reference brands:** (с чем визуально рифмуется — Rick Owens · Vetements · A-COLD-WALL · Vaquera · Eckhaus Latta · Maison Margiela · Yohji · Acne · Heliot Emil · Diesel · Bode · Jacquemus · Carhartt WIP · Patagonia · Stüssy · Supreme · Telfar · Mowalola · Bianca Saunders · Marine Serre · Iris van Herpen)
- **Mood word:** одна одна фраза (например `«хтонический ритуал»` / `«урбан-выживание»` / `«гранж-нежность»` / `«фарм-делирий»`)

### Brand archetype → world matrix (дефолтный матч)

| Brand archetype | Reference brands | Primary worlds (top 3) | Fallback worlds |
|---|---|---|---|
| **Dark streetwear / dystopia** | Rick Owens, A-COLD-WALL, Heliot Emil, ERROR SYSTEM, ORISS, Diesel new-era | HK dystopia · Tokyo back-alley · industrial-bunker | rooftop storm · brutalist plaza |
| **Y2K revival / techno-frutiger** | Heaven by Marc Jacobs, Vaquera, Diesel, KNWLS, MISBHV | Y2K Japan suburb · abandoned mall · arcade after-hours · bowling alley | gas station 3am · Tokyo neon |
| **Technical outdoor / mountaincore** | Arc'teryx, Patagonia, Salomon, Klättermusen, Snow Peak | Mountain treeline · alpine ski lift · frozen lake · volcanic crater | misty pine forest · stormy moor |
| **Western / Americana** | RRL, Bode (western), Stetson, Junya x Levi's, Levi's vintage | Cornfield at dusk · big-sky plains · Mojave · honky-tonk parking · highway diner | lowrider meet · scrapyard |
| **Goth / occult / dark avant** | Rick Owens, Ann Demeulemeester, Comme des Garçons noir, Yohji black, Boris Bidjan Saberi | Ruined chapel · catacombs · cemetery dusk · stormy moor | empty Orthodox church · witch hut |
| **Couture-avant / sculptural** | Iris van Herpen, Maison Margiela artisanal, Schiaparelli, Vaquera, Mugler | Empty palace ballroom · ruined opera foyer · salt flats · brutalist plaza · volcanic field | abandoned spa · decommissioned theatre |
| **Tactical / techwear / military** | ACRONYM, Stone Island Shadow Project, Veilance, Errolson, GUERRILLA-GROUP | Concrete bunker · radar station · oil rig · quarry · soviet sanatorium | rooftop helipad · power plant |
| **Heritage-craft / earth-tone / quiet luxury** | Lemaire, The Row, Auralee, Toogood, Margaret Howell, Studio Nicholson | Rocky atlantic coast · fishing village dock · misty pine forest · stone cottage · sheep pasture | empty library · old archive |
| **Sportcore / clean / mall-core** | Telfar, Martine Rose (sport), adidas SPZL, Nike ACG, Stüssy clean | Public pool deck · 24h laundromat · empty mall · bowling alley · highway truck stop | arcade · diner booth |
| **Biker / leather / punk** | Schott NYC, Enfants Riches Déprimés, Junya Watanabe MAN biker, 99%IS | Biker bar parking · motorcycle garage · desert highway · drag strip · scrapyard | underground rave · trailer park |
| **Hip-hop / streetwear-crew** | Supreme, BAPE, ANTI SOCIAL SOCIAL CLUB, Corteiz, Stüssy, Aimé Leon Dore | NYC subway · Brooklyn rooftop · Paris crew · LA Eastside · São Paulo edge | basketball court · arcade |
| **Bohemian / kaftan / global-craft** | Marine Serre, Bode, Story mfg, Chloé, Ulla Johnson | Moroccan medina · Mongolian steppe · Vietnamese rice paddy · Cuban Havana · Indian palace decay | Lagos market · Tbilisi old town |
| **Domestic-soft / intimate / nightwear-as-day** | Eckhaus Latta, Vaquera, Sandy Liang, Cecilie Bahnsen, Simone Rocha | Motel room 3am · kitchen at dawn · bedroom curtains · bathroom tile · hotel corridor | suburban garage · diner booth |
| **Cyber-dystopia / sci-fi futurism** | Mugler, Balenciaga (Demna era), Diesel, Coperni, AVAVAV | Underground parking · helipad rooftop · neon HK · radar station · power plant | airport at night · abandoned subway |
| **Skater / DIY-distressed / patch-grunge** | Cactus Plant Flea Market, ERL, Online Ceramics, Brain Dead, Section 8 | Skate park · vacant lot · trailer park · abandoned waterpark · railway tracks | suburban garage · backyard |
| **Pastoral / folk / heritage-revival** | Bode, Story mfg, Toogood, Margaret Howell, Cawley | Sheep pasture · misty pine forest · fishing village · stone cottage · cornfield dawn | stable barn · old library |

### Правило triangulation (КАК ВЫБИРАТЬ)
Когда есть фото шмотки + описание бренда:
1. **Brand archetype matrix** даёт 3 primary мира.
2. **Shape × world таблица** даёт 3 мира под силуэт.
3. **Пересечение** = твой выбор. Если пересечения нет — приоритет у brand archetype (потому что мир должен сказать «это [бренд]», а не «это [одежда вообще]»).
4. Если 2–3 кандидата примерно равны — выдай пользователю буквами, дай выбрать:
   ```
   А — <мир 1, одна строка обоснования>
   Б — <мир 2, одна строка обоснования>
   В — <мир 3, одна строка обоснования>
   ```

### Когда brand НЕ задан
- Если у вещи **сильный visual hook** (chain-mesh / all-over print / fur / cargo) → выбирай по shape × world матрице, выдай 2–3 варианта на выбор.
- Если вещь **нейтральная** (basic tee / plain pants / hoodie) → СПРОСИ мир/бренд/настроение. Без контекста выйдет generic.
- **Дефолт-дефолт под безымянного русскоязычного юзера**: city-grit (HK / Tokyo / Paris), потому что это база скилла. Но всегда лучше спросить.

---

## Слой 1 — От шмотки к идее (процесс)

1. **GARMENT DNA** — разбери фото (см. блок выше).
2. **BRAND DNA** — если бренд/референс упомянут, декодируй (см. brand decoder). Если нет — спроси или возьми city-grit дефолт.
3. **Match world** — triangulation через brand archetype matrix + shape × world таблицу. Выдай 2–3 кандидата на выбор, если нет очевидного.
4. **Choose one world** — отбери тот, который сильнее всего рифмуется и с brand, и с visual hook вещи.
4.5. **CORE COLLISION** — внутри выбранного мира сформулируй коллизию по W2 (что с чем сталкивается) и выбери Mode-баланс (какие кадры A, какие B). Если предлагаешь пользователю миры на выбор буквами — к каждому миру сразу прилагай его коллизию одной фразой: выбирают не локацию, а идею.
5. **Develop 6 shots constellation** — внутри коллизии сгенерируй 10+ потенциальных кадров (HOOK + пул ролей + AFTERMATH), отбери 6 сильнейших через восемь тестов, разложи по лестнице эскалации.

---

## Слой 2 — Восемь тестов на каждый кадр

Каждый кадр проходит **все восемь.** Не прошёл один — переписать или выкинуть.

### Тест 1 — Шмотка читается?
Видно силуэт + хотя бы одну фактурную деталь вещи? Если кадр можно опубликовать БЕЗ этой шмотки и ничего не изменится — провал. Шмотка должна быть **поводом для кадра**.

### Тест 2 — Не каталог?
«Модель стоит на белом фоне, eye-level, smiling, holding pose» — провал. Должно читаться как **бэкстейдж со съёмки** или **украденный фотоснэп** (Закон 0).

### Тест 3 — Город, не студия?
«Где это снято?» — должен быть конкретный реальный ответ (rooftop в Mong Kok / переход Shibuya / Paris Pere Lachaise alley). Ответ «не знаю, какая-то локация» = провал.

### Тест 4 — Низкий угол ИЛИ дикая оптика ИЛИ осознанный deadpan?
Eye-level 50mm + frontal = заставка стока. Минимум один из: **низкий tilt-up / fisheye / wide-angle distortion / extreme close-up / overhead / split / dutch / handheld lurch.** Исключение (W3): в кадрах COLLISION ICON и WORLD DEADPAN нарочито «скучный» хроникальный eye-level — легален и желателен, ЕСЛИ в кадре есть невозможность, которую он документирует. Стандартный угол без невозможности в кадре — провал.

### Тест 5 — Есть peak millisecond?
Не «модель стоит», а «модель MID-STEP, fabric whipping, head snapping, hand thrusting в линзу». Хотя бы один глагол на главного субъекта (см. L12). Нет глагола — переписать.

### Тест 6 — Один практический источник?
В промпте указан КОНКРЕТНЫЙ источник: `harsh on-camera flash` / `single sodium streetlamp from frame-right` / `neon kanji sign spilling magenta on wet ground` / `headlights of oncoming car`. Описание «moody lighting» — провал.

### Тест 7 — Captured?
Указан capture-формат (плёнка / флэш / CCTV / bodycam / FMV / game engine) и `--style raw --s 50`. Нет — провал. См. Закон 0.

### Тест 8 — WOW: пересказ ≤5 слов? (ГЛАВНЫЙ)
Перескажи кадр одной фразой до 5 слов. Фраза вызывает «ЧТО?!» у чужого человека («мотоцикл припаркован на кресле»)? Если фраза звучит как описание фотосессии («модель в куртке под дождём») — провал по W1. Плюс проверка W10: этот кадр уже гулял по AI-лентам? Если да — сменить коллизию или медиум.

**Если из 10 кадров прошли только 4 — выдай 4.** Не разбавляй.

---

## Слой 2.5 — SPECTACLE LAYER (ОБЯЗАТЕЛЬНО, ставится поверх мира)

Главная причина провала прошлых россыпей — кадры выглядят как **«красивая улица + крутая модель»**, а не как **«событие, которое нельзя пропустить»**. Зритель скроллит за 0.4 секунды.

⚠️ **АНТИ-РЕЦЕПТ:** прошлая формула «стихия + тотем + абсурд в каждую россыпь» сама стала шаблоном — каждая констелляция выходила одинаковой (дождь, злая собака, горящий капюшон). Больше НЕ собирать все три автоматически.

### Spectacle 2.0 = ЯДРО + максимум ДВА усилителя

**0. CORE COLLISION (СТОП-ГЕЙТ — без неё россыпь НЕ ВЫДАЁТСЯ вообще):**
Сквозная коллизия двух несовместимых миров по W2, сформулированная одной фразой уровня арт-дирекшена: «готический кутюр живёт в советской панельке», «техвир-курьеры обслуживают руины собора», «бренд существует внутри PS2-игры 2003 года». Коллизия вырастает из triangulation (шмотка × бренд → мир) и определяет ВСЁ: локацию, кастинг, реквизит, медиум.

⛔ **Гейт-проверка (обязательная, ДО генерации кадров): назови ДВА мира, которые сталкиваются в констелляции.** Если мир один — коллизии нет, генерировать кадры запрещено, вернись и придумай коллизию. Типовая ловушка (боевой провал 2026-07-03): скилл выбрал когерентный мир, идеально подходящий бренду (готика для гот-бренда: крипта + свечи + питон + оскал), и решил, что этого достаточно. **Мир, соответствующий бренду — это сцена, а не идея.** Получился дорогой Rick Owens-эдиториал, где каждый кадр пересказывался как «модель в склепе» — ни одного «ЧТО?!». Соответствие бренду даёт ОДИН из двух миров коллизии; второй мир обязан быть ему чужим (готика × автобусная остановка, крипта × супермаркет, кутюр × очередь в поликлинику).
Проверка формулы: если коллизию нельзя пересказать с эффектом «ЧТО?» — это не коллизия, а мудборд.

**Усилители (выбрать 0–2 из трёх, только те, что усиливают КОЛЛИЗИЮ, а не заменяют её):**

**1. STIHIA / WEATHER EVENT (опционально — не «погода», а событие):**
| Стихия | Что прописывать дословно | Под какие миры |
|---|---|---|
| **Ливень-стена** | `torrential monsoon downpour, sheets of rain backlit by sodium streetlamp, water sluicing off rooftops, ankle-deep flood on street, raindrops streaking past flash` | city-grit · cultural-specific · sacred-decay |
| **Затопленный город** | `street flooded knee-deep with brown stormwater, debris and plastic crates floating, motorbikes half-submerged, single light pole sticking out of water` | city-grit · cultural-specific · liminal |
| **Гроза с молниями** | `lightning strike forking across sky in deep background, sky cracked open, one bolt frozen mid-strike illuminating wet figure, electrical hum in air` | post-apoc · rooftop · climate-extreme · sacred-decay |
| **Горящий город / пожар** | `building burning in background, orange flame light raking subject from frame-right, smoke pouring across frame, ash falling like black snow, distant siren glow` | city-grit · post-apoc · industrial-isolated |
| **Дым/пожарный туман** | `dense black smoke rolling across alley at hip-height, embers floating, orange glow of unseen fire behind, visibility 8 meters` | city-grit · industrial · post-apoc |
| **Метель / снежная буря** | `horizontal blizzard, snow striking subject sideways, breath in clouds, drift on shoulders building, single sodium lamp halo in white-out` | climate-extreme · industrial-isolated · nature-grit |
| **Песчаная буря** | `sandstorm wall advancing, visibility 5 meters, harmattan dust orange-grading everything, subject squinting into wind` | nature-grit · cultural-specific (Morocco/Mongolia) |
| **Цунами / прибой** | `storm surge crashing over seawall behind subject, white spray exploding mid-frame, ankle-deep saltwater on stone street` | coast · island · cultural-specific |
| **Извержение / пепельный дождь** | `volcanic ash falling like grey snow, sulfur haze, orange crater glow on horizon, ash settling on shoulders and hair` | volcanic field · post-apoc |
| **Затмение / красная луна** | `blood-red full moon hanging huge low on horizon, abnormal red wash on everything, no other light source, dogs howling in distance` | nature-grit · sacred-decay · post-apoc |
| **Стихия-зверь** (ген SURREAL огненный дракон) | `the wildfire behind the subject rears up in the shape of a colossal fire serpent / smoke coiling into a dragon's head, embers as scales, the subject small in foreground unbothered` | nature-grit · post-apoc · cultural-specific (JP/CN) |
| **Комета / метеор** (ген SURREAL) | `a bright comet streaking low across the starfield, long ionized tail, dust trail, single cold highlight on the subject from above, deep space black` | climate-extreme · nature-grit · liminal-dreamcore |
| **Биолюм-свечение** (ген SURREAL светящееся поле) | `the ground/field glows with bioluminescent bloom, cold blue-violet light rising from below, glowing petals or spores lifting into the air, subject backlit by a single moon-hard beam` | nature-grit · liminal-dreamcore · jungle |

⚠️ **Стихия — не атмосферная подпись**, а **действующий персонаж кадра**. Должна влиять на: ткань (мокрая/обугленная/в снегу), волосы (прилипшие/развевающиеся), землю (лужи/пепел/затопление), свет (молния/пламя/blue-on-blue blizzard), действие героя (закрывается рукой / щурится / бежит).

**2. TOTEM ANIMAL (опционально — если выбран, встречается в 1–2 кадрах из 6):**

| Архетип бренда | Подходящие тотемы | Как прописывать |
|---|---|---|
| **Dark streetwear / dystopia** | `massive black wolfhound, eyes glowing yellow` · `black horse with blood-red eyes` · `three-headed mastiff Cerberus, drool` · `huge raven with broken wing` | стоит рядом с героем, в той же позе, мокрое от дождя, не милое |
| **Goth / occult / sacred-decay** | `pale unicorn with blood-stained horn, ribs visible` · `demon goat with curling horns, blank white eyes` · `swarm of crows on shoulders` · `albino python coiled around arm` | как ритуальный спутник, candle-lit, неподвижный, прямо смотрит |
| **Western / americana** | `wild mustang stallion, dust-caked` · `pack of coyotes` · `lone vulture on fence post` · `longhorn skull held aloft` | в кадре как природный хищник, golden hour rake |
| **Couture-avant / sculptural** | `swan with blood on neck` · `albino peacock fanning` · `bull with horns wrapped in chain` · `swarm of moths around face` | сюрреально-неподвижное, монументальное |
| **Cyber-dystopia / techwear** | `Doberman with chrome muzzle` · `wolf with glitching neon eyes` · `mechanical drone-bird` · `feral cat with shaved patterns` | техно-животное, неон-глаза |
| **Heritage / pastoral** | `bull with brass nose ring` · `pack of sheepdogs` · `goshawk on glove` · `lone wolf at treeline` | реалистично, в природной среде |
| **Cultural-specific** | Vietnamese: `water buffalo with mud caked` · `fighting cock with bloodied spur` · `imperial dragon kite overhead` · `swarm of bats from temple` | культурно точно, не Disney |
| **Tribal / global-craft** | `camel with kohl-eye paint` · `falcon mid-flight` · `python` · `panther` | mythic, монументально |

⚠️ Тотем — **не милый pet и не sidekick**. Прописывать дословно характер: `mangy, scarred, missing one eye, ribs showing, drooling, bloodied, dust-caked, eyes glowing`. Никогда `cute, fluffy, happy, playing`.

**3. ABSURD MICRO-DETAIL (опционально — мелкая нелогичность второго просмотра, НЕ замена коллизии)**

Один сверхъестественный/нелогичный элемент, который зритель замечает на второй пересмотр. Примеры:
- `model's hood is on fire but he doesn't react`
- `chain pendant floating upward against gravity`
- `swarm of moths circling head like halo`
- `single goldfish flopping in puddle next to boot`
- `model's shadow points wrong direction from light source`
- `crow perched on shoulder, completely still`
- `mannequin propped against wall in background mimicking model's pose`
- `floating sheets of burning paper drifting past`
- `eyes catching flash with feral animal eyeshine (white reflection)`
- `model holds a still-burning candle in the rain — flame not extinguishing`
- `one boot lace untied and floating in mid-air`
- `phone in puddle face-up still glowing screen`
- `single neon light-drawing line traces the subject's profile and hand in mid-air` (ген SURREAL «don't leave me»)
- `ring of small flames burning a symbol into the gravel around the subject's feet` (ген SURREAL огненный круг)
- `three glowing blades passing straight through the torso, no wound, no reaction` (ген SURREAL Таро — символ буквально)
- `chunks of ceiling plaster frozen mid-air around the subject who does not react` (ген SURREAL RAM — frozen debris)
- `handwritten culture-scrawl painted across a huge object behind — a meme-phrase, not a logo` (ген SURREAL «NEED MONEY FOR PAGANI»)

⚠️ Абсурд = **одна вещь на кадр, не два**. Должна быть прописана **деталью, не атмосферой**: «moth crawling across left eyebrow», не «mystical aura».

### Применение Spectacle 2.0 к россыпи

- **CORE COLLISION — сквозная, читается во всех 6 кадрах** (это и есть мир констелляции), но её невозможный элемент раскрывается по лестнице эскалации W5: намёк → присутствие → пик на позиции 3–5 → послевкусие.
- **Стихия — ЕСЛИ выбрана, то во все 6 кадров** (одинаковая, как Style anchor — это часть мира). Если не выбрана — не выдумывать дождь «для красоты».
- **Тотем — ЕСЛИ выбран, то в 1–2 кадрах** (роль TOTEM в пуле ролей + опционально фоном в crew-кадре). Тотем без функции в коллизии = AI-клише (см. W10).
- **Абсурд-микродеталь — максимум в 2 кадрах**, разные. НЕ во всех (передоз ломает «captured» эстетику) и НЕ вместо коллизии.
- Итоговая проверка слоя: убери из констелляции стихию и тотем — ВАУ должно остаться (оно живёт в коллизии). Если без дождя и собаки кадры превращаются в лукбук — коллизия слабая, переделать ЯДРО, а не добавлять усилители.

---

## Слой 3 — Сборка констелляции: 2 фикс-слота + ролевой пул (НЕ шаблон!)

⚠️ Старый жёсткий порядок «FISHEYE → TOTEM → DETAIL → CREW → WAIST → ENDING» был источником одинаковых россыпей — каждая выходила с тем же скелетом. Теперь фиксированы только **Кадр 1 (HOOK)** и **Кадр 6 (AFTERMATH)**. Кадры 2–5 собираются из ролевого пула под конкретную коллизию и раскладываются по лестнице эскалации W5: **пик невозможного — на позиции 3–5, не в начале.**

### Фикс-слот: Кадр 1 — HOOK (конфронтация или POV-вовлечение)
Самый динамичный кадр россыпи, но НЕ самый невозможный (пик позже — W5). Два варианта на выбор:
- **Вариант A — MAIN FISHEYE:** низкий угол снизу + fisheye 8–14mm / wide 20mm. Модель **наступает на камеру**, шмотка доминирует нижние 2/3, лицо/торс врываются в линзу. Camera: aggressive handheld push-in. Action: strides into lens / lunges / thrusts hand toward camera / boot-stomp.
- **Вариант B — POV HOOK (ген Bandit/ps2 Skull):** зритель = участник с первого кадра: POV-руки в рукавах героя на руле/на перилах, крю целится взглядами В линзу через лобовое, зверь идёт НА камеру. Закрывает требование W4 сразу.
- Hook намекает на коллизию (виден её след/тень/деталь), но не раскрывает пик.

### Фикс-слот: Кадр 6 — AFTERMATH (послевкусие, не пик)
Герой **уходит вглубь кадра**, силуэт против вспышки, последний взгляд через плечо, deadpan-натюрморт последствий (следы коллизии на земле). Эмоция: «фильм закончился, осталось послевкусие».
- Camera: ultra-wide 16–20mm static handheld OR telephoto 85mm compression
- Composition: leading lines к фигуре / negative space / память о коллизии в кадре
- Разрешён вариант DARK AFTERMATH по W8: 90% черноты, один луч, силуэт шмотки.

### Ролевой пул для кадров 2–5 (выбрать 4 РАЗНЫХ под коллизию, не по алфавиту)

| Роль | Что это | Камера | Когда брать |
|---|---|---|---|
| **COLLISION ICON** ⭐ обязателен | Чистая коллизия deadpan-тэблоу (ген Spike3/Robot/Horse): объект/герой не в своей комнате, снято скучающей камерой как хроника | mid-wide 35mm, eye-level, static — нарочито «никакая» | В КАЖДОЙ констелляции, ставить на позицию пика (3–5) |
| **POV IMPLICATION** ⭐ обязателен, если Кадр 1 = вариант A | Зритель-участник (W4): POV-руки, пасть/взгляд/жест в 10 см от линзы | fisheye/wide POV, handheld | Всегда, если не закрыт Кадром 1 |
| **TOTEM** | Герой + зверь как зеркало (mangy/scarred, stares into lens); PROP TOTEM если зверь не подходит | low-mid wide 24mm, drift | Только если тотем выбран в Spectacle 2.0 |
| **ACTION CLOSE-UP / DETAIL** | Руки/тело рвут-хватают-зажигают; 60–80% кадра — фактура шмотки, глагол обязателен | macro 35–50mm / overhead / Dutch | Когда у вещи сильная фактура/hardware |
| **GROUP / CREW WIDE** | 3–5 фигур в выживальческой постановке (марш сквозь стихию, выход из дыма), V-formation | wide 20–24mm handheld | Когда бренд = крю-культура; каждая фигура в garment lock или униформе мира |
| **ACTION MEDIUM / WAIST** | Талия/hardware/hem — герой кадра, pelvis-to-knees crop, weight-shift mid-step | medium 35mm chest-height | Когда у вещи пояс/hardware/переходы силуэта |
| **DARK ICON** | Радикальная тьма W8 (ген Knight): 90% чёрного, один луч, из тьмы выступает ТОЛЬКО силуэт/фактура вещи | 50mm static, single hard shaft | Куртки/кожа/металл, noir-бренды; макс 1 на россыпь |
| **WORLD DEADPAN** | Мир коллизии БЕЗ героя: memento-mori натюрморт (ген Desert: могила с ботинками), следы жизни бренда в мире | mid-wide static, хроникальный | Когда мир сам пересказывается ≤5 слов; макс 1 |
| **DOUBLE-EXPOSURE ICON** | Профиль/силуэт героя заполнен вторым миром (ночной город, звёзды, горящее поле); эмоциональный кадр-обложка (ген SURREAL) | 50–85mm портрет, статичный | Портрет-нота вместо DARK ICON; макс 1; шмотка читается по силуэту/воротнику |
| **GOD-SCALE** | Невозможный масштаб в тумане: колосс со светящимися глазами / стихия-зверь, герой в шмотке — крошечный scale-маркер на переднем плане (ген SURREAL колосс, дракон) | ultra-wide 16mm, фигура низом кадра | Когда бренд эпичный/мифо; фигура мелкая — шмотка тут НЕ читается, поэтому макс 1 и не в счёт garment-квоты |

### Правила сборки
- **COLLISION ICON — обязателен всегда, без исключений.** Если в собранной россыпи нет ни одного кадра, чей пересказ ≤5 слов звучит невозможно («готы буднично ждут автобус», «шуба висит среди мясных туш») — констелляция бракуется ЦЕЛИКОМ, вернись к шагу 4.5 и пересобери коллизию. Красивых кадров без этого не выдавать.
- **POV IMPLICATION — обязателен** (в пуле или как Кадр 1 вариант B).
- **Эскалация W5:** позиции 2→5 идут по нарастанию невозможного; пик (обычно COLLISION ICON) — на 3–5.
- **Mode B минимум в 2 кадрах** (мир будничный, шмотка = гость).
- **≥2 иконы-thumbnail** (W7) — обычно COLLISION ICON + DARK ICON/TOTEM.
- **Не повторять набор ролей и коллизию из предыдущей констелляции** — если юзер генерит подряд, менять скелет.

### Квоты на россыпь
- **Garment fully readable: минимум в 4 из 6 кадров.**
- **Пересказ ≤5 слов с эффектом «ЧТО?»: ВСЕ 6 кадров (W1).**
- **Одна невозможность на кадр, не больше (W6).**
- **Лицо/тело в действии: минимум 4 из 6** (DARK ICON и WORLD DEADPAN могут быть неподвижными).
- **Динамика интенсивности (W5b): ≥2 тихих/deadpan-кадра, ≤2 кадра одного типа крупности+эмоции, ровно ОДИН пик громкости.**
- **Низкий угол / wide distortion: минимум 3 из 6.** Deadpan-кадры (COLLISION ICON, WORLD DEADPAN) имеют право на нарочито скучный eye-level — это их сила (W3).
- **Стихия: если выбрана — во всех 6; тотем: если выбран — в 1–2.**
- **Абсурд-микродеталь: максимум в 2 кадрах.**
- **Пустые luxury-интерьеры: 0.**
- **Все 6 — Закон 0 (capture-формат + грязь).**
- **Все 6 — идентичный Style anchor (копипаст).**
- **Минимум 3 из 6 — активная камера** (handheld, push-in, whip, lurch); deadpan-кадры — статичная хроника, это ок.

---

## 🎨 STYLE ANCHOR — копируется во ВСЕ 6 кадров

Один capture-формат + один grade + один свет — выбрать ОДИН раз для россыпи и **вставлять дословно в каждый промпт**.

### Capture-форматы (выбрать ОДИН)
| Формат | Когда | Фраза |
|---|---|---|
| **Прямая вспышка / точкастрел** | Городской ночной грит, абсурд в бытовухе, chain/mesh, edgy | `harsh direct on-camera flash, cheap point-and-shoot snapshot, flat frontal light, blown highlights, deep black background, red-eye, snapshot aesthetic` |
| **Просроченная плёнка 35мм** | Магический реализм, грит-дэй, Paris/Y2K | `shot on expired 35mm film, heavy grain, halation on highlights, faded washed-out color, light leaks, motion blur` |
| **CCTV / surveillance** | Found-footage вайб, parking deck, alley | `grainy CCTV still, timestamp-free security camera angle, low-light noise, fish-eye corner mount` |
| **Bodycam / GoPro POV** | Action, погоня, urban movement | `bodycam fisheye POV, motion blur, overexposed blown highlights, shaky, low-res snapshot` |
| **PS3-era FMV / videogame still** | Post-apoc, грозовое небо, FF-mood | `early-2010s videogame cutscene still, soft compression artifacts, low dynamic range, grungy color grade, washed-out blues` |
| **Phone snapshot, overcast day** | Y2K Japan, candid alley, документалка | `blurry phone camera still, flat overcast daylight, washed cool color, blown-out white sky, accidental framing` |
| **Polaroid SX-70 / instant** | Domestic-intimate, motel, kitchen, soft-grunge | `Polaroid SX-70 instant photo, lifted highlights, soft milky shadows, warm cast, faded border edge, slight chemical bloom` |
| **Medium format 6x6 film** | Couture-avant, sculptural, opera foyer, palace decay | `6x6 medium format film still, fine grain, square frame, natural color, deep blacks, slight halation` |
| **Concert pit / paparazzi tele** | Crew / sport / underground rave | `paparazzi telephoto 200mm grab, motion blur, shallow focus, harsh on-camera flash from afar, compressed background` |
| **Wildlife trail-cam / IR** | Forest / desert / industrial isolated | `trail camera infrared still, monochrome night vision, timestamp burn, motion-triggered flash, harsh frontal` |
| **Hi8 home video** | Y2K nostalgia / pastoral / domestic | `Hi8 home video still, interlacing artifacts, oversaturated color, date stamp burn, lens dust, low resolution` |
| **35mm slide film (Kodachrome)** | Pastoral / heritage / western / cultural | `Kodachrome 35mm slide still, saturated warm reds, deep blue sky, sharp grain, vintage editorial feel WITHOUT being editorial` |
| **PS2/PS3 game engine** (ген ps2 Skull / AltGirl) | Y2K-revival / cyber / skater / «игра, которой не существует»; шмотка = скин персонажа | `early-2000s PlayStation 2 game footage, low-poly 3D character, flat baked textures, muddy draw-distance fog, jagged edges, interlaced video compression, in-game third-person camera` |
| **Radical noir B&W** (ген Knight) | Кожа/металл/couture-noir; кадры DARK ICON и DARK AFTERMATH | `extreme low-key black-and-white film still, 90 percent of frame in pure crushed black, single hard shaft of light, subject barely emerging from darkness, heavy grain, wet skin catching highlight` |
| **POV-проход found-footage** (ген Coridor) | Liminal-миры, подъезды/коридоры, Kling-переходы между кадрами | `first-person walking POV, wide handheld phone camera, fluorescent corridor light, slight fisheye, found-footage pacing, uncorrected white balance, motion wobble` |
| **Double-exposure / in-camera composite** (ген SURREAL «don't leave me», комета) | Портрет-икона, dreamcore, эмоциональный кадр; silhouette героя заполнен вторым миром | `in-camera double exposure, subject's silhouette filled with a second scene (night city / starfield / burning field), analog film multi-exposure, light bleed, soft ghosting overlap, grain` |
| **Surreal photo-composite** (ген SURREAL Порше-в-квартире, RAM-сквозь-потолок) | COLLISION ICON / Mode B, невозможный объект в реальном интерьере | `photorealistic composite, impossible object placed in a mundane real space, matched flash/practical lighting, frozen debris mid-air, deadpan snapshot, film grain, looks like a real photo someone faked` |

### Grade (выбрать ОДИН под мир)
- **Cool steel + warm practical** (HK / Tokyo / cyber-dystopia / underground parking): `cool teal-leaning steel base, deep crushed shadows, one warm sodium/neon highlight, no soft fill`
- **Washed cool overcast** (Y2K Japan / Berlin / mall liminal / stormy moor): `flat cool overcast grade, desaturated, no warmth, blown white sky`
- **Low warm sun + deep shadow** (Paris / LA / cornfield / Mojave / cultural-specific): `low-angle warm directional sun raking subject, hard deep crushed shadow on opposite side, no fill`
- **Stormy diffuse + lightning** (post-apoc / mountain ridge / coast / oil rig): `stormy diffuse grey light, soft-edged lightning flashes, wet desaturated palette`
- **Candle / single bulb interior** (sacred-decay / motel / kitchen-3am / catacombs / witch hut): `single warm tungsten bulb / candle pool, surrounding swallowed in deep black, halation on flame, no fill`
- **Earth-tone overcast** (nature-grit / heritage-craft / pastoral / fishing village / pine forest): `muted earth grade, brown-green palette, soft flat diffused daylight, fog in mid-ground, no saturated colors`
- **Bleached desert midday** (salt flats / Mojave / volcanic field / cornfield noon): `harsh overexposed white sun, bleached colors, deep black under-shadow, heat haze, no atmosphere`
- **Frost-blue alpine** (frozen lake / ski lift / sub-zero / glacier): `cold blue-white grade, visible breath, frost halation, no warmth at all, single low warm sun if any`
- **Snow / white-out** (sandstorm / snowstorm / fog): `white-on-white near monochrome, low visibility, single dark figure as only contrast, desaturated to near grey`
- **Tropical green-wet** (jungle / rice paddy / mangrove / monsoon): `humid green-leaning grade, wet leaves catching highlights, soft haze, no harsh sun`
- **Crushed noir B&W** (DARK ICON / Knight-ген / noir-бренды): `high-contrast black-and-white, blacks crushed to pure black, single hard highlight, no mid-greys, film grain`
- **Low-poly engine grade** (PS2-регистр): `muted early-2000s game palette, orange-brown apocalyptic sky OR grey-green fluorescent interior, dithering, low dynamic range, texture-baked shadows`

⚠️ Тёплое = **точечный практический источник** (одна лампа, неон, фара, низкое солнце), НЕ «golden hour magic light». Запрещены: `amber light, golden hour, warm glow, beautiful light, dramatic light, cinematic light` без конкретного источника.

### Палитра (что писать в Style anchor)
> Style: `<capture-формат>`, `<grade>`, heavy grain, slight motion blur, imperfect focus, looks like real found street photography — not a render, not editorial.

---

## Технические законы промпт-инжиниринга (унаследовано из боевой версии)

Каждый отвечает на конкретный провал из 30+ предыдущих сессий. Не нарушать.

### L0 — Capture-формат и grit-параметры
- В каждом промпте — **один capture-формат** из меню выше.
- `--style raw --s 50` дефолт. Никогда `--s 250+`.
- **Запрещённые слова в промптах:** `cinematic, luxury, pristine, immaculate, 8k, hyperdetailed, octane, unreal engine, glossy, polished, beautiful, elegant, masterpiece, editorial, vogue, perfume ad, golden hour, amber, warm glow, soft light, dramatic lighting, beauty light, model headshot, professional photography`.

### L1 — Якорь первым, шмотка во второй фразе
Первые 10 слов = 70% внимания модели. Структура:
```
[Камера + угол + capture-формат]. [Субъект + GARMENT LOCK + action глагол]. [Локация + один источник света]. [STYLE ANCHOR]. --ar 4:3 --style raw --s 50 --v 8.1
```

### L1a — Garment dominates lower frame
Когда шмотка должна быть героем кадра (кадры 1, 2, 6) — **прописывай место в кадре дословно**: `the floor-sweeping chain-mesh skirt fills the lower two-thirds of frame, dragging on wet concrete in foreground`.

### L2 — Один сюр-якорь, без вложенных описаний
Не «куртка покрыта вышитыми глазами на принте джинс с patches with chains» — модель схлопнется. **Одна сильная деталь + одна поддержка.** Всё остальное — в Style anchor.

### L3 — Сквозной style anchor для всей россыпи
6 кадров = один фильм. **Идентичная style-секция во всех 6 промптах**, дословно скопирована.

### L4 — Character lock через явное описание
MJ не помнит героя между кадрами. **3 идентичных маркера в каждом кадре с героем:** возраст + причёска/одежда вне героя-шмотки + опознавательная деталь (татуха, пирсинг, цвет волос, цепь).
> e.g. `young East-Asian man early 20s, bleached white buzz cut, silver hoop earring, faded jaw tattoo`

⚠️ **В тело промпта НЕ подставлять `--cref`, `--sref`, `--cw`.** Пользователь подкрепит референсы в интерфейсе MJ через drag-and-drop. Скилл выдаёт текстовый промпт + только базовые параметры (`--ar 4:3 --style raw --s 50 --v 8.1`).

### L5 — Никакого ЛОГОТИПА бренда в кадре (но culture-scrawl разрешён)
Логотип/название твоего бренда накладывается в After Effects. **Не закладывай лого бренда, его имя, «надпись на куртке» с неймом.** Принты/паттерны на одежде — ОК (часть garment DNA), но не логотип.

⚠️ **Уточнение (ген SURREAL «NEED MONEY FOR PAGANI», «don't leave me»):** рукописный **culture-scrawl / мем-фраза на реквизите** (граффити на капоте, тег на стене, фраза-double-exposure) — это НЕ логотип, а мощный WOW-приём и разрешён. Правила: (1) фраза — на постороннем объекте (машина, стена, небо), НЕ на продвигаемой шмотке; (2) это мем/эмоция/ирония («need money for pagani», «don't leave me», «not for sale»), не название бренда; (3) макс 1 такой кадр на россыпь. Это добавляет «человек это написал» — усиливает Закон 0.

### L6 — Лимит сложности на кадр
Максимум 3 нарративных элемента: субъект + действие + одна деталь среды. Остальное — свет/фактура/style.
**L6a — MJ не считает выше 3–4.** Для групп: `a row of approximately five figures shoulder-to-shoulder`.

### L7 — Светотеневые коллизии: укажи явно
«Warm vs cold» в общем виде модель игнорирует. Конкретно:
✅ «Harsh sodium streetlamp rakes the model's face from frame-left. Cool blue dusk on the wet asphalt frame-right. Crushed black shadow under the coat hem.»

### L8 — Кадр 1 = HOOK = конфронтация или POV, но НЕ пик
Открывающий — самый динамичный: low-angle fisheye наступание на камеру (вариант A) или POV-вовлечение зрителя (вариант B). Стихия, если выбрана, уже в кадре. Но пик невозможного — НЕ здесь (W5): hook даёт намёк на коллизию, удар приходит на позиции 3–5. Establishing-world-нота — это Кадр 6 AFTERMATH, не первый.

### L9 — Никакой статики, motion в каждом
**≥4 из 6 кадров с активной камерой** (push-in, orbit, handheld, lurch, whip, track). Locked-off только для детальных still-life (кадр 6) или симметричного crew tableau.

**Язык камеры под мир:**
| Мир | Камера |
|---|---|
| HK / Tokyo dystopia | Low-angle handheld, push-in to face, fisheye lurch, neon reflections in motion |
| Paris / LA crew | Mid-handheld pan across group, low warm sun pivot, slow dolly side |
| Y2K Japan alley | Static phone-snap framing, slight handheld drift, candid pull-back |
| Post-apoc storm | Slow crane down on figure, lightning strobe cuts, wide dolly back |
| Underground parking | Tracking shot parallel to columns, bodycam follow, fluo flicker |

Дефолт — **handheld**, НЕ «slow elegant dolly». Handheld = «камера там была».

### L9b — Оптика под кадр (новый порядок)
- **Кадр 1 (HOOK):** fisheye 8–14mm ИЛИ wide 20mm с barrel distortion, низкий угол; вариант B — POV fisheye handheld.
- **COLLISION ICON / WORLD DEADPAN:** mid-wide 35mm eye-level static — нарочито хроникальная «скучная» камера (это законное исключение из правила дикой оптики, см. Тест 4).
- **TOTEM:** mid-low wide 24mm, locked-off с handheld drift, оба субъекта в кадре.
- **DARK ICON:** 50mm static, один жёсткий луч, 90% черноты.
- **ACTION CLOSE-UP / DETAIL:** macro 35–50mm / overhead / Dutch.
- **GROUP WIDE:** wide 20–24mm с perspective distortion at edges, handheld.
- **ACTION MEDIUM / WAIST:** medium 35mm chest-height handheld, slight low angle.
- **Кадр 6 (AFTERMATH):** ultra-wide 16–20mm static handheld ИЛИ telephoto 85mm compression (silhouette case).
- **Никакого 85mm beauty-shot** — допустим 85mm только для silhouette/wide-сжатие в AFTERMATH.

### L10 — Реквизит в широких планах дропается
В широком кадре маленький предмет рядом с фигурой и пейзажем модель выбросит. Делай реквизит **крупным** (motorcycle / bicycle / boombox / shopping cart / chain pile) или выноси в **отдельный close-up** (кадр 6).

### L11 — Two-subject anchoring через положение
«X с lefty, Y с righty» = swap. Якорь пространством:
✅ «**Frame-left:** young man in chain-mesh tunic, mid-stride toward us. **Frame-right:** girl in oversized leather puffer, lighter sparking in cupped hand.»

### L12 — Субъект в действии, не в позе (КРИТИЧНО)
Виральный кадр fashion-промо — **миллисекунда движения**, не статуэтка. Спокойный позирующий герой = каталог.

❌ Статика: «model stands wearing chain-mesh top», «girl poses in puffer», «boy holds chain casually».
✅ Динамика: «model strides into lens, chain-mesh hem swinging mid-step, head snapping toward camera», «girl thrusts hand into frame, puffer sleeve crushing into fisheye», «boy mid-spin, chain whipping around hip».

**Минимум один активный глагол на главного субъекта в каждом кадре.** Палитра:
- Движение тела: `strides / lunges / mid-step / mid-spin / mid-turn / leans into / pushes off / pivots`
- Жесты: `thrusts hand / flicks lighter / throws sign / cracks knuckles / pulls hood / grabs chain`
- Лицо/корпус: `head snaps / glares into lens / mid-shout / mid-drag of cigarette / blows smoke`
- Шмотка живёт: `fabric whips / chain swings / hem drags / sleeve crushes / hood falls / collar pops`

### L12b — Peak Millisecond
В промпте каждого action-кадра — слово-маркер пика:
| Маркер | Когда |
|---|---|
| `mid-step / mid-stride / mid-turn / mid-spin` | движение тела |
| `mid-snap / mid-snarl / mid-shout` | лицо |
| `mid-throw / as it lands` | броски, удары |
| `caught mid-air / whipping / swinging` | ткань, цепь, волосы |
| `thrusting into lens / looming at camera` | конфронтация |

Если ни одного маркера — переписать.

### L13 — Kling = временна́я дуга, а не подпись (КРИТИЧНО для видео)
MJ-кадр = одна миллисекунда. **Kling должен описать что происходит за 5 секунд ПОСЛЕ неё.**

**Структура динамичного Kling-промпта (3 бита через временны́е связки):**
```
[Якорь + стартовое состояние.] [БИТ 1 — субъект запускает действие: активный глагол.]
[БИТ 2 — пик разворачивается + среда оживает: "as ... , ...".]
Camera: [движение, синхронное действию]. Lighting: [практический источник + как он мигает/дёргается]. [STYLE ANCHOR дословно.]
```

**Три обязательных слоя движения** (нет одного — переписать):
1. **Движение субъекта** — глагол во времени: «strides forward, chain hem swinging as the model steps, head snapping toward lens».
2. **Движение шмотки** — fabric/chain/hood/sleeve в кадре оживает: `chain hem catches the asphalt, swings out`, `puffer sleeve crushes into the lens`, `wide pant-leg pools then sweeps as he pivots`.
3. **Движение камеры**, синхронное действию — push-in *на* шаг, whip-pan *за* поворотом головы.

**Временны́е связки — обязательны:** `as`, `then`, `the instant`, `mid-`, `whipping`, `snapping`, `swinging`, `right as`.

❌ Статично: «Model wears chain-mesh top. Camera: push-in. Lighting: flash.»
✅ Динамично: «Young East-Asian man in chain-mesh tunic strides into the lens — the instant his boot lands the chain hem swings out hitting wet concrete, his head snaps right and the on-camera flash fires hard. Camera: low-angle handheld push-in lurching with his step. Lighting: harsh on-camera flash strobing once at apex of stride, sodium spill from background filling shadows.»

**L13a — Конкретные действия, не атмосфера.** Kling исполняет глаголы тела, не настроение. Список простых действий: «walks up, stops, throws hand up at camera, flips hood back, mid-step kick, picks up chain, throws sign, spits cigarette out». НЕ пиши «outfit blowing into pure light, reflections dancing» — Kling это игнорирует. Свет и фактура — ТОЛЬКО в Lighting и Style anchor, не в теле действия.

**Длительность:**
- **5s** — один разворачивающийся пик (один глагол доходит до взрыва)
- **10s** — два бита (запуск → пик → оседание: цепь ещё качается, флэш ещё мигает в дыму)

---

## Формат вывода (ВСЕГДА когда генерируется россыпь)

```markdown
# 🎬 Промо-констелляция: <короткое название идеи>

**GARMENT DNA:**
- Тип: <one line>
- Силуэт: <one line>
- Материал/цвет: <one line>
- Deco/маркеры: <one line>
- Visual hook: <one phrase>

**🌍 Мир:** <выбранный мир, 1 строка с обоснованием — почему он усиливает hook>

**💥 CORE COLLISION:** <одна фраза-коллизия уровня арт-дирекшена: «X живёт в Y» / «X вторгается в Y» — это идея всего ролика. Поле НЕ МОЖЕТ быть пустым или содержать один мир («готика в крипте» — не коллизия); без валидной коллизии выдача запрещена>

**⚡ SPECTACLE 2.0 (усилители — только выбранные, 0–2):**
- **Стихия:** <если выбрана — одна из weather event фраз дословно; иначе «—»>
- **Тотем:** <если выбран — архетип + характер: mangy/scarred/bloodied + что делает; иначе «—»>
- **Абсурд-микродетали:** <макс 2 на россыпь; иначе «—»>

**📈 Лестница эскалации:** <карта одной строкой: Кадр 1 намёк → ... → Кадр N ПИК → Кадр 6 послевкусие>

**🔒 GARMENT LOCK (копируется во ВСЕ 6 кадров — НЕ варьировать):**
> "<тип> with <силуэт + deco>, <цвет/материал>, <visual hook>"

**🔒 Style anchor (копируется во ВСЕ 6 кадров — НЕ варьировать):**
> Style: <ОДИН capture-формат из меню>, <ОДИН grade>, heavy grain, slight motion blur, imperfect focus, looks like real found street photography — not a render, not editorial.

**🔒 Character lock (если есть сквозной герой):**
> <возраст + национальность/раса + причёска + опознавательная деталь — дословно во все кадры с героем>

---

### Россыпь (6 кадров: HOOK + 4 роли из пула + AFTERMATH, порядок = лестница эскалации)

Каждый кадр озаглавлен **пересказ-фразой ≤5 слов** (W1) — она и есть проверка на ВАУ.

#### Кадр 1 — «<пересказ ≤5 слов>» — HOOK <вариант A fisheye / B POV> · Mode <A/B>
- **Subject move:** <активный глагол + взаимодействие с миром/стихией>
- **MJ prompt:**
  ```
  <Камера + угол + capture-формат>. <subject + character lock + GARMENT LOCK дословно + active verb>. <Location + коллизия/стихия + one practical light>. <STYLE ANCHOR дословно>. --ar 4:3 --style raw --s 50 --v 8.1
  ```
- **Kling prompt (5s):**
  ```
  <Anchor start state.> <BEAT 1: subject launches action.> <BEAT 2: peak unfolds via "as/the instant" + garment lives + мир reacts.> Camera: <movement synced to action>. Lighting: <practical source + how it flicks>. <STYLE ANCHOR verbatim>.
  ```
- **Camera/Duration:** <...> / 5s

#### Кадры 2–5 — «<пересказ ≤5 слов>» — <РОЛЬ из пула> · Mode <A/B>
[та же структура на каждый кадр; обязательно: COLLISION ICON присутствует и стоит на позиции пика (3–5); POV IMPLICATION закрыт здесь или Кадром 1-B; роли подобраны под коллизию, не по алфавиту]

#### Кадр 6 — «<пересказ ≤5 слов>» — AFTERMATH (послевкусие / DARK AFTERMATH)
[та же структура — уход вглубь кадра / silhouette / deadpan-натюрморт последствий коллизии]

---

### Workflow генерации (вручную в Midjourney)
1. Сначала **Кадр 1 (HOOK)** в MJ — он задаёт фактуру всей россыпи.
2. После генерации Кадра 1: пользователь **вручную** добавляет в окне MJ:
   - **Style Reference:** drag-and-drop сгенерированного Кадра 1 → во все остальные 5 промптов (единый фильм-вайб).
   - **Character Reference:** drag-and-drop фото шмотки → во все 6 (garment lock). Второй cref — крупное лицо героя после утверждения.
   - `--cw` (character weight) подкручивается пользователем в интерфейсе по вкусу.
3. **В тексте промпта НЕ дублировать `--cref`, `--sref`, `--cw`** — MJ сам подцепит из drag-and-drop.
4. В Kling — MJ-кадр загружается как start-frame через Image-to-Video, длительность 5s/10s.

### Kling negative prompt (одинаковый для всех)
```
glossy, 3d render, cgi, octane, unreal engine, luxury commercial, perfume ad, car ad,
real estate render, fashion magazine cover, vogue editorial, polished, pristine, plastic skin,
overlit, studio lighting, HDR, oversharpened, AI gloss, smooth clean render, deformed limbs,
extra fingers, mutated hands, watermark, signature, text, logo, brand name, cartoon, anime,
oversaturated, flat lighting, generic AI face, tourist photo, instagram aesthetic, teal grade,
soft beauty light, model headshot, smiling model, posed, catalog, seamless background, cyclorama
```

### Kling параметры
- Aspect: 4:3 (мастер, кропится в 9:16/1:1) · Mode: Pro · Duration: 5s static-leaning / 10s with arc

### Sound design (опционально)
- **Музыка:** <жанр/референс под мир — phonk/drift HK · plugg/rage Tokyo · drum-n-bass Berlin · trap Paris · dark ambient post-apoc>
- **Diegetic:** <звуки мира — rain on wet asphalt, neon hum, distant traffic, train horn>
- **SFX:** <flash pop, chain rattle, fabric whip, boot stomp on wet ground>
```

---

## Поведение скилла

### Если на входе фото шмотки + описание бренда (ИДЕАЛЬНЫЙ КЕЙС)
1. **GARMENT DNA** — разбери фото.
2. **BRAND DNA** — декодируй бренд: tribe / decade / reference brands / mood word.
3. **Triangulation:** brand archetype matrix → 3 миров, shape × world → 3 миров. Пересечение = твой выбор. Если очевидно — выдавай. Если нет — покажи 2–3 на выбор буквой с одной строкой обоснования (к каждому миру — его коллизия одной фразой).
4. **⛔ COLLISION GATE:** сформулируй CORE COLLISION и назови ДВА сталкивающихся мира. Мир из шага 3 — только ПЕРВЫЙ из них; второй обязан быть ему чужим. Пока гейт не пройден — кадры не генерируются.
5. **Один мир + коллизия выбраны** → сгенерируй россыпь из 6 кадров (COLLISION ICON на пике, ≥2 кадра Mode B).

### Если на входе только фото шмотки (без бренда)
1. **GARMENT DNA**.
2. **Спроси бренд / мир / настроение** одной фразой («Это под какую марку или вайб? Если своя — опиши одной строкой: тёмный стрит / технический outdoor / Y2K / western / готик / sportcore / heritage-craft»).
   - Если пользователь говорит «выбери сам» — иди по shape × world матрице, выдай 2–3 на выбор.
3. Дальше как в идеальном кейсе.

### Если на входе фото шмотки + явный мир / явная локация
Пропусти triangulation, сразу к шагу 4 (россыпь). BRAND DNA всё равно полезно декодировать чтобы tone попасть точнее.

### Если на входе только описание / текст без фото
Спроси фото или хотя бы детальное описание вещи. **Без garment DNA скилл не работает** — выдаст generic стрит-сцены без зацепа.

### Если на входе несколько фото луков
Возьми ОДИН look как hero (или спроси какой), остальные = вариации в Кадре 4 (CREW) как комплементарные униформы мира.

### Если на входе фото лукбука / съёмки (не сток шмотки)
Извлеки GARMENT DNA из того, что носит модель, BRAND DNA из эстетики съёмки. Дальше как идеальный кейс.

---

## Чек-лист самопроверки (перед выдачей)

**⛔ СТОП-ГЕЙТ (провал любого пункта = россыпь НЕ выдаётся, пересборка с шага 4.5 — никакие красивые кадры это не компенсируют):**
- [ ] **CORE COLLISION сформулирована и называет ДВА чужих друг другу мира** (не один когерентный мир, подходящий бренду)
- [ ] **COLLISION ICON существует** — есть кадр, чей пересказ ≤5 слов звучит невозможно, и он стоит на позиции пика (3–5)
- [ ] **≥2 кадра Mode B** — будничный мир, где шмотка = невозможный гость
- [ ] **Хотя бы 3 из 6 пересказов вызывают «ЧТО?!»** — если все шесть читаются как shot-list фотосессии, это эдиториал, не ВАУ
- [ ] **Динамика интенсивности (W5b):** ≥2 тихих/deadpan-кадра, ≤2 одинаковой крупности+эмоции, один пик громкости — НЕ все кадры «орёт в линзу»

**Закон 0 (главное):**
- [ ] Каждый из 6 кадров — capture-формат прописан
- [ ] **Ноль запрещённых слов** (cinematic/luxury/8k/octane/pristine/editorial/golden hour/beauty light) в промптах
- [ ] `--style raw --s 50 --v 8.1` во всех
- [ ] **Ноль студии / seamless / catalog framing**
- [ ] Negative prompt с анти-глянец + анти-fashion-editorial терминами

**Garment + Brand:**
- [ ] GARMENT DNA разобран и записан
- [ ] GARMENT LOCK формула одинакова во всех 6 промптах
- [ ] **Шмотка полноценно видна минимум в 4 из 6 кадров**
- [ ] **В теле промптов НЕТ `--cref`, `--sref`, `--cw`** (только `--ar 4:3 --style raw --s 50 --v 8.1`)
- [ ] Workflow объясняет drag-and-drop референсов вручную в MJ
- [ ] **BRAND DNA декодирован** (tribe / decade / reference brands / mood word) — или явно спрошено если не задано
- [ ] **Triangulation выполнен**: brand archetype matrix × shape × world → выбранный мир обоснован одной строкой
- [ ] Если 2–3 мира равны — выданы буквами на выбор, не выбрано вслепую

**WOW-ДОКТРИНА (главный блок проверки):**
- [ ] **CORE COLLISION сформулирована одной фразой** и вызывает «ЧТО?» (W2)
- [ ] **Каждый кадр озаглавлен пересказом ≤5 слов**, и ни один пересказ не звучит как описание фотосессии (W1)
- [ ] **Невозможное снято deadpan** — камера не удивляется, эпичных ракурсов вокруг чуда нет (W3)
- [ ] **Есть кадр-соучастие** — POV / взгляд-зверь-жест прямо в линзу (W4)
- [ ] **Эскалация:** пик невозможного на позиции 3–5, НЕ в Кадре 1; Кадр 6 = послевкусие (W5)
- [ ] **Одна невозможность на кадр**, остальное подчёркнуто обычное (W6)
- [ ] **≥2 кадра проходят thumbnail-тест** (W7)
- [ ] **Лица не позируют** — рычат/ржут/орут/застыли (W9)
- [ ] **Ни один кадр не совпадает с AI-клише** (неоновый дождь, худи на закате, голуби slow-mo) (W10)
- [ ] **≥2 кадра Mode B** (будничный мир, шмотка = невозможный гость)

**SPECTACLE 2.0 (Слой 2.5):**
- [ ] Усилителей не больше двух; выбраны только те, что работают НА коллизию
- [ ] Если стихия выбрана — дословно во всех 6 и влияет на ткань/волосы/землю/действие
- [ ] Если тотем выбран — НЕ милый (mangy/scarred/bloodied), в 1–2 кадрах, с функцией в коллизии
- [ ] Абсурд-микродетали — максимум в 2 кадрах
- [ ] Тест слоя: убери стихию и тотем — ВАУ остаётся в коллизии?

**Россыпь (сборка):**
- [ ] **6 РАЗНЫХ кадров одного мира — НЕ 6 ракурсов одной позы**
- [ ] Style anchor идентичен во всех 6 (копипаст)
- [ ] Кадр 1 = HOOK (вариант A fisheye или B POV), намёк на коллизию без пика
- [ ] **COLLISION ICON присутствует** и стоит на позиции пика (3–5)
- [ ] POV IMPLICATION закрыт (Кадром 1-B или кадром из пула)
- [ ] Роли кадров 2–5 подобраны под коллизию и НЕ повторяют скелет прошлой россыпи
- [ ] **Лицо/тело в действии — ≥4 из 6 кадров**
- [ ] **Низкий угол / wide distortion — ≥3 из 6**; deadpan-кадры имеют право на хроникальный eye-level
- [ ] **Активная камера — ≥3 из 6 кадров**
- [ ] Кадр 6 (AFTERMATH) = послевкусие / DARK AFTERMATH, не пик

**Промпт-инжиниринг:**
- [ ] Якорь — первая фраза (L1); шмотка во второй
- [ ] Один сюр-якорь, без вложенных конструкций (L2)
- [ ] Two-subject через frame-left/right (L11)
- [ ] Свет: «что чем освещено» конкретно, один практический источник (L7)
- [ ] L12 — активный глагол на главного субъекта каждого кадра
- [ ] L12b — маркер пика (mid-step/snap/whip/throw) в каждом action-кадре
- [ ] L13 — Kling-промпт = временна́я дуга с 3 слоями движения + стихия реагирует
- [ ] L13a — действия конкретные (walks/throws/spits), не атмосферные
- [ ] L5 — никакого бренда/текста/лого в промптах

**Восемь тестов на каждый кадр:**
- [ ] Шмотка читается?
- [ ] Не каталог?
- [ ] Город, не студия?
- [ ] Низкий угол ИЛИ дикая оптика ИЛИ осознанный deadpan?
- [ ] Есть peak millisecond?
- [ ] Один практический источник?
- [ ] Captured (формат + raw + s 50)?
- [ ] WOW: пересказ ≤5 слов вызывает «ЧТО?» и не совпадает с AI-клише?

---

## Качество > количество

Лучше 4 сильных кадра, чем 6 разбавленных. Из 10 кандидатов прошли 4 — выдай 4 + честно скажи «остальные не прошли тесты, генерим заново или оставляем».

**Финальный тест перед отдачей** (четыре вопроса):
1. **«Это похоже на промо ORISS / ERROR SYSTEM / Rick Owens-tier стрит-бренда или на AI-каталог с Shein?»** Второе — переделай.
2. **«Если убрать шмотку из кадра — что-то останется?»** Если кадр работает без шмотки — она не была героем. Переписать.
3. **«Перескажи все 6 кадров подряд одной строкой каждый — хочется ли переслать этот список другу?»** Если список читается как shot-list фотосессии — коллизия не сработала (W1/W2).
4. **«Я видел эти кадры в AI-лентах?»** Модель в неоновом дожде, худи на закате, волк рядом с героем — уже видел. Переделай коллизию или смени медиум (PS2-движок / radical noir / found-footage POV) (W10).
