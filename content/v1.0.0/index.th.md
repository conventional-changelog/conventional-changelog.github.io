---
draft: false
aliases: ["/th/"]
---

# Conventional Commits 1.0.0

## ข้อสรุป

ข้อกำหนดของข้อตกลงในการ Commits (Conventional Commits) คือข้อตกลงอย่างง่ายที่สร้างขึ้นสำหรับข้อความที่ commit
ข้อกำหนดนี้จะรวมข้อกำหนดในการสร้างข้อความในการ commit อย่างชัดเจน
ซึ่งจะช่วยให้สามารถเขียนชุดเครื่องมืออัตโนมัติต่อยอดได้ง่ายขึ้น
ข้อตกลงนี้จะใช้รูปแบบเดียวกับ [SemVer](http://semver.org)
โดยมีการอธิบายถึงฟีเจอร์ การแก้ไขต่าง ๆ และการเปลี่ยนแปลงที่ขัดต่อเวอร์ชั่นก่อนหน้าลงไปในข้อความที่ commit

ข่้อความที่ commit ควรจะมีโครงสร้างตามนี้

---

```
<ชนิด>[ละได้ ขอบเขต]: <รายละเอียด>

[ละได้ เนื้อหา]

[ละได้ ข้อความลงท้าย]
```
---

<br />
โดย commit จะมีหน่วยโครงสร้างย่อย ๆ ตามนี้ เพื่อใช้ในการสื่อสารถึงความตั้งใจให้กับคนที่นำไลบรารี่ของคุณไปใช้งาน

1. **fix:** commit ที่มี _ชนิด_ `fix` หมายถึงมีการแก้ไขบักในโค้ดของคุณ (จะสอดคล้องกับ [`PATCH`](http://semver.org/#summary) ใน semantic versioning)
2. **feat:** commit ที่มี _ชนิด_ `feat` หมายถึงมีการเพิ่มฟีเจอร์ใหม่เข้าไปในโค้ด (จะสอดคล้องกับ [`MINOR`](http://semver.org/#summary) ใน semantic versioning)
3. **BREAKING CHANGE:** commit ที่ลงท้ายด้วย `BREAKING CHANGE:` ในข้อความลงท้าย หรือ ต่อท้ายด้วย `!` หลังจาก type หรือ scope จะหมายถึงมีการเพิ่มการเปลี่ยนแปลงที่กระทบกับ API เดิม (จะสอดคล้องกับ [`MAJOR`](http://semver.org/#summary) ใน semantic versioning)
โดยที่ BREAKING CHANGE สามารถเป็นส่วนหนึ่งของ commit _ชนิด_ ไหนก็ได้
1. _ชนิด_ อื่น ๆ ที่ไม่ใช่ `fix:` and `feat:` สามารถใช้ได้เช่นกัน เช่น [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (อ้างอิงจาก [ข้อตกลงของ Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)) ได้แนะนำชนิด `build:`, `chore:`,
  `ci:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:` และอื่น ๆ
1. _ข้อความลงท้าย_ ที่นอกเหนือจาก `BREAKING CHANGE: <รายละเอียด>` สามารถใช้ได้ และเขียนตามข้อตกลงเดียวกันกับ
  [git trailer format](https://git-scm.com/docs/git-interpret-trailers)

ชนิดอื่น ๆ เพิ่มเติมไม่ได้อยู่ในขอบเขตตามข้อกำหนดของข้อตกลงในการ Commits นี้ และไม่ได้มีผลกระทบอะไรใน semantic versioning (ถ้าไม่ได้ระบุใน BREAKING CHANGE)
<br /><br />
ขอบเขตอาจจะถูกระบุไปกับชนิดของ commit เพื่อบอกข้อมูลของบริบทเพิ่มเติม โดยจะระบุอยู่ในเครื่องหมายวงเล็บ เช่น `feat(parser): add ability to parse arrays`

## ตัวอย่าง

### ข้อความ commit ที่มีการระบุรายละเอียด และลงท้ายด้วย breaking change footer
```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### ข้อความ commit ที่มี `!` เพื่อบ่งบอก breaking change
```
refactor!: drop support for Node 6
```

### ข้อความ commit ที่มีทั้ง `!` และ BREAKING CHANGE ลงท้าย
```
refactor!: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.
```

### ข้อความ commit ที่ไม่มีเนื้อหา
```
docs: correct spelling of CHANGELOG
```

### ข้อความ commit ที่ระบุขอบเขต
```
feat(lang): add polish language
```

### ข้อความ commit ที่มีเนื้อหาหลายย่อหน้า และมีข้อความลงท้ายหลายข้อความ
```
fix: correct minor typos in code

see the issue for details

on typos fixed.

Reviewed-by: Z
Refs #133
```

## ข้อกำหนด

คำสำคัญ “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, และ “OPTIONAL” ในเอกสารฉบับนี้จะถูกแปลตามที่อธิบายไว้ใน [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt)

1. ข้อความ commit จะต้องขึ้นต้นด้วย ชนิด ซึ่งประกอบด้วยคำนาม `feat`, `fix`, ฯลฯ และตามด้วยขอบเขตซึ่งอาจจะละไว้ได้ และตามด้วย `!` ซึ่งอาจจะละไว้ได้ และเครื่องหมายโคล่อน (:) และเว้นวรรค
2. ชนิด `feat` จะถูกใช้เมื่อใน commit นั้นมีการเพ่ิมฟีเจอร์ใหม่เข้าไปในแอพพลิเคชั่น หรือไลบรารี่ของคุณ
3. ชนิด `fix` จะถูกใช้เมื่อ commit นั้นเป็นการแก้ไขบักสำหรับแอพพลิเคชั่นของคุณ
4. ขอบเขตอาจจะถูกเขียนหลังจากชนิด โดยขอบเขตจะต้องอธิบายได้ถูกส่วนของโค้ด และอยู่ภายใต้วงเล็บ เช่น `fix(parser):`
5. คำอธิบายจะต้องอยู่ต่อจากเครื่องหมายโคล่อนและเว้นวรรคที่อยู่หลังจากชนิดและขอบเขตในตอนแรกทันที
คำอธิบายจะเป็นข้อความสรุปอย่างสั้นสำหรับการเปลี่ยนแปลงของโค้ด เช่น _fix: array parsing issue when multiple spaces were contained in string_
1. เนื้อหา commit ที่ยาวกว่าสามารถใส่เพิ่มหลังจากข้อความ commit แบบสั้นแล้วได้ โดยให้ใส่ข้อมูลในบริบทเพิ่มเติมที่เกี่ยวข้องกับความเปลี่ยนแปลงของโค้ด โดยเนื้อหานี้จะต้องเริ่มด้วยการเว้นบรรทัดว่างหนึ่งบรรทัดหลังจากรายละเอียดของ commit ในบรรทัดแรก
2. เนื้อหา commit ใส่ได้ตามอิสระ และอาจจะมีหลายย่อหน้าก็ได้
3. ข้อความลงท้ายอาจจะมีมากกว่าหนึ่ง และจะต้องอยู่หลังจากเนื้อหาโดยการเว้นบรรทัดว่างหนึ่งบรรทัด โดยข้อความลงท้ายแต่ละข้อความจะต้องประกอบด้วย กลุ่มคำ และตามด้วย `:<เว้นวรรค>` หรือ `<เว้นวรรค>#` เป็นตัวคั่น และตามด้วยข้อความ (ส่วนนี้ได้แรงบันดาลใจมาจาก
  [git trailer convention](https://git-scm.com/docs/git-interpret-trailers))
4. กลุ่มคำในข้อความลงท้ายจะต้องใช้ `-` แทนช่องว่าง เช่น `Acked-by` (ซึ่งจะช่วยแยกแยะส่วนที่เป็นข้อความลงท้ายกับเนื้อหาที่มีหลายย่อหน้าออกจากกัน) ข้อยกเว้นเดียวคือ `BREAKING CHANGE` ซึ่งอาจจะถูกใช้เป็นกลุ่มคำได้เช่นกัน
5. ข้อความในข้อความลงท้ายอาจจะมีเว้นวรรค และมีการขึ้นบรรทัดใหม่ก็ได้ การอ่านข้อความลงท้ายหนึ่งข้อความจะสิ้นสุดเมื่อเจอกลุ่มคำและตัวคั่นในข้อความลงท้ายถัดไป
6. การเปลี่ยนแปลงที่มีผลกระทบจะต้องมีการบ่งชี้ให้เห็นในส่วนของชนิด หรือขอบเขตในตอนต้น หรือเป็นส่วนหนึ่งของข้อความลงท้าย
7. ถ้าการเปลี่ยนแปลงที่มีผลกระทบเป็นส่วนหนึ่งของข้อความลงท้าย การเปลี่ยนแปลงนั้นจะต้องขึ้นต้นด้วยคำว่า BREAKING CHANGE (ตัวอักษรตัวใหญ่ทั้งหมด) และตามด้วยเครื่องหมายโคลอน `:` เว้นวรรค และรายละเอียด เช่น
_BREAKING CHANGE: environment variables now take precedence over config files_
1. ถ้าการเปลี่ยนแปลงที่มีผลกระทบเป็นส่วนหนึ่งของชนิดหรือขอบเขตในตอนต้น จะต้องใส่ `!` ต่อท้ายทันที ก่อนเครื่องหมายโคลอน `:` และเมื่อใช้ `!` อาจจะไม่ต้องใส่ `BREAKING CHANGE:` ในข้อความลงท้ายก็ได้ และรายละเอียดของ commit จะถูกใช้เพื่ออธิบายถึงสิ่งที่กระทบนั้น ๆ
2. ชนิดของ commit อื่น ๆ นอกเหนือจาก `feat` และ `fix` อาจจะถูกใช้ในข้อความ commit ได้ เช่น _docs: updated ref docs._
3. ส่วนประกอบอื่น ๆ ใน Conventional Commits จะไม่ไม่ให้ความสำคัญกับตัวอักษรใหญ่หรือเล็ก ยกเว้นแต่คำว่า BREAKING CHANGE ซึ่งจะต้องเป็นตัวใหญ่เสมอ
4. BREAKING-CHANGE จะมีความหมายเดียวกันกับ BREAKING CHANGE เมื่อถูกใช้เป็นกลุ่มคำในข้อความลงท้าย

## ทำไมถึงควรใช้ Conventional Commits

* ใช้ในการสร้าง CHANGELOG โดยอัตโนมัติ
* ใช้ช่วยในการตัดสินใจในการปรับเวอร์ชั่นตาม semantic version โดยอัตโนมัติ (โดยดูจากชนิดของ commit ที่บันทึก)
* ใช้สื่อสารถึงธรรมชาติของการเปลี่ยนแปลงให้กับเพื่อนร่วมทีม สาธารณะ และผู้ที่เกี่ยวข้องอื่น ๆ
* ใช้เริ่มกระบวนการ build และการเผยแพร่
* ช่วยให้ผู้ที่จะมีส่วนร่วมในโปรเจกต์ทำงานได้ง่ายขึ้นโดยช่วยให้พวกเขาสามารถดูข้อความ commit ย้อนหลังแบบมีโครงสร้างได้

## คำถามที่พบบ่อย

### ฉันจะจัดการกับข้อความ commit ในช่วงเริ่มต้นของการพัฒนาได้อย่างไร?

เราแนะนำให้คุณทำเหมือนกับคุณได้ปล่อยผลิตภัณฑ์ของคุณออกสู่ตลาดแล้ว โดยปกติ *บางคน* ถึงแม้จะหมายถึงเพื่อนร่วมทีมพัฒนาซอฟต์แวร์ของคุณก็ตาม มาใช้ซอฟต์แวร์ของคุณ เขาก็อยากที่จะรู้ว่าส่วนไหนถูกแก้ไขแล้ว ส่วนไหนที่มีการเปลี่ยนแปลง และรายละเอียดส่วนอื่น ๆ

### ชนิดของ commit ควรจะเป็นตัวใหญ่ หรือตัวเล็ก?

จะเป็นตัวใหญ่หรือตัวเล็กก็ได้ แต่มันจะเยี่ยมมากถ้ามันสอดคล้องกันทั้งหมด

### ฉันควรจะทำอย่างไรถ้า commit นั้นเป็นไปได้มากกว่าหนึ่งชนิด​?

กลับไปแก้ไขและพยายามแบ่งออกให้เป็นหลาย commit เท่าที่จะเป็นไปได้ ประโยชน์ส่วนหนึ่งของ Conventional Commits คือการที่มันช่วยให้เราสามารถจัดการกับ commit และ PR ได้ดีกว่าเดิม

### นี่มันจะไม่ทำให้การพัฒนาและรอบการทำงานช้าลงกว่าเดิมหรือ?

มันทำให้การทำงานแบบไม่มีการจัดการช้าลง แต่มันจะช่วยให้คุณทำงานได้เร็วขึ้นในระยะยาวกับหลาย ๆ โปรเจกต์ที่มีส่วนร่วมจากหลาย ๆ คน

### Conventional Commits จะทำให้นักพัฒนาจำกัดจำนวนของชนิดที่พวกเขาทำเพราะจะทำให้พวกเขาติดอยู่กับชนิดที่มีอยู่หรือไม่?

Conventional Commits สนับสนุนเราให้สามารถสร้างชนิดได้มากกว่านั้น เช่น fixes นอกจากนั้นแล้ว ความยืดหยุ่นของ Conventional Commits ยังอนุญาตให้ทีมของคุณสร้างชนิดของพวกเขาขึ้นมาเอง และปรับเปลี่ยนมันได้ตลอดเวลาอีกด้วย

### นี่เกี่ยวข้องกับ SemVer อย่างไร?

commit ที่มีชนิดเป็น `fix` จะถูกมองเป็น `PATCH` ใน release ส่วน commit ชนิดที่เป็น `feat` จะถูกมองเป็น `MINOR` release และ commits ที่เป็น `BREAKING CHANGE` ไม่ว่าจะเป็นชนิดใดก็ตาม จะถูกมองเป็น `MAJOR` release

### ฉันควรจะใส่เวอร์ชั่นของส่วนขยายให้กับข้อกำหนดของข้อตกลงในการ commit อย่างไร เช่น `@jameswomack/conventional-commit-spec`?

เราแนะนำให้ใช้ SemVer ในการที่จะปล่อยส่วนขยายของคุณให้กับข้อกำหนดนี้ (และสนับสนุนให้คุณสร้างส่วนขยายนี้ด้วย!)

### ฉันจะทำอย่างไรถ้าฉันใส่ชนิดของ commit ผิดโดยไม่ได้ตั้งใจ?

#### เมื่อคุณใช้ชนิดที่เป็นส่วนหนึ่งในข้อตกลง แต่ผิดชนิด เช่น ใช้ `fix` แทนที่จะเป็น `feat`

ก่อนที่จะรวม หรือปล่อยความผิดนั้นออกสู่ตลาด เราแนะนำให้ใช้ `git rebase -i` เพื่อแก้ไขข้อความใน commit ย้อนหลัง แต่ถ้าทำหลังจากที่ปล่อยสู่ตลาดไปแล้ว การแก้ไขจะแตกต่างกันไปขึ้นอยู่กับเครื่องมือและวิธีการที่คุณใช้

#### เมื่อคุณใช้ชนิดที่ *ไม่ได้* เป็นส่วนหนึ่งในข้อตกลง เช่น ใช้ `feet` แทนที่จะเป็น `feat`

ในสถานการณ์ที่แย่ที่สุด มันไม่ใช่วันสิ้นโลกถ้าคุณจะใส่ commit ที่ไม่สอดคล้องกับข้อกำหนดของข้อตกลงในการ commit มันมีความหมายง่าย ๆ คือ commit นั้นจะถูกมองข้ามไปถ้าใช้เครื่องมือที่อ้างอิงตามข้อกำหนดนี้เท่านั้นเอง

### คนที่มีส่วนร่วมในโปรเจกต์ทั้งหมดจะต้องใช้ข้อกำหนดของข้อตกลงในการ commit นี้หรือไม่?

ไม่! ถ้าคุณใช้ลำดับการทำงานแบบที่ต้องยุบรวม commit บน Git คนที่เป็นผู้ดูแลจะสามารถจัดการกับข้อความ commit ในขณะที่รวม commit เข้ามาโดยที่ไม่เป็นภาระกับผู้ที่ไม่ค่อยได้ commit
ลำดับการทำงานโดยทั่วไปสำหรับแบบนี้คือต้องทำให้ระบบ git ของคุณทำการยุบรวม commit ที่มาจาก pull request โดยอัตโนมัติ และแนะนำฟอร์มให้กับผู้ดูแลเพื่อใส่ข้อความ commit ที่เหมาะสมในการรวม commit เข้ามา

### Conventional Commits จะจัดการกับการย้อนกลับ commit ได้อย่างไร?

การย้อนกลับโค้ดอาจจะซับซ้อนได้: คุณกำลังย้อนกลับหลาย ๆ commit หรือไม่? ถ้าคุณกำลังย้อนกลับฟีเจอร์ ในการปล่อยซอฟต์แวร์สู่ตลาดครั้งถัดไปจะกลายเป็นเพียงการ patch หรือไม่?

Conventional Commits ไม่ได้บอกถึงวิธีการอย่างชัดเจนว่าจะต้องทำอย่างไรเมื่อเกิดการย้อนกลับ แต่เราปล่อยให้เป็นการจัดการของนักพัฒนาเครื่องมือเป็นผู้ใช้ความยืดหยุ่นของ _ชนิด_ และ _ข้อความลงท้าย_ ในการพัฒนาตรรกะในการจัดการการย้อนกลับ

คำแนะนำหนึ่งคือการใช้ชนิด `revert` และข้อความลงท้ายที่มีการอ้างถึงหมายเลข commit ที่จะถูกย้อนกลับ

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```

## เกี่ยวกับ

ข้อกำหนดของ The Conventional Commits ได้รับแรงบันดาลใจ และอ้างอิงมาจาก [Angular Commit Guidelines](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines).

แบบร่างฉบับแรกของข้อกำหนดนี้ถูกเขียนขึ้นโดยความร่วมมือของกลุ่มคนที่มีส่วนร่วมในโปรเจกต์เหล่านี้

* [conventional-changelog](https://github.com/conventional-changelog/conventional-changelog): a set of tools for parsing Conventional Commits messages from git histories.
* [parse-commit-message](https://npmjs.com/package/parse-commit-message): Extensible utilities for parsing, stringify and validating Conventional Commit messages.
* [bumped](https://bumped.github.io): a tool for releasing software that makes it easy to perform actions before and after releasing a new version of your software.
* [unleash](https://github.com/netflix/unleash): a tool for automating the software release and publishing lifecycle.
* [lerna](https://github.com/lerna/lerna): a tool for managing monorepos, which grew out of the Babel project.

## เครื่องมือสำหรับ Conventional Commits

* [fastlane-plugin](https://github.com/xotahal/fastlane-plugin-semantic_release): follows the specification to manage versions and generate a changelog automatically
* [commitizen/cz-cli](https://github.com/commitizen/cz-cli): A Node.js tool to create commit messages following the Conventional Commits specs.
* [commitizen-tools/commitizen](https://github.com/commitizen-tools/commitizen): A tool written in Python to create commiting rules for projects, auto bump versions and auto changelog generation.
* [php-commitizen](https://github.com/damianopetrungaro/php-commitizen): A PHP tool built to create commit messages following the Conventional Commits specs.
Configurable and usable for PHP projects as a composer dependency or usable globally for non-PHP projects.
* [commitlint](https://github.com/conventional-changelog/commitlint): A linter to check that your commit messages meet the Conventional Commits format.
* [gitlint](https://github.com/jorisroovers/gitlint): Git commit message linter written in Python, which can be configured to [enforce Conventional Commits format](https://jorisroovers.com/gitlint/contrib_rules/#ct1-contrib-title-conventional-commits).
* [conform](https://github.com/autonomy/conform): a tool that can be used to enforce policies on git repositories, including Conventional Commits.
* [detect-next-version](https://npmjs.com/package/detect-next-version): Parse, detect and get more metadata about given Conventional Commits.
* [recommended-bump](https://www.npmjs.com/package/recommended-bump): Calculcates the recommended version bump based on given Conventional Commits.
* [git-commits-since](https://www.npmjs.com/package/git-commits-since): Get all (raw) commits since period or (by default) from latest git SemVer tag, plus plugins support.
* [standard-version](https://github.com/conventional-changelog/standard-version): Automatic versioning and CHANGELOG management, using GitHub's new squash button and the recommended Conventional Commits workflow.
* [Conventional Commit](https://github.com/lppedd/idea-conventional-commit): provides extensible context and template-based completion, and inspections, for Conventional Commits inside the VCS Commit dialog. Available for all [JetBrains IDEs](https://www.jetbrains.com/).
* [Git Commit Template](https://plugins.jetbrains.com/plugin/9861-git-commit-template): Add Conventional Commits support to [JetBrains Editors](https://www.jetbrains.com/) (IntelliJ IDEA, PyCharm, PhpStorm...).
* [commitsar](https://github.com/commitsar-app/commitsar): Go tool for checking if commits on branch are Conventional Commits compliant. Comes with Docker image for CI uses.
* [semantic-release](https://github.com/semantic-release/semantic-release): A tool that automates the whole package release workflow including: determining the next version number, generating the release notes and publishing the package.
* [python-semantic-release](https://github.com/relekang/python-semantic-release): Automatic semantic versioning for Python projects. This is a Python implementation of the [semantic-release](https://github.com/semantic-release/semantic-release) for Node.js.
* [VSCode Conventional Commits](https://marketplace.visualstudio.com/items?itemName=vivaxy.vscode-conventional-commits): Add Conventional Commits supports for VSCode.
* [Pyhist](https://github.com/jgoodman8/pyhist): A Python utility to automagically update the package version from the git history and generate the Changelog.

## โปรเจกต์ที่ใช้ Conventional Commits

* [yargs](https://github.com/yargs/yargs): everyone's favorite pirate themed command line argument parser.
* [istanbuljs](https://github.com/istanbuljs/istanbuljs): a collection of open-source tools and libraries for adding test coverage to your JavaScript tests.
* [uPortal-home](https://github.com/UW-Madison-DoIT/angularjs-portal) and [uPortal-application-framework](https://github.com/UW-Madison-DoIT/uw-frame): Optional supplemental user interface enhancing [Apereo uPortal](https://www.apereo.org/projects/uportal).
* [massive.js](https://github.com/dmfay/massive-js): A data access library for Node and PostgreSQL.
* [electron](https://github.com/electron/electron): Build cross-platform desktop apps with JavaScript, HTML, and CSS.
* [scroll-utility](https://github.com/LeDDGroup/scroll-utility): A simple to use scroll utility package for centering elements, and smooth animations
* [Blaze UI](https://github.com/BlazeUI/blaze): Framework-free open source UI toolkit.
* [Monica](https://github.com/monicahq/monica): An open source personal relationship management system.
* [mhy](https://mhy.js.org): A zero-config, out-of-the-box, multi-purpose toolbox and development environment.
* [@tandil/diffparse](https://github.com/danielduarte/diffparse#readme): Simple parser for Diff files (unified diff format).
* [@tandil/diffsplit](https://github.com/danielduarte/diffsplit#readme): Easy split of .diff & .patch into its files.
* [@thi.ng/umbrella](https://github.com/thi-ng/umbrella): Monorepo of ~100 TypeScript projects for data driven development
* [yii2-basic-firestarter](https://github.com/HunWalk/yii2-basic-firestarter): 🔥 An enhanced Yii2 app template.
* [dcyou/resume](https://github.com/dcyou/resume): 😎 Template to easily and quickly create your online CV.
* [Nintex Forms](https://www.nintex.com/workflow-automation/modern-forms/): Easily create dynamic online forms to capture and submit accurate and current data.
* [Tina CMS](https://tinacms.org): An open source toolkit for building front-end content-management into your website.
* [Uno Platform](https://platform.uno): Build Mobile, Desktop and WebAssembly apps with C# and XAML. Today. Open source and professionally supported.

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

_ต้องการเพิ่มโปรเจกต์ของคุณลงในรายชื่อนี้?_ [ส่ง pull request](https://github.com/conventional-changelog/conventionalcommits.org/pulls).
