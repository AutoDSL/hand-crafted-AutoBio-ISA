### Types

| Type | Example           | Unit                             |
| ---- | ----------------- | -------------------------------- |
| NUM  | 16                |                                  |
| BOOL | False             |                                  |
| STR  | “a small scissor” |                                  |
| TEMP | 37C               | C,F or roomtemp（RT）            |
| TIME | 30min             | sec, min, hour, day or overnight |
| VOL  | 20ul              | ul, ml, l                        |
| CONC | 1g/L              | 质量单位 or 物质的量单位/VOL     |
|      |                   |                                  |

- RANGE怎么设置？NUM，TEMP，TIME，VOL，CONC都可以替换为对应的RANGE类型

### 1. Remove 去除

- **Remove** **aliquot of cells(r1)** **for counting(purpose)**.
- **Remove** the **colon(r1)** at **the most distal position accessible(source)** with **a small scissor(device) (sample any organ or tissue of interest for further studies)(notice).**
- **Remove** **residual hemocytes(r1)** by **centrifuging at 150 x g at room temperature for 10 min(method)**.

归纳：

1. Remove ? from ? （with/using） ？by？for？
2. 常见Remove supernatant+suspend/resuspend

同义词：

| Argument | Type     | Commet |
| -------- | -------- | ------ |
| r1       | REQ\|REG |        |
| source   | OPT\|STR |        |
| device   | OPT\|STR |        |
| purpose  | OPT\|STR |        |
| method   | OPT\|STR |        |
| notice   | OPT\|STR |        |
| r0       | RET\|REG |        |

### 2. Add 加入

- **Add 400 ul of methanol(r1)**,to **the protein solution(r2)**.
- **Add 4 ml of PBS(r1)** in **an empty ultra-low attachment dish(r2)**.
- **Add 10% volume of 3M sodium acetate, pH 5.2(r1)**

总结：

1. 加入多种试剂应当分多条ADD

同义词：apply，load，pour

| Argument | Type     | Commet          |
| -------- | -------- | --------------- |
| r1       | REQ\|REG | 待加入试剂      |
| r2       | REQ\|REG | 被加入试剂/容器 |
| device   | OPT\|STR |                 |
| r0       | RET\|REG |                 |

### 3. Transfer 转移

例句：

- **Transfer** the **cryo vials(r1)** from **the -80°C freezer(source)** into **a pre-equilibrated CoolBox CFT30 containing a green freezing cartridge inside it(destination)**.
- **Transfer** **1 µl(volume)** of **PBS with your target single cell(r1)** into **the bottom of a PCR tube carefully(destination)**.
- **Transfer** the **supernatant(component)** to **a new eppendorf(destination)**.
- **Pipette** the **conjugation reaction mixture(r1)** onto **the column(destination)**.

总结：

1. transfer有时转移全部，有时只转移一部分（如上清液，或一部分体积）。后者使用component或volume表分割
2. destionation前的介词也应当一并保留，避免语义缺失
3. Pipette=Transfer by pipetting

同义词：
Pipette

| Argument    | Type     | Commet |
| ----------- | -------- | ------ |
| r1          | REQ\|REG |        |
| source      | OPT\|STR |        |
| destination | REQ\|STR |        |
| component   | OPT\|STR |        |
| volume      | OPT\|VOL |        |
| notice      | OPT\|STR |        |
| r0          | RET\|REG |        |

### 4. Incubate 孵育

例句：

- **Incubate** at room **temperature(temperature)** for **30min(time)** in **the dark(environment)**.
- **Incubate** the **washed RBC(r1)** with **equal volume of bacteria(r2)** at **room temperature(temperature)** **under steady rotation at 6 rpm(notice)**.
- **Incubate** the **cells(r1)** again for **3 more hours(time)** at **BOD incubator(device)**.
- Incubate the reaction in **thermocycler(device)**:  **1 cycle at 95°C for 5 min, 40 cycles of 95°C for 1 min, 60°C for 30 s and 72°C for 15 s, 1 cycle 72°C for 5 min and hold at 8°C(thermoProgram)**.

总结：



| Argument      | Type           | Commet                             |
| ------------- | -------------- | ---------------------------------- |
| r1            | REQ\|REG       |                                    |
| r2            | OPT\|List<REG> | 孵育额外加入的试剂                 |
| temperature   | REQ\|TEMP      | defult=roomtemp                    |
| time          | OPT\|TIME      |                                    |
| environment   | OPT\|STR       |                                    |
| device        | OPT\|STR       |                                    |
| thermoProgram | OPT\|STR       | device=thermocycler时，此参数为REQ |
| notice        | OPT\|STR       |                                    |
| r0            | RET\|REG       |                                    |

### 5. Suspend 悬浮

例句：

- **Suspend** by **gentle trituration 100 times(mothod)** **without bubbles(notice)**
- **Suspend** **1-5 million cells(r1)** in the **labeling medium(r2)** for **10 min(time)** at **37 ˚C(temperature)** **(refer to step 1 in the protocol for mammalian cell cultures for labeling medium preparation)(notice)**.
- **Resuspend** the **cell pellet(r1)** at a density of **3.0 x 10-6cells/mL(targetConc)** in **freezing medium(r2)**.

总结：

1. resuspend常有targetConc参数，但并未指出使用何装置控制浓度？
2. 悬浮介质有时缺失，此时如何判断应当使用什么试剂？

