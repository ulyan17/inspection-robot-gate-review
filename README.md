# Inspection Robot MVP for an Oil and Gas Facility: Stage-Gate Go/No-Go Review

A hands-on assignment. Your team acts as the review committee at stage gate 4 (В4). Four vendors have proposed an inspection robot for a pumping station. Using recorded test runs, you assess each vendor and decide which one, if any, may proceed to a pilot at a real facility.

Nothing needs to be installed or run. You need a web browser and Word (or Google Docs).

The test materials and the protocol template are in Russian. Russian labels are quoted below exactly as they appear, with an English translation in parentheses.

<table>
<tr>
<td width="25%"><a href="evidence/A/README.md"><img src="docs/img/vendor-A.gif" alt="Vendor A"></a><br><b>A «Быстрый обход» (Fast Sweep)</b></td>
<td width="25%"><a href="evidence/B/README.md"><img src="docs/img/vendor-B.gif" alt="Vendor B"></a><br><b>B «Надёжный» (Reliable)</b></td>
<td width="25%"><a href="evidence/C/README.md"><img src="docs/img/vendor-C.gif" alt="Vendor C"></a><br><b>C «Сбалансированный» (Balanced)</b></td>
<td width="25%"><a href="evidence/D/README.md"><img src="docs/img/vendor-D.gif" alt="Vendor D"></a><br><b>D «Оптимальный маршрут» (Optimal Route)</b></td>
</tr>
</table>

In the Russian materials the vendors are labelled А, Б, В, Г. They correspond to A, B, C, D here and to the folders `evidence/A … D`.

---

## Assignment

### What to do

