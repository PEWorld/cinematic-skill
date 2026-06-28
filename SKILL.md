---
name: cinema-prompt
description: Генерирует промпты для динамичного промо-ролика одежды по фото шмотки + описанию бренда. Вход — изображение вещи (куртка, штаны, аксессуар, луки) ± brand-DNA (своя марка / референс-бренды / mood). Скилл сам триангулирует «шмотка × бренд → мир» через brand-archetype matrix (16 архетипов: dark streetwear / techwear / western / goth / couture-avant / sportcore / heritage / pastoral / cyber / biker / hip-hop / bohemian / Y2K / domestic-soft / mountaincore / skater) и подбирает локацию из 9 семейств миров (city-grit · nature-grit · sacred-decay · industrial-isolated · subculture-sport · domestic-intimate · liminal-dreamcore · historic-decay · cultural-specific · climate-extreme). Выход — констелляция из 6 кадров одного мира с готовыми Midjourney + Kling промптами в эстетике «снято, не отрендерено» — НЕ глянцевая каталожная съёмка. Use this skill whenever the user uploads/links a clothing item or full look and asks for promo video ideas, lookbook scenes, brand campaign frames, Kling prompts, MJ prompts, или просит сцены / раскадровку / промо ролик / клип под одежду. Skill is pushy — trigger on ANY garment image with intent to make video content, even if the user не говорит «Kling» или «промпт».
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

### Шаг 3. Использовать --cref/--sref для лока
В Workflow генерации обязательно выдай:
- **`--cref <URL_фото_шмотки> --cw 100`** — приоритет персонажа/одежды
- **`--sref <URL_hero_кадра>`** — единый фильм-вайб для всех 6
- (опционально) **`--sref random`** для второго прохода если нужен дикий вариант

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
5. **Develop 6 shots constellation** — внутри мира сгенерируй 10+ потенциальных кадров (см. распределение ниже), отбери 6 сильнейших через тесты.

---

## Слой 2 — Семь тестов на каждый кадр

Каждый кадр проходит **все семь.** Не прошёл один — переписать или выкинуть.

### Тест 1 — Шмотка читается?
Видно силуэт + хотя бы одну фактурную деталь вещи? Если кадр можно опубликовать БЕЗ этой шмотки и ничего не изменится — провал. Шмотка должна быть **поводом для кадра**.

### Тест 2 — Не каталог?
«Модель стоит на белом фоне, eye-level, smiling, holding pose» — провал. Должно читаться как **бэкстейдж со съёмки** или **украденный фотоснэп** (Закон 0).

### Тест 3 — Город, не студия?
«Где это снято?» — должен быть конкретный реальный ответ (rooftop в Mong Kok / переход Shibuya / Paris Pere Lachaise alley). Ответ «не знаю, какая-то локация» = провал.

### Тест 4 — Низкий угол ИЛИ дикая оптика?
Eye-level 50mm + frontal = заставка стока. Минимум один из: **низкий tilt-up / fisheye / wide-angle distortion / extreme close-up / overhead / split / dutch / handheld lurch.** Стандартный угол без оправдания — провал.

### Тест 5 — Есть peak millisecond?
Не «модель стоит», а «модель MID-STEP, fabric whipping, head snapping, hand thrusting в линзу». Хотя бы один глагол на главного субъекта (см. L12). Нет глагола — переписать.

### Тест 6 — Один практический источник?
В промпте указан КОНКРЕТНЫЙ источник: `harsh on-camera flash` / `single sodium streetlamp from frame-right` / `neon kanji sign spilling magenta on wet ground` / `headlights of oncoming car`. Описание «moody lighting» — провал.

### Тест 7 — Captured?
Указан capture-формат (плёнка / флэш / CCTV / bodycam / FMV) и `--style raw --s 50`. Нет — провал. См. Закон 0.

**Если из 10 кадров прошли только 4 — выдай 4.** Не разбавляй.

---

## Слой 3 — Распределение 6 кадров (констелляция)

6 кадров покрывают разные роли. **НЕ 6 ракурсов одного манекена.**

### Кадр 1 — HERO HOOK (конфронтация, fisheye/wide)
Самый сильный кадр россыпи. **Низкий угол снизу + fisheye / 14–20mm wide.** Модель **наступает на камеру**, шмотка доминирует нижние 2/3, лицо/торс в линзе. Аналог HK chain-mesh реф 1.
- Camera: aggressive handheld push-in, low-angle tilt-up, fisheye barrel distortion
- Garment: **silhouette + texture доминируют**
- Action: lunges / strides into lens / thrusts hand toward camera / mid-step boot-stomp

### Кадр 2 — GARMENT-AS-HERO (объект-первый план)
Шмотка крупно как объект: **низ кадра — текстура/деталь вещи занимает 60–80%**, фон — мир в bokeh. Аналог HK split нижний полу-кадр.
- Camera: low static macro-wide, 35mm
- Frame: garment fills lower frame, model torso/silhouette сверху обрезана
- Detail: textile / hardware / patch / hem dragging / chain spilling