| Argument   | Type      | Commet |
| ---------- | --------- | ------ |
| r1         | REQ\|REG  |        |
| r2         | OPT\|REG  | 悬浮液 |
| targetConc | OPT\|CONC |        |
| notice     | OPT\|STR  |        |
| r0         | RET\|REG  |        |

### 6. Plate

例句：

- **Plate** the **transformed bacterial cells(r1)** on **agar plates containing Carbenicillin(r2)**.

- **Plate** **5x10-6 monocytes(r1)** in **5 ml MDDC culture media in a 10 cm plate with recombinant human GM-CSF at 10 ng\/ml and recombinant human IL-4 at 50 ng\/ml(r2)**
- Plate preparation: **20 μl of 100 mM IPTG and 70 μl of 2% Bluo-Gal(r1)** were **spread** on **LB plate containing kanamycin \\(final concentration of 50 μg\/ml) and gentamycin \\(final concentration of 7 μg\/ml)(r2)**.

总结：

1. Plate多数情况是将cells铺在plate/dish中，少数情况铺设在试剂中

同义词：

spread

| Argument | Type     | Commet   |
| -------- | -------- | -------- |
| r1       | REQ\|REG |          |
| r2       | OPT\|REG | 辅助试剂 |
| r0       | RET\|REG |          |

### 7. Collect

例句：

- **Collect** **cells(component)** by **centrifugation (200 g, 5 min, room temperature)(method)**
- **Collect** **10 ml whole blood(component)** by **peripheral venipuncture(method)** using **a 21 gauge butterfly needle(device)** into **a K2EDTA vacutainer tube(destination)**.
- **Collect** **flow(component)** through for **analysis(purpose)**.
- **Harvest** the **hiPSCs(component)** with **a Cell Scraper(device)**.
- **Harvest** **sperm(component)** from the **caudal epididymides of a >8 week-old B6D2F1 male(r1)**

总结：

1. 通过离心进行collect时，往往不会显式指出目标容器。
2. Collect every 200 mL into a separate Eppendorf tube, for a total of 4 samples collected (E1-E4).一起收集4管，应当翻译为四个Collect语句？
3. 收集操作的源试剂（如提取细胞的溶液，跟在from后）往往不显示指出。

同义词：

Harvest

| Argument    | Type     | Commet       |
| ----------- | -------- | ------------ |
| r0          | REQ\|REG |              |
| component   | REQ\|STR | 要收集的部分 |
| destination | OPT\|STR |              |
| volume      | OPT\|VOL |              |
| purpose     | OPT\|STR |              |
| r0          | RET\|REG |              |

### 8. Mix

例句：