1. Download the protocol template: **[gate_protocol.docx](https://github.com/ulyan17/inspection-robot-gate-review/raw/main/submission/gate_protocol.docx)**.
2. Fill it in using the test materials in this repository (links below).
3. Submit the completed file to the instructor.
4. Defend the committee's decision in 2 minutes.

Time for filling in the protocol: 42 minutes. Teams of 3–4 people.

### Where the materials are

| Item | Location | Contents |
|---|---|---|
| Protocol template | [submission/gate_protocol.docx](https://github.com/ulyan17/inspection-robot-gate-review/raw/main/submission/gate_protocol.docx) | the 7 pages you fill in |
| Vendor claims | [variants/VENDORS.md](variants/VENDORS.md) | what each vendor promises |
| Vendor A materials | [evidence/A/README.md](evidence/A/README.md) | animation, maps, log, report, sensor readings, code |
| Vendor B materials | [evidence/B/README.md](evidence/B/README.md) | same |
| Vendor C materials | [evidence/C/README.md](evidence/C/README.md) | same |
| Vendor D materials | [evidence/D/README.md](evidence/D/README.md) | same |
| Summary, 5 scenarios | [evidence/compare.md](evidence/compare.md) | all vendors on the same 5 acceptance scenarios |
| Summary, 30 scenarios | [evidence/compare_30.md](evidence/compare_30.md) | all vendors on 30 random scenarios |
| Checkpoint specs, glare vs overheating | [evidence/README.md](evidence/README.md) | pressure range and temperature limit for checkpoints K1–K6 |
| Gate criteria | [Gate criteria](#gate-criteria) section and [configs/gate_thresholds.json](configs/gate_thresholds.json) | thresholds used for the decision |

### How a vendor page is organised

Every page `evidence/A … D` has the same sections:

| Section | Contents |
|---|---|
| «Заявление подрядчика» (vendor claim) | what the vendor promises |
| «1. Демо-прогон (seed 19)» (demo run) | animation and final map of one run |
| «2. Приёмка: 5 сценариев» (acceptance, 5 scenarios) | maps for scenarios seed 101, 102, 103, 104, 105 |
| «3. Код подрядчика» (vendor code) | the file with the robot's settings |

Under each map there are three collapsible blocks. Click a block title to expand it:

| Block | Contents |
|---|---|
| «Лог миссии и итог» (mission log and summary) | the robot's messages during the mission, the result for each gate criterion, and the line «Истина этого seed» (ground truth) showing where the anomaly actually was |
| «Отчёт подрядчика» (vendor report) | what the robot reported: the line «Покрытие: N/6, аномалий: N, тревог: N» (coverage, anomalies, alarms), a table by checkpoint, a list of alarms («Тревоги») |
| «Замеры датчиков» (sensor readings) | every frame: pressure, normal pressure range, maximum temperature, number of pixels above the limit. The marks «вне нормы» (out of range) and «выше предела» (above limit) flag deviations |

Checkpoint colours on maps and animations: green — normal, orange — alarm, grey — not inspected. Red marks on the route are steps inside the Ex zone.

---

## Procedure

### Step 1. Preparation — 2 minutes

1. Download [gate_protocol.docx](https://github.com/ulyan17/inspection-robot-gate-review/raw/main/submission/gate_protocol.docx) and open it in Word or Google Docs.
2. Assign roles:
   - presenter — gives the defence;
   - data analyst — works with maps, logs, sensor readings and code;
   - protocol owner — fills in the template.
3. Fill in **page 1**: team, group, date, names by role.

### Step 2. Demo run — 9 minutes

Open the pages for [A](evidence/A/README.md), [B](evidence/B/README.md), [C](evidence/C/README.md), [D](evidence/D/README.md) in turn, section «1. Демо-прогон (seed 19)». About 2 minutes per vendor.

For each vendor:

1. Read the claim at the top of the page.
2. Watch the animation: route, checkpoint colours, marks inside the Ex zone.
3. Fill in the vendor's row in **Table 1** (template page 2):

| Table 1 column | Source |
|---|---|
| «Точек проверено из 6» (checkpoints inspected out of 6) | block «Отчёт подрядчика», line «Покрытие: N/6» |
| «Тревог всего» (total alarms) | block «Отчёт подрядчика», same line, «тревог: N» |
| «Тревога на точке аномалии (да/нет)» (alarm at the anomaly checkpoint, yes/no) | block «Лог миссии и итог», line «Истина этого seed: аномалия на K…»; compare with the alarm list in the report |
| «Время миссии, с» (mission time, s) | block «Лог миссии и итог», line «Время миссии, с» |
| «Шагов в Ex-зоне» (steps in the Ex zone) | block «Лог миссии и итог», line «Нарушения Ex-зон, шагов» |
| «Ручных вмешательств» (manual interventions) | block «Лог миссии и итог», line «Ручные вмешательства» |

4. Compare the result with the claim and write one or two observations in the field **«Измерения показали»** (measurements showed) on that vendor's page (template pages 3–6).

At the end of the step, fill in the field below Table 1: **«Чьё заявление не подтвердилось уже на демо-прогоне и в чём»** (whose claim was already refuted in the demo run, and how).

### Step 3. Summaries for 5 and 30 scenarios — 8 minutes

Open [evidence/compare.md](evidence/compare.md) and [evidence/compare_30.md](evidence/compare_30.md). Fill in **Table 2** (template page 2):

| Table 2 column | Source |
|---|---|
| «Все обязательные: 5 сценариев» (all mandatory criteria met, 5 scenarios) | `compare.md`, section 1, last row «Все обязательные сразу» |
| «Все обязательные: 30 сценариев» (all mandatory criteria met, 30 scenarios) | `compare_30.md`, section 1, same row |
| «Проваленные обязательные критерии и доля прогонов (5 / 30)» (failed mandatory criteria and share of runs) | section 1 of both files: rows of type «обяз.» (mandatory) where the vendor has ❌; write the criterion name and its share on 5 and on 30 scenarios |
| «Номера проваленных сценариев (seed 101–105)» (failed scenario numbers) | `compare.md`, section 3 «По каждому сценарию» (per scenario), the vendor's table: rows with ❌ in the last column «обязательные» |

Then:
1. Compare the results on 5 and on 30 scenarios. Note the vendor whose results differ noticeably.
2. Add the numbers from Table 2 to each vendor's **«Измерения показали»** field.

### Step 4. Root-cause analysis — 15 minutes

About 4 minutes per vendor. Vendors can be split among team members.

For each vendor, on its page:

1. Pick a failed scenario from Table 2. Write its number in the field **«Проверенный сценарий»** (scenario examined).
2. In section «2. Приёмка», open the map of that scenario: which checkpoints are grey or orange, whether there are marks in the Ex zone, where the route goes.
3. Expand **«Лог миссии и итог»**: which messages repeat, which criterion failed, where the anomaly actually was.
4. Expand **«Отчёт подрядчика»**: what the robot reported for each checkpoint, and whether the alarms match the ground truth.
5. Expand **«Замеры датчиков»** and check:
   - how many frames were taken at each checkpoint;
   - whether any frames are marked «кадр смазан» (blurred frame, no gauge reading);
   - which pressure values are marked «вне нормы» (out of range);
   - how many pixels are «выше предела» (above limit) and in how many consecutive frames. One pixel in one frame is glare. A spot repeated across several frames is overheating. See the example in [evidence/README.md](evidence/README.md), section «Блик или перегрев» (glare or overheating).
6. In section **«3. Код подрядчика»**, find the settings at the top of the file: number of readings per checkpoint, retries for an unreachable checkpoint, flags. Determine which setting explains what you see in the data.
7. Fill in on the vendor's page:
   - **«Причина»** (cause) — the failure mechanism in one or two sentences;
   - **«Доказательство 1: данные»** (evidence 1: data) — map, log or sensor table: source, what it shows, conclusion;
   - **«Доказательство 2: код»** (evidence 2: code) — which setting and how it explains the result.

Where to start looking (directions, not answers):

| | What to check |
|---|---|
| A | the state of checkpoint K2 on the maps; how many frames are taken per checkpoint in the sensor table; whether alarms match the ground truth |
| B | how many times the log mentions calling the operator; what makes up the mission time |
| C | which of the five scenarios failed; which alarms in it are false and which gauge values they came from |
| D | the part of the route next to the Ex zone on the maps; the code setting that affects the route |

### Step 5. Decisions — 8 minutes

1. On each vendor's page, mark **one** decision: GO, GO С УСЛОВИЯМИ (GO with conditions), HOLD, RECYCLE or KILL. See [Choosing a decision](#choosing-a-decision).
2. Fill in **«Что исправить»** (what to fix) — the condition under which the committee would say GO.
3. On **page 7**:
   - mark the pilot candidate or «НИКОГО» (none);
   - write the justification and admission conditions: 3–5 sentences with numbers from Tables 1 and 2;
   - fill in the table of the two main pilot risks at a real facility: risk, likelihood (Н/С/В — low/medium/high), consequences, mitigation;
   - write what you would change or add to the [gate criteria](#gate-criteria) for a real station.
4. Leave «Оценка преподавателя» (instructor's assessment) blank.

### Step 6. Check before submitting

- [ ] page 1 is filled in;
- [ ] Table 1 has four rows with all columns filled;
- [ ] Table 2 has four rows, failed scenario numbers are listed;
- [ ] every vendor page has all fields filled and exactly one decision marked;
- [ ] every evidence field names its source: vendor page, scenario number, block or line of code;
- [ ] page 7 has one option marked, a justification with numbers, two risks and a proposal on thresholds.

### How to submit

1. Save the file as `Протокол_<team>.docx`.
2. Send it to the instructor as instructed.

To mark a decision, replace ☐ with ☒ or highlight the option. If you work in Google Docs, submit as .docx or PDF.

---

## Answer requirements

### Measurements

State numbers. Example for a hypothetical vendor X, not one of the four:

> All mandatory criteria met in 2 of 5 scenarios and in 40% of 30. Mission time criterion failed: 410–450 s against a 360 s threshold.

### Evidence

Format: source, what it shows, conclusion.

| Acceptable | Not acceptable |
|---|---|
| "Vendor X materials, map seed 103: checkpoint K4 is grey. The robot did not return to the unreachable checkpoint." | "Bad algorithm." |
| "Vendor X code: `PARK_AT_DOCK = True`. After every checkpoint the robot drives back to the charger." | "Probably a bug in the code." |
| "Vendor X readings, seed 102: eight consecutive frames at K3. The robot gets stuck at one checkpoint." | "It was slow." |

### Choosing a decision

| Decision | When it applies |
|---|---|
| GO | all mandatory criteria are met consistently, on both 5 and 30 scenarios; no significant risks |
| GO WITH CONDITIONS | a rare failure is explained and covered by a pilot condition: restricted zone, additional check, time limit |
| HOLD | not enough data to decide, or an external condition is required |
| RECYCLE | the defect is found and fixable; the vendor reworks the MVP and passes the gate again |
| KILL | the approach is unsuitable, the defect is dangerous, or the vendor concealed it |

A mandatory criterion that fails regularly rules out GO. The justification is assessed, not the vendor chosen: "admit none" is also a valid decision.

### Common mistakes

- assessment without numbers;
- cause without a source;
- decision based on a single run without comparing 5 and 30 scenarios;
- GO despite a failed mandatory criterion, without explanation;
- several decisions marked, or none;
- empty fields.

---

## Gate criteria

KPIs are computed from the simulator's ground truth, not from the vendor's report. Thresholds are in [configs/gate_thresholds.json](configs/gate_thresholds.json).

| Criterion (as in the materials) | Threshold | Type |
|---|---|---|
| Ex zone violations («Нарушения Ex-зон») | 0 steps | mandatory |
| Checkpoint coverage («Покрытие точек контроля») | at least 90% | mandatory |
| Anomaly found («Аномалия найдена») | yes | mandatory |
| False alarms («Ложные тревоги») | at most 1 per run | mandatory |
| Manual interventions («Ручные вмешательства») | 0 | mandatory |
| Run failure («Сбой запуска») | none | mandatory |
| Reading accuracy («Точность показаний») | at least 80% of checkpoints within ±0.15 bar | desirable |
| Mission time («Время миссии») | at most 360 s | desirable |

## Test site

Pumping station, 40 × 30 m.

<img src="docs/img/world.png" width="720" alt="Pumping station map: checkpoints K1–K6, Ex zone, vehicle on the access road">

| Element | Description |
|---|---|
| K1–K6 | checkpoints: pressure gauge, 8 × 8 pixel thermal camera, tag. Each checkpoint has a spec: normal pressure range and temperature limit |
| Ex zone (hatched) | explosive atmosphere zone around the drain tank; entry is prohibited |
| Vehicle (orange rectangle) | may block the dead end with checkpoint K2 at the start of the mission |
| DOCK | charging station, start and finish |
| Anomaly | one per scenario; its location and type depend on the scenario number (seed) |

The sensors produce noise: blurred frames without a gauge reading, gauge outliers, thermal glare.

---

## Grading

| Block | Points | Criteria |
|---|---:|---|
| Preparation | 5 | page 1 filled in |
| Measurements | 15 | Tables 1 and 2 filled in and consistent with the data; numbers in «Измерения показали» |
| Root-cause analysis | 30 | 7.5 per vendor: correct cause (3), evidence from data (2.5), evidence from code (2) |
| Decisions | 15 | decisions consistent with measurements (8), pilot choice justified (7) |
| Risks and thresholds | 10 | risks relate to a real facility (5), threshold proposal justified (5) |
| Defence | 25 | decision based on numbers (10), answer to the committee's question (10), within 2 minutes (5) |
| Total | 100 | |

## Defence

2 minutes per team:

1. pilot candidate, or rejection of all;
2. which numbers the decision is based on: 5 scenarios and 30;
3. the main finding and its evidence;
4. the main pilot risk and mitigation.

One question from the committee follows.

---

## Homework

Done at home with the project installed and running: reproduce the session, improve your own robot in the `student/` folder and port it to ROS 2. Guide: [homework/README.md](homework/README.md).

## Troubleshooting

| Problem | Solution |
|---|---|
| The template link does not download | open [submission/gate_protocol.docx](submission/gate_protocol.docx) and click Download raw file on the right |
| No Word | Google Docs: File → Open → Upload |
| The animation does not load | reload the page; the final map is right below the animation |
| Blocks do not expand | click the block title |
| ☐ cannot be changed to ☒ | highlight the chosen option or make it bold |