### Кадр 3 — FACE / TORSO in motion
Лицо или торс героя крупно в движении. Не позирует — **что-то делает**: smoking, drinking, throwing sign, looking back over shoulder mid-turn, hood pulled mid-gesture.
- Camera: medium handheld, 35mm
- Lighting: hard practical (harsh flash / single sodium / neon spill)
- Garment partially in frame: collar / hood / chain catching light

### Кадр 4 — CREW / GROUP power-stance
Двойник или 3–5 фигур one shot. Plekhom-to-shoulder / V-formation / sprawled на ступенях. Аналог Paris crew + Y2K Japan trio.
- Camera: low-mid wide-angle, 24mm, perspective distortion at edges
- Garment lock: КАЖДАЯ фигура в той же шмотке ИЛИ один герой в шмотке + 2–3 фигуры в комплементарной униформе мира
- Action: hand signs / mid-turn / синхронный шаг

### Кадр 5 — WORLD WIDE (место, в котором шмотка живёт)
Establishing мира — но **с фигурой внутри**, не пустой пейзаж. Архитектура / переулок / rooftop / underpass. Силуэт героя где-то в кадре (мелкий или средний), но шмотка узнаваема по силуэту.
- Camera: wide / ultra-wide, 16–24mm
- Composition: leading lines (rail / wire / fence / road) + figure
- Anti-poster test: если кадр без человека был бы desktop wallpaper — добавь движение или absurd.

### Кадр 6 — DETAIL / PROP / STILL-IN-MOTION (texture + action)
Деталь, поднятая до образа: рука с цепью, ботинок в луже, hem дрегается по асфальту, рука зажигает зажигалку, цепь падает на бетон. **Должно быть движение.** Не натюрморт.
- Camera: macro / overhead / dutch
- Required: РУКИ ИЛИ ТЕЛО в кадре (без человеческого присутствия = реклама).
- Light: hard practical, harsh shadow

### Квоты на россыпь
- **Garment fully readable: минимум в 4 из 6 кадров.**
- **Лицо/тело в действии: минимум в 5 из 6 кадров.**
- **Низкий угол или wide distortion: минимум в 4 из 6 кадров.**
- **Пустые luxury-интерьеры: 0.**
- **Все 6 — Закон 0 (capture-формат + грязь).**
- **Все 6 — идентичный Style anchor (копипаст).**
- **Минимум 4 из 6 — активная камера** (handheld, push-in, whip, lurch). Locked-off — для still-life деталей.

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

В выводе всегда указывай `--cref <url> --cw 100`.

### L5 — Никакого бренда / рендеренного текста в кадре
Бренд накладывается в After Effects. **Не закладывай ни текст, ни лого, ни «надпись на куртке».** Принты/паттерны на одежде — ОК (это часть garment DNA), но не name/logotype.

### L6 — Лимит сложности на кадр
Максимум 3 нарративных элемента: субъект + действие + одна деталь среды. Остальное — свет/фактура/style.
**L6a — MJ не считает выше 3–4.** Для групп: `a row of approximately five figures shoulder-to-shoulder`.

### L7 — Светотеневые коллизии: укажи явно
«Warm vs cold» в общем виде модель игнорирует. Конкретно:
✅ «Harsh sodium streetlamp rakes the model's face from frame-left. Cool blue dusk on the wet asphalt frame-right. Crushed black shadow under the coat hem.»

### L8 — Кадр 1 = HERO HOOK = конфронтация
Открывающий — самый агрессивный: low-angle fisheye, шмотка доминирует, модель наступает на камеру. Establishing / wide world — на кадр 5.

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

### L9b — Оптика под мир
- **Кадр 1 (HERO HOOK):** fisheye 8–14mm ИЛИ wide 20mm с barrel distortion.
- **Кадр 4 (CREW):** wide 24mm, perspective distortion at edges.
- **Кадр 5 (WORLD WIDE):** ultra-wide 14–20mm или telephoto 85mm для compression.
- **Кадры 2, 3, 6:** 35mm дефолт, иногда 50mm.
- **Никакого 85mm beauty-shot** — это reads как perfume ad.

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

**🔒 GARMENT LOCK (копируется во ВСЕ 6 кадров — НЕ варьировать):**
> "<тип> with <силуэт + deco>, <цвет/материал>, <visual hook>"

**🔒 Style anchor (копируется во ВСЕ 6 кадров — НЕ варьировать):**
> Style: <ОДИН capture-формат из меню>, <ОДИН grade>, heavy grain, slight motion blur, imperfect focus, looks like real found street photography — not a render, not editorial.

**🔒 Character lock (если есть сквозной герой):**
> <возраст + национальность/раса + причёска + опознавательная деталь — дословно во все кадры с героем>

---

### Россыпь (6 кадров)

#### Кадр 1 — HERO HOOK (low-angle fisheye, конфронтация)
- **Subject move:** <что делает, активный глагол>
- **MJ prompt:**
  ```
  Low-angle fisheye 10mm tilt-up. <subject + character lock + GARMENT LOCK дословно + active verb>. <Location + one practical light>. <STYLE ANCHOR дословно>. --ar 4:3 --style raw --s 50 --v 8.1 --cref <url> --cw 100 --sref <url>
  ```
- **Kling prompt (5s):**
  ```
  <Anchor start state.> <BEAT 1: subject launches action.> <BEAT 2: peak unfolds via "as/the instant" + garment lives + environment reacts.> Camera: <movement synced to action>. Lighting: <practical source + how it flicks>. <STYLE ANCHOR verbatim>.
  ```
- **Camera/Duration:** Low-angle handheld push-in / 5s

#### Кадр 2 — GARMENT-AS-HERO (low static, deco крупно)
[same structure]

#### Кадр 3 — FACE/TORSO in motion (medium handheld, character beat)
[same structure]

#### Кадр 4 — CREW power-stance (wide 24mm, group)
[same structure]

#### Кадр 5 — WORLD WIDE (ultra-wide, figure inside)
[same structure]

#### Кадр 6 — DETAIL/PROP still-in-motion (macro/overhead, hands required)
[same structure]

---

### Workflow генерации
1. Сначала **Кадр 1 (HERO HOOK)** в MJ — он задаёт фактуру всей россыпи.
2. URL Кадра 1 → во все остальные как `--sref <url>` (единый фильм).
3. URL фото шмотки → во все как `--cref <url> --cw 100` (garment lock).
4. Сквозной герой → второй `--cref <url>` человека-маркера.
5. В Kling — MJ-кадр как start-frame через Image-to-Video, длительность 5s/10s.

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
3. **Triangulation:** brand archetype matrix → 3 миров, shape × world → 3 миров. Пересечение = твой выбор. Если очевидно — выдавай. Если нет — покажи 2–3 на выбор буквой с одной строкой обоснования.
4. **Один мир выбран** → сгенерируй россыпь из 6 кадров.

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
- [ ] `--cref <url шмотки> --cw 100` указан в Workflow
- [ ] **BRAND DNA декодирован** (tribe / decade / reference brands / mood word) — или явно спрошено если не задано
- [ ] **Triangulation выполнен**: brand archetype matrix × shape × world → выбранный мир обоснован одной строкой
- [ ] Если 2–3 мира равны — выданы буквами на выбор, не выбрано вслепую

**Россыпь:**
- [ ] **6 РАЗНЫХ кадров одного мира — НЕ 6 ракурсов одной позы**
- [ ] Один мир выбран и обоснован
- [ ] Style anchor идентичен во всех 6 (копипаст)
- [ ] **Лицо/тело в действии — ≥5 из 6 кадров**
- [ ] **Низкий угол / wide distortion — ≥4 из 6 кадров**
- [ ] **Активная камера — ≥4 из 6 кадров**
- [ ] Кадр 1 = HERO HOOK = low-angle fisheye конфронтация
- [ ] Кадр 4 (CREW) — все фигуры в garment lock или комплементарной униформе
- [ ] Кадр 5 (WORLD WIDE) — пройден anti-poster test (есть фигура / есть движение / есть absurd)
- [ ] Кадр 6 (DETAIL) — РУКИ или ТЕЛО в кадре (не натюрморт)

**Промпт-инжиниринг:**
- [ ] Якорь — первая фраза (L1); шмотка во второй
- [ ] Один сюр-якорь, без вложенных конструкций (L2)
- [ ] Two-subject через frame-left/right (L11)
- [ ] Свет: «что чем освещено» конкретно, один практический источник (L7)
- [ ] L12 — активный глагол на главного субъекта каждого кадра
- [ ] L12b — маркер пика (mid-step/snap/whip/throw) в каждом action-кадре
- [ ] L13 — Kling-промпт = временна́я дуга с 3 слоями движения, не подпись к стопке
- [ ] L13a — действия конкретные (walks/throws/spits), не атмосферные
- [ ] L5 — никакого бренда/текста/лого в промптах
- [ ] Workflow (sref/cref) выдан полностью

**Семь тестов на каждый кадр:**
- [ ] Шмотка читается?
- [ ] Не каталог?
- [ ] Город, не студия?
- [ ] Низкий угол ИЛИ дикая оптика?
- [ ] Есть peak millisecond?
- [ ] Один практический источник?
- [ ] Captured (формат + raw + s 50)?

---

## Качество > количество

Лучше 4 сильных кадра, чем 6 разбавленных. Из 10 кандидатов прошли 4 — выдай 4 + честно скажи «остальные не прошли тесты, генерим заново или оставляем».

**Финальный тест перед отдачей** (два вопроса):
1. **«Это похоже на промо ORISS / ERROR SYSTEM / Rick Owens-tier стрит-бренда или на AI-каталог с Shein?»** Второе — переделай.
2. **«Если убрать шмотку из кадра — что-то останется?»** Если кадр работает без шмотки — она не была героем. Переписать.