- **Mix** by **pipetting carefully(method)** to **make the stock of the single cell suspension(purpose)**.
- **Mix** **20 μl of 10× PCR buffer(r1[0]), 2 μl of 250 mM MgCl-2(r1[1), 10 μl of 5 mM dNTPs(r1[2]), 1 μl of 100 μM mDNA-F2 primer(r1[3]), 1 μl of 100 μM mDNA-R3 primer(r1[4]), 2 μl of Taq DNA polymerase(r1[5]), 5 μl of the 1st PCR product from step 71(r1[6])**, and **159 μl of RNase- free water(r1[7])** in a **200-μl PCR tubes(container)**.
- **Mix** well by **pipetting up and down(method)** **at least 10 times(repeat)**.

总结：

1. Mix有时候是充分混合前面几部已经加入的试剂，有的时候混入新的试剂（如何处理？r1设定为List）。
2. 大部分Mix指令比较简单。

| Argument  | Type           | Commet             |
| --------- | -------------- | ------------------ |
| r1        | REQ\|List<REG> | List至少有一个元素 |
| method    | OPT\|STR       |                    |
| container | OPT\|STR       |                    |
| purpose   | OPT\|STR       |                    |
| repeat    | OPT\|NUM       |                    |
| notice    | OPT\|STR       |                    |
| r0        | RET\|REG       |                    |

### 9. Dilute

例句：

- **Dilute** **Streptavidin HRP and Biotin Conjugate(r1) 1:99(targetConc)** using **conjugate diluent(r2)** to **prepare the detection solution(purpose).**
- **Dilute** **10 µl purified virus(r1)** in **90 µl PBS(r2)** to **add Multiplicity of infection of 10 to the tube of cells to infect(purpose).**
- **Dilute** the **genomic DNA products(r1)** to **50 ng/μL(targetConc)**.

总结：

1. 有时候通过1：n或者浓度单位来显式指出目标浓度，有时候通过给出稀释溶剂的体积来隐式指出。
2. Dilute cells to 1.0 x 105 cells\/mL (for 6 well) or 1.25 x 105 cells\/mL (for 12 well) in supplemented growth medium in a 50 mL tube or larger sterile bottle to the total volume that will be used for seeding (2 mL\/well for 6 well and 800 μL\/well for 12 well, making 2-5 mL extra).**若可选不同稀释方式，应该怎样表示？**
3. 有时并未指出稀释液种类，应当用什么来稀释？

| Argument   | Type     | Commet |
| ---------- | -------- | ------ |
| r1         | REQ\|REG |        |
| r2         | REQ\|REG | 稀释液 |
| targetConc | OPT\|STR |        |
| purpose    | OPT\|STR |        |
| r0         | RET\|REG |        |

### 10. shake

例句：

- **Shake** at **moderate speed(speed)** for **approximately 30 minutes(time)**.
- **Shake** the **tubes(r1)** **vigorously(speed)** by **hand(method)**.
- **Shake** **PCR clean-up plate(r1)** using the **plate shaker(device)** at **1800 rpm(speed)** for **2 minutes(time)**.

总结：

1. shake大部分也是用rpm或xg表示强度，和离心相同。
2. Shake 200x spin 14K for 10 mins @ 4C**,14K是什么？200x是什么？**
3. Shake at 900-1100 rpm for 30 sec and turn down to 300-450 rpm.**分段离心怎么表示？**

| Argument    | Type      | Commet             |
| ----------- | --------- | ------------------ |
| r1          | REQ\|REG  |                    |
| speed       | OPT\|SPD  |                    |
| time        | OPT\|TIME |                    |
| method      | OPT\|STR  |                    |
| device      | OPT\|STR  |                    |
| repeat      | OPT\|NUM  | 手摇一般会给出次数 |
| temperature | OPT\|TEMP |                    |
| r0          | RET\|REG  |                    |

### 11. Centrifuge

例句：

- **Centrifuge** at **2,500g(spd)** for **15 min(time)** at **4 °C(temperature)**.
- **Spin** at **13,200 rpm(spd)** at **RT(temperature)** for **15min(time)**.
- **Centrifuge** **samples(r1)** for **1 min(time)** at **13,000 g(spd)** to **separate the phases(purpose)**.
- **Spin** down **(1 sec)(time)**.

总结：

1. 离心是在离心机中进行的标准操作，protocol书写较为规范。标准的离心中，离心力（rpm/xg/rcf）和时间是必须给出的，温度可选；但是若随意spin down一下，这三个参数都可以不给（spin down就是快速离心的意思，稍微离心一下，把管子内壁上的残留甩下来）

同义词：

centrifugate，spin

| Argument    | Type      | Commet |
| ----------- | --------- | ------ |
| r1          | REQ\|REG  |        |
| speed       | OPT\|SPD  | 离心力 |
| time        | OPT\|TIME |        |
| temperature | OPT\|TEMP |        |
| purpose     | OPT\|STR  |        |
| r0          | RET\|REG  |        |

### 12. Purify

例句：

- **Purify** **CD11c-positive cells(r1**) **twice(repeat)** using **CD11c MicroBeads(device)** **according to** **the manufacturer&#x2019;s instructions(notice)**.
- **Purify** **RNA(r1)** using a **RNeasy Micro Kit (Qiagen)(device)**.
- **Purify** the **products(r1)** using **Eppendorf Perfectprep PCR Cleanup 96(device)**.

总结：

1. 比较难以归纳，但是大部分是使用特定设备净化。

| Argument | Type     | Commet                             |
| :------- | -------- | ---------------------------------- |
| r1       | REQ\|REG |                                    |
| device   | REQ\|STR | 净化设施必须给出，否则无法进行操作 |
| notice   | OPT\|STR |                                    |
| r0       | RET\|REG |                                    |

### 13. Discard

例句：

- **Discard** **supernatant(component)**.
- **Discard** the **protein solution(component)**.
- **Pipette off(device)** **supernatant(component)** completely.

总结：

1. Discard常与remove连用，如Remove and discard the supernatant. 但是remove语义本来就包含discard，所以此时discard是多余的。
2. Discard往往只扔掉操作reagent的一部分（如上清液），否则制作这个reagent就没有意义了。
3. 绝大部分情况都是discard the supernatant。

同义词：

pipette off

| Argument  | Type     | Commet |
| :-------- | -------- | ------ |
| r1        | REQ\|REG |        |
| component | REQ\|STR |        |
| r0        | RET\|REG |        |

### 14. Replace 

例句：

- **Replace** the **medium(component)** with **xeno-free hEPS medium(r2)** **24 hours later(timer)**.
- **Replace** **1 ml(volume)** of **Locke solution(component) 10 times every 5 min(frequency)**.
- **Replace** with **250 µL Cell Recovery Solution(r2)**.

总结：

1. Replace大部分意思是代替，少部分意思是放置（同place），如Replace plates into incubator and incubate for a further 18 to 24 hours.如何处理？
2. 有时候操作的是设备而非试剂如Replace the waste tube with a collection microcentrifuge tube.，如何处理？
3. vol对component进行约束，是不是有点怪？

| Argument  | Type      | Commet     |
| :-------- | --------- | ---------- |
| r1        | REQ\|REG  |            |
| component | OPT\|STR  |            |
| r2        | REQ\|REG  | 换成的试剂 |
| volume    | OPT\|VOL  |            |
| frequency | OPT\|FREQ |            |
| timer     | OPT\|TIME |            |
| r0        | RET\|REG  |            |

### 15. Measure

例句：

- **Measure** the **total weight(parameter)** of **the sample loaded (for example, 750 µL in Figure 5) in a well(r1)**.
- **Measure** the **recovered RCA DNA(r1)** using **Nanodrop(device)**[紫外分光光度计?].
- **Measure** the **final volume(parameter)** of the **supernatant \(About 500 µL)(component)** by **weighing the tubes again(method)**.

总结：

1. emit应当是Data类型？
2. 有些Measure并没有给出测量的具体parameter，其原因可能是测量的内容通过device隐式给出，如紫外分光光度计就是测吸光度的。

| Argument  | Type      | Commet |
| :-------- | --------- | ------ |
| r1        | REQ\|REG  | alive  |
| parameter | OPT\|STR  |        |
| device    | OPT\|STR  |        |
| component | OPT\|STR  |        |
| method    | OPT\|STR  |        |
| d0        | RET\|DATA |        |

### 16. Dissolve

例句：

- **Dissolve** **1.0 g HAuCl4•4H2O(r1)** with **Millipore water(r2)** in **a 100 mL volumetric flask(container)** to make **1% (w\/v) HAuCl4•4H2O solution(targetConc)**.
- **Dissolve** **0.8 mg RGO(r1)** in **1.5 mL chitosan solution(r2)**.
- **Dissolve** the **pellet(r1)** in **water (VW)(r2)** to yield a solution of **0.01-0.1 mg/ml(targetConc)** **(based on the amount of starting materials) (note: the color is yellowish)(notice)**.

总结：

1. 嵌套无法解决？Dissolve the Matrigel ring by adding about 125 µL dispase at 5 mg\/mL to each well of the 24-well plate to make the final concentration of dispase 1 mg\/ml.
2. **Dissolve** the **reagents(r1)** **according to manual instructions(notice)**.r2 missing怎么办？因为r2在notice里面，预测也预测不出来

| Argument   | Type      | Commet |
| :--------- | --------- | ------ |
| r1         | REQ\|REG  |        |
| r2         | REQ\|REG  |        |
| container  | OPT\|STR  |        |
| targetConc | OPT\|CONC |        |
| notice     | OPT\|STR  |        |
| r0         | RET\|REG  |        |

### 17. Aspirate 吸取

例句：

- **Aspirate** **PBS(component)** from the **collection tube(source)**.
- **Aspirate** **supernatant(component)**.
- **Aspirate** **gently(notice)** to **remove the supernatant(component)**.

总结：

1. 句式非常简单（Aspirate something），类似Discard。只是往往和其他操作连用，如Aspirate and re-suspend，Aspirate and discard等。
2. 一般都不给出r1，全靠预测。
3. 如何判断吸的是全部，还是一个部分？如果是全部则r1 alive

| Argument  | Type     | Commet  |
| :-------- | -------- | ------- |
| r1        | REQ\|REG | alive？ |
| component | OPT\|STR |         |
| source    | OPT\|STR |         |
| notice    | OPT\|STR |         |
| r0        | RET\|REG |         |

### 18. Spin

应该同Centrifuge？未搞清spin down和spin区别。



### 19. Coat 涂覆

例句：

- **Coat** **samples(r1)** with **gold(r2)** using **sputter coater(device)**.
- **Coat** **wells(r1)** with **1-2 ml of 0.5% gelatin solution(r2)** in **a humidified incubator(device)** at **37⁰C(temperature)** for **30 minutes(time).**
- **Coat** the **surface of MEA(r1)** with **0.1mg\/mL poly-D-lysine(r2[0])** and **Geltrex(r2[1])** to **improve cell adhesion(purpose)**. 

总结：

1. Coat a 6-well UpCell<sup>®<\/sup> plate \\(for corneal epithelial transplantation) or a 12-well culture insert \\(for promoting differentiation or for long-term culture) with LN511E8 at 0.5-1.0 mg\/cm<sup>2<\/sup> by incubation at 37°C for at least 60 min. Or怎么处理？
2. 

| Argument    | Type           | Commet |
| :---------- | -------------- | ------ |
| r1          | REQ\|REG       |        |
| r2          | REQ\|List<REG> |        |
| device      | OPT\|STR       |        |
| time        | OPT\|TIME      |        |
| temperature | OPT\|TEMP      |        |
| r0          | RET\|REG       |        |

### 20. Rinse 冲洗

例句：

- **Rinse** **filter(r1)** with **2 mL ice cold staining solution(r2)** to **dislodge cells stuck to the membrane(purpose)**.
- **Rinse** **brains(r1)** **six times(repeat)** in **PBS(r2)**, **4 min(time)** for each rinse.
- **Rinse** the **metallic layer(componment)** of the **blank DVD(r1)** with **ethanol(r2)** to **remove the organic dye(purpose)**.

总结：

1. 有时候没有指出冲洗的液体，应当默认为水？

| Argument | Type           | Commet        |
| :------- | -------------- | ------------- |
| r1       | REQ\|REG       |               |
| r2       | REQ\|List<REG> | default=water |
| repeat   | OPT\|NUM       |               |
| time     | OPT\|TIME      |               |
| purpose  | OPT\|STR       |               |
| r0       | RET\|REG       |               |

### 21.Elute 洗脱

例句：

- **Elute** **column(r1)** with **5 column volumes of 25 mM DTT in PBS(r2)**, **flow rate 2.5 ml/min(flowrate)**.
- **Elute** **DNA(r1)** by using **50 µL 25 mM K-3BO-3 (pH 7.0)(r2)**.
- **Elute** **proteins(r1)** **twice(repeat)** with **at least four to 10 bead volumes of elution buffer \\(0.2 M glycine, pH 2.3\/ 0.5% Igepal CA-630)(r2)** for **20 min(time), 37 ˚C(temperature).**

总结：

1. 大部分句式简单，仅指出洗脱液类别。少数过柱操作说明了流速（flowrate）

| Argument    | Type           | Commet |
| :---------- | -------------- | ------ |
| r1          | REQ\|REG       |        |
| r2          | REQ\|List<REG> |        |
| flowrate    | OPT\|RATE      |        |
| time        | OPT\|TIME      |        |
| temperature | OPT\|TEMP      |        |
| r0          | RET\|REG       |        |

### 22. Combine 具体设计待讨论

### 23. Vortex 涡旋仪

例句：

- **Vortex** **vigorously(notice)** for **30 seconds(time)** at **RT(temperature)**.
- **Vortex** **9 times(repeat)**.
- **Vortex** the **tube(r1)** **at the lowest speed(notice)** for **at least 30 minutes(time)** **to permeabilize membranes(purpose)**.

总结：

1. 什么参数都不是必须给出，有时候只是随意转一下。
2. at lowest speed等，是归于notice还是speed？speed是否为离心机独有参数？

| Argument    | Type      | Commet |
| :---------- | --------- | ------ |
| r1          | REQ\|REG  |        |
| time        | OPT\|TIME |        |
| temperature | OPT\|TEMP |        |
| repeat      | OPT\|NUM  |        |
| purpose     | OPT\|STR  |        |
| notice      | OPT\|STR  |        |
| r0          | RET\|REG  |        |

### 24. Thaw 解冻

例句：

- **Thaw** **Matrigel(r1)** **on ice(environment)**.
- **Thaw** **100 ml aliquot of serum(r0)** at **4°C(temperature)** **overnight(time)**.
- **Thaw** **20 mM unidirectional linker mix(r1)** **in an ice-water bath(environment)**.

总结：

1. Env参数应当包含前面的介词，如“on ice”
2. Thaw 常与 on ice连用，但是有时候也会简单到没有任何参数，如Thaw samples
3. protocol写作比较规范

| Argument    | Type      | Commet                     |
| :---------- | --------- | -------------------------- |
| r1          | REQ\|REG  |                            |
| environment | OPT\|STR  | 包含名词前的介词，如on ice |
| temperature | OPT\|TEMP |                            |
| time        | OPT\|TIME |                            |
| r0          | RET\|REG  |                            |

### 25. Passage 传代    

例句：

- **Passage** to **new Gelatin-coated 150-mm culture dish(r2)** at **1:4 dilution(targetConc)** with **0.25w\/v% trypsin digestion(r3)**.
- **Passage** **feeder-independent hESCs(r1)** using **0.5 mM EDTA(r3)** in **sterile D-PBS(r2)** **without calcium and magnesium(notice)**.
- **Passage** **xeno-free human EPS cells(r1)** **every 3-4 days(frequency)**.

总结：

1. Protocol样本较少
2. 传代培养基未指出时，如何判断使用何种培养基？
3. 可能出现额外加入多种试剂的情况，故将r3提前扩展为List

| Argument   | Type           | Commet             |
| :--------- | -------------- | ------------------ |
| r1         | REQ\|REG       |                    |
| r2         | REQ\|REG       | 传代培养基         |
| r3         | OPT\|List<REG> | 传代额外加入的试剂 |
| targetConc | OPT\|CONC      |                    |
| notice     | OPT\|STR       |                    |
| frequency  | OPT\|FREQ      |                    |
| r0         | RET\|REG       |                    |

### 26. Pellet 破碎

例句：

- **Pellet** **cells(r1)** by **centrifugation at 200 rcf for 5 min (4ºC)(method)**.
- **Pellet** the **particles(r1)** via a **magnetic separator(device)**.
- **Pellet** **cells(r1)** for **3 min(time)** at **300xg(speed)**, **4°C(temperature)** in a **pre-chilled centrifuge(device)**.

总结：

1. 大部分例句都是Pellet cells，少部分例句中Pellet的对象是beads磁珠或nuclei细胞核，但是也是与细胞相关的。
2. Pellet cells by centrifugation经常出现，暂且将整个centrifugation处理为method字段。
3. 所有的conditions都是可选的，因为有时候仅要求Pellet the cells

| Argument    | Type      | Commet           |
| :---------- | --------- | ---------------- |
| r1          | REQ\|REG  |                  |
| method      | OPT\|STR  | 用以处理嵌套语句 |
| time        | OPT\|TIME |                  |
| speed       | OPT\|SPD  |                  |
| temperature | OPT\|TEMP |                  |
| device      | OPT\|STR  |                  |
| r0          | RET\|REG  |                  |

### 27. Repeat 重复

例句：

- **Repeat** **steps 11(begin)**-**13(end)** to **collect more samples(purpose)**.
- **Repeat** **wash(predict begin and end)**.
- **Repeat** **this step(predict begin and end)** **one more time(repeat)**.

总结：

1. 假设没有双重循环（实际上也没看到）。
2. 起止点都为闭区间。
3. 有时不指出重复起止点，如何推测？

| Argument | Type     | Commet                  |
| :------- | -------- | ----------------------- |
| begin    | REQ\|NUM | infer from the protocol |
| end      | REQ\|NUM | infer from the protocol |
| repeat   | REQ\|NUM | default=1               |

### 28. Digest 消化

例句：

- **Digest** for **6hr(time)** **RT(temperature)**.
- **Digest** **cortices from E16 rats(r1)** by **0.125 % trypsin(r2)**.
- **Digest** **tissue(r1)** in **10 mL of lysis buffer(r2)**.

总结：

1. Digest描述分为两种，第一种包括了待消化物和消化剂（如Digest cortices from E16 rats by 0.125 % trypsin.），第二种只接受一个试剂，等同于Place（如Digest for 6hr RT），原因可能是protocol将消化试剂写入了上一条ADD中

| Argument    | Type      | Commet     |
| :---------- | --------- | ---------- |
| r1          | REQ\|REG  | 待消化试剂 |
| r2          | OPT\|REG  | 消化试剂   |
| time        | OPT\|TIME |            |
| temperature | OPT\|TEMP |            |
| r0          | RET\|REG  |            |

### 29. Extract 提取

例句：

- **Extract** the **solution(r1)** with **EtOAc (4 ×(repeat) 50 mL)(r2)**.
- **Extract** **remaining peptide(r1)** from **gel(source)** with **50 μl extract buffer I(50% Acetonitrile\/5% Formic acid)(r2)** for **30 min(time)** in a **thermomixer(700 rpm)(device)**.
- **Extract** **genomic DNA(r1)** from **5 ml whole blood(r2)** using **standard phenol/chloroform method(method)**.

总结：

1. (4 × 50 mL)意思为50mL抽取四次，包含一个隐藏的repeat，不能直接作为r2的属性。
2. 极少数提取操作未指明提取试剂，如：Extract spleens and place them in a Petri dish.是否为徒手摘取？
3. 提取后的原试剂，是否还有利用价值（是否alive）？

| Argument | Type     | Commet                |
| :------- | -------- | --------------------- |
| r1       | REQ\|REG | 待提取试剂（alive？） |
| r2       | OPT\|REG | 提取剂                |
| repeat   | OPT\|NUM | 反复提取次数          |
| r0       | RET\|REG |                       |

### 30. Equilibrate 不知道意思

### 31. Pipette 吹打

例句：

- **Pipette** **cells(r1)** **few times(repeat)**.
- **Pipette** up and down **several times(repeat)** to **ensure mixing(purpose)**.
- **Pipette** about **20-30 times(repeat)** with a **1 ml pipette tip(device)** to **obtain a single cell suspension(purpose)**.

总结：

1. Pipette有三种意思，一种归于Transfer/Add，是转移操作；一种归于Discard，通常写作“Pipette off”一种是“吹打”

| Argument | Type     | Commet |
| :------- | -------- | ------ |
| r1       | REQ\|REG |        |
| repeat   | OPT\|NUM |        |
| purpose  | OPT\|STR |        |
| r0       | RET\|REG |        |

### 32. Concentrate

例句：

- **Concentrate** **eluate(r1)** in **speedvac(device, 真空离心蒸发浓缩器)** to **22.5 µL(targetVol)**.
- **Concentrate** the **commercial silver colloid(r1) 10 times(repeat)** by **centrifugation \\(16,770 g, 15 min)(method).**
- **Concentrate** **proteins(r1)** to **greater than 0.1 mg/mL(targetConc)** for **reconstitution of chromatin(purpose)**, **if necessary, using a concentrator \\(MWCO, 10,000) or a CM52 column(notice)**.

总结：

1. 和Dilute稀释不一样的是，Concentrate大多数指出的是目标体积而不是目标浓度
2. 为了精准表达意思，此处的浓度采用新参数targetVol而非旧参数Volume，避免被误认为是待浓缩试剂的体积。
3. 有的protocol未给出任何参数，如Concentrate if necessary，只是视情况浓缩，不利于指令翻译。

| Argument   | Type      | Commet |
| :--------- | --------- | ------ |
| r1         | REQ\|REG  |        |
| targetVol  | OPT\|VOL  |        |
| targetConc | OPT\|CONC |        |
| method     | OPT\|STR  |        |
| device     | OPT\|STR  |        |
| r0         | RET\|REG  |        |

### 33. Harvest

归为Collect

### 34. Sterilize 灭菌

例句：

- **Sterilize** the **both sides(component)** of **flanks(r1)** with **a Betadine dipped gauze sponge(r2)**.
- **Sterilize** **the medium(r1)** in **an autoclave(device)**  at **110C(tempurature)** for **15 minutes(time)**.
- **Sterilize** **20-50 seeds(r1)** for **30 s(time)** with **20 ml of 75% ethanol(r2)** in **a sterile Petri dish with a lid(device)**.

总结：

1. 有时使用试剂灭菌，有时使用设备，所以r2是可选的。
2. 有时只对r1的一个部分进行灭菌（如小鼠皮肤），故应加入component参数

| Argument    | Type      | Commet     |
| :---------- | --------- | ---------- |
| r1          | REQ\|REG  | 待灭菌试剂 |
| r2          | OPT\|REG  | 灭菌剂     |
| component   | OPT\|STR  |            |
| device      | OPT\|STR  |            |
| time        | OPT\|TIME |            |
| tempurature | OPT\|TEMP |            |
| r0          | RET\|REG  |            |

### 35. precipitate 沉淀

例句：

- **Precipitate** the **RNA(component) overnight(time)** with **one volume of 5 M lithium chloride(r2)** at **-80°C(temperature)**.
- **Precipitate** **DNA(component)** by **adding &#x25B2; 3.5 ml or &#x25CF; 10.5 ml \\(0.7 volumes) of room temperature isopropanol to the eluted DNA(method)**.
- **Precipitate** **DNA(component)** at **-20&#xB0;C(temperature)** for **at least 30 min(time).**

总结：

1. 沉淀的一定是原始试剂r1的一部分，所以使用component指示要沉淀的部分
2. 出现大量嵌套（by adding等），使用method字段处理。
3. 沉淀后的原试剂是否还有使用价值（如提取上清液）？是否keep alive？

| Argument    | Type      | Commet     |
| :---------- | --------- | ---------- |
| r1          | REQ\|REG  | 待沉淀试剂 |
| r2          | OPT\|REG  | 沉淀剂     |
| component   | REQ\|TIME |            |
| time        | OPT\|TIME |            |
| temperature | OPT\|TEMP |            |
| method      | OPT\|STR  |            |
| r0          | RET\|REG  |            |

### 36. Quench 猝灭

例句：

- **Quench** the crosslinking by **adding 10 mL of 2.5M Glycine(method)**.(crosslinking是反应名不是试剂名)
- **Quench** with **NH4Cl 50mM 15 min(r2)**.
- **Quench** **unreacted iodoacetamide(r1)** by **incubation with 5 – 10 mM DTT (final concentration) for 30 min at 25 °C(method)**.

总结：

1. 大量出现嵌套语句，如Quench the crosslinking by adding 10 mL of 2.5M Glycine.
2. 猝灭剂理应是REQ，但是出现在嵌套语句中被处理为method一部分，所以r2是OPT

| Argument | Type      | Commet     |
| :------- | --------- | ---------- |
| r1       | REQ\|REG  | 待猝灭试剂 |
| r2       | OPT\|REG  | 猝灭剂     |
| time     | OPT\|TIME |            |
| r0       | RET\|REG  |            |

### 37. Flow

例句：

- **Flow** the **worm suspension(r1)** through the **filtering device(device)** to **remove debris(purpose)**.
- **Flow** the **cleavage buffer(r1)** onto **the sample(r2)** to **extinguish fluorescence from the sample(purpose)**.
- **Flow** the **imaging buffer(r1)** onto **the sample(r2)**.

总结：

1. Flow可描述为：使一个液体试剂流过某种固体（设备device或试剂r2），r2是OPT。
2. Flow cytometry analysis of SVF等Flow开头的句子并非Flow操作，而是流式细胞仪。

| Argument | Type     | Commet                    |
| :------- | -------- | ------------------------- |
| r1       | REQ\|REG | 流动试剂                  |
| r2       | OPT\|REG | 待冲刷试剂                |
| device   | OPT\|REG | device和r2不可同时missing |
| purpose  | OPT\|STR |                           |
| r0       | RET\|REG |                           |

### 38. Normalize 标准化

例句：

- **Normalize** **samples(r1)** for protein concentration \\(recommended concentration: **between 0.3 and 0.6 µg\/µl(targetConc)**).

总结：

1. 可以对溶液浓度进行标准化，也可以对于数据进行标准化。可以操作REG也可以操作DATA【DATA未处理】

| Argument   | Type      | Commet |
| :--------- | --------- | ------ |
| r1         | REQ\|REG  |        |
| targetConc | OPT\|CONC |        |
| r0         | RET\|REG  |        |

### 39. Dispense

例句：

- **Aliquot** **control cells(r1)** into **9(r0.size) tubes(container)** of **100 µL(volume)** each.
- **Dispense** **4 μL(volume)** into **each(r0.size)** well of a **96-well PCR plate(container)**.
- **Aliquot** the **cell suspension(r1)** at **1 ml(volume)** each into **cryotubes(container)**.

总结：

1. 分发操作，r0为List<REG>类型，元素数量通常由protocol指出，有时候需要推测。
2. protocol较为规范，容器，体积均必须给出
3. 仅此一个操作允许多emit

| Argument  | Type           | Commet |
| :-------- | -------------- | ------ |
| r1        | REQ\|REG       |        |
| volume    | REQ\|VOL       |        |
| container | REQ\|STR       |        |
| r0        | RET\|List<REG> |        |

### 40. Evaporate 蒸发

例句：

- **Evaporate** the **tube(r1)** under **N2(environment)** in **a water bath(environment)** with **30-40 C(temperature)**. It takes **about an hour(time)**.
- **Evaporate** the **solvent(r1)** to **dryness(termination)** using **a rotary evaporator(device)**.
- **Evaporate** the **separated organic solution(r1)** with **a rotary evaporator(device)** at **50℃(temperature)** for **4 minutes(time)**.

总结：

1. 句式比较规范，Evaporate没有二义性

| Argument    | Type      | Commet             |
| :---------- | --------- | ------------------ |
| r1          | REQ\|REG  |                    |
| environment | OPT\|STR  |                    |
| device      | OPT\|STR  |                    |
| temperature | OPT\|TEMP |                    |
| time        | OPT\|TIME |                    |
| termination | OPT\|STR  | 反应终点，如”蒸干“ |
| r0          | RET\|REG  |                    |

### 41. Aliquot 取样

例句：

- **Aliquot** **3 mL(volume)** of **cold DMEM/F-12(r1)** into **a 15 mL tube(container)**.
- Aliquot **cells(r1)** into **a 15 mL tube(container)**.
- Aliquot **mRNA(r1)**.

总结：

1. Aliquot 有时是等分样品之意，这些应归入Dispense
2. 取样后原样品应当还有反应价值，keep alive

| Argument  | Type     | Commet     |
| :-------- | -------- | ---------- |
| r1        | REQ\|REG | keep alive |
| volume    | OPT\|VOL |            |
| container | OPT\|STR |            |
| r0        | RET\|REG |            |

### 42. Wash 

例句：

- **Wash** the **slides(r1)** in **0.01M PBS(r2)** for **5 min(time)** **three times(repeat)**.
- **Wash** the **beads(r1)** **twice(repeat)** by **adding 500 μL of Tween Wash Buffer and incubating at 55 for 2 minutes shaking(method)**.
- **Wash** **twice(repeat)** for **5 min(time)** with **1 ml PBS(r2)** at **room temperature(temperature)** **while gently rocking(notice)**.

总结：

1. 有少量指令嵌套。

| Argument    | Type      | Commet |
| :---------- | --------- | ------ |
| r1          | REQ\|REG  |        |
| r2          | OPT\|REG  | 清洗剂 |
| time        | OPT\|TIME |        |
| temperature | OPT\|TEMP |        |
| repeat      | OPT\|NUM  |        |
| notice      | OPT\|STR  |        |
| method      | OPT\|STR  |        |
| r0          | RET\|REG  |        |

### 43. Place

例句：

- **Place** the **cryo vials(r1)** **directly(notice)** **in the wells of the pre-equilibrated CoolRack CFT30(destination)** to **snap-freeze the samples(purpose)**.
- **Place** **500 μL(volume)** of **the final extract(r1)** in **a chromatographic vial(destination)**.
- **Place** back in **37°C incubator(destination) overnight(time)**.

总结：

1. Place的目的地有很多，包括container，device，environment（water bath），考虑到是转移操作，此处统一识别为destination
2. 有必要保留destination前的介词，可以区别in ice（冰浴）和on ice等的区别，保留完整语义。

| Argument    | Type      | Commet |
| ----------- | :-------- | :----- |
| r1          | REQ\|REG  |        |
| destination | REQ\|STR  |        |
| notice      | OPT\|STR  |        |
| time        | OPT\|TIME |        |
| r0          | RET\|REG  |        |

### 44. Prepare

例句：

- Prepare a bacteria glycerol stock by diluting the bacterial preparation with a sterile glycerol solution for a final 15-50% v\/v glycerol concentration.
- Prepare a 1% × 2% agarose gel: Melt 1.0 g agarose in 84.6ml DEPC water and boil in a microwave.

总结：

1. Prepare大部分时候不表示实际操作，只是作为其他操作的comment或者嵌套了其他指令。建议保留原文，不设计为特定指令。
2. 少数时候Prepare也表示实际操作，如：Prepare 1 ml of PBS in 1.5 ml Eppendorf tube and set up micropipette \\(The Stripper) with 75 µm tip. 意思类似于Transfer

### 45. Use

例句：

- **Use towels(device)** to **move bowels to the left side to expose the major vessels in the retroperitoneum(purpose)**.
- **Use** **a 1 mL syringe(device)** to **add 5 mL CM \\(2:1) to redissolve the lipids and cap tightly(purpose)**.
- **Use the adhesive film(device)** to **seal the plate(purpose)**.

总结：

1. 和Prepare相似，大部分时候不表示实际操作。但是Use总是与嵌套连用，形式较Prepare单一，可以用device+purpose结构描述。
2. Use没有实际操作，所以没有REG。r0，r1等实际藏在嵌套指令purpose中

| Argument | Type     | Commet |
| -------- | :------- | :----- |
| device   | REQ\|STR |        |
| purpose  | REQ\|STR |        |





### Condition

| Argument      | Type              | Commet                                                       |
| ------------- | ----------------- | ------------------------------------------------------------ |
| source        | STR               | 涉及转移的操作中，操作前试剂的位置（Transfer，Collect，Aspirate）（from） |
| destination   | STR               | 涉及转移的操作中，操作后试剂的位置（into）                   |
| temperature   | TEMP              | 温度（at）                                                   |
| volume        | VOL               | 体积（用于表示分割，如取10ml上清液）                         |
| time          | TIME              | 时间（for）                                                  |
| targetConc    | CONC              | 目标浓度                                                     |
| device        | STR               | 工具/设备（in，via，using）                                  |
| method        | STR               | 方法（by）                                                   |
| environment   | STR               | 环境（in，on）                                               |
| notice        | STR               | 注意事项，包括副词，括号中的内容等                           |
| purpose       | STR               | 用途（本质是commet一种）（to，for）                          |
| thermoProgram | STR               | 热循环仪程序                                                 |
| container     | STR               | 操作容器（in）                                               |
| frequency     | FREQ=NUM/TIME     | 频率                                                         |
| repeat        | NUM               | 重复次数                                                     |
| supplement    | STR               | 辅剂 STR还是REG？                                            |
| speed         | SPD               | shake/centrifuge/spin强度，单位为rpm或xg(xg=rcf)             |
| component     | STR               | remove/discard操作试剂的组分                                 |
| timer         | TIME              | 一定时间后执行                                               |
| parameter     | NUM/VOL/TEMP/TIME | Measure测定某些参数                                          |
| flowrate      | RATE=VOL/TIME     | Elute等操作的流速                                            |
| targetVol     | VOL               | Concentrate目标体积，区别于vol                               |
| termination   | STR?              | 反应终点（until）                                            |