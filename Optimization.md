Майнкрафт, особенно с модами — очень требовательная к ресурсам ПК игра, анон. Если у тебя слабая печка, то ты скорее всего окажешься не доволен её производительностью. В этой статье специально для тебя были собраны все возможные рекомендации по оптимизации Minecraft, с которыми в кубач можно будет поиграть даже на некропк. Впрочем, пользуйся вдумчиво и аккуратно: некоторые из них могут оказать обратный эффект и лишь усугубить ситуацию.  

---

## Оптимизация аргументов запуска

Аргументы запуска (_**JVM флаги**_) — отличный способ облегчить жизнь твоему сборщику мусора и в целом начать использовать ресурсы комьютера более эффективно. Учти, что некоторым флагам может понадобиться полная версия джавы, т. е. **JDK** или **серверная** версия JRE. Скачать можно открытый вариант _[`тут`](https://adoptopenjdk.net/)_ или закрытый от Oracle [`тут`](https://www.oracle.com/java/technologies/javase-server-jre8-downloads.html). **На сайте Oracle требуется регистрация для скачивания**!
> Статья, в которой рассказывается об оптимизации сборщика мусора **G1GC** (_Aikar's arguments_): _[`клик`](https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/)_  
_**TIP:** По моему опыту, больше подходит для сервера, нежели для клиента._  

> Ещё одна полезная статья с аргументами, но в этот раз для оптимизации клиента: _[`оригинал`](https://cwelth.com/manuals.php?mid=2)_,  [`гуглодоки`](https://docs.google.com/document/d/1Y9bijAyuXMlbCs9ttR5X1DOGzK-yq353zS70X01M9hY/edit?usp=sharing), [`пастбин`](https://pastebin.com/VX5K9NW7), [`гист`](https://gist.github.com/nightloli/36a6ac3558449452b121db030c86ee27).

Флаги, скорее всего, заслуженно, не описанные в статьях выше:

Для 1.7.10 **-Dforge.forceNoStencil=true** — [Источник](https://www.reddit.com/r/feedthebeast/comments/2g6c13/ways_to_optimize_performance_for_1710_packs/ckg5c1k/)

**-XX:+UseStringDeduplication** — сборщик мусора будет пытаться экономить память, уничтожая повторяющиеся строки

**-XX:-DontCompileHugeMethods** — отключает лимит джавы на длинну методов, которые она может скомпилировать

**-server** — тот флаг, для которого тебе точно понадобится серверная версия джавы или JDK, анон! Виртуальная машина джавы будет использовать больше оптимизаций при компиляции байткода в обмен на дольшее время для 'разогрева'. 

**-Dorg.lwjgl.util.NoChecks=True** — отключает state tracking и дополнительные проверки во время игры.


## Оптимизация с помощью модов

С помощью модификаций можно добавлять не только килотонны нового контента, но и заставлять игру работать быстрее.  

---
### Оптимизация новейшей версии

| Мод | Описание |
|---|---|
|OptiFine| |
|Phosphor| |
|Lithium| |
|OptiFabric| |
> **TIP:** В новейших версиях (1.14+) появился новый мод-лоадер: `Fabric`. Он смог составить конкуренцию всем привычному Forge, что является показателем и огромным достижением, и к фабрику уже тоже имеются оптимизационные моды.  

---

### Оптимизация 1.12.2
|Мод|Описание|
|---|---|
|OptiFine|Добавьте описание|
|FoamFix|Добавьте описание|
|AI Improvements|Добавьте описание|
|Surge|Добавьте описание|
|Multithreaded Noise|Добавьте описание|
|Performant|Добавьте описание|
|Unloader|Добавьте описание|
|TexFix|Добавьте описание|
|Phosphor|Добавьте описание|
|BetterFps|де-факто аналог оптифайна по функционалу. нужен ли он тут?|
|VanillaFix|Добавьте описание|
|Chunk-Pregenerator|Добавьте описание|
|Clumps|Добавьте описание|

---

### Оптимизация 1.7.10
|Мод|Описание|
|---|---|
|OptiFine|Добавьте описание|
|BetterFps|де-факто аналог оптифайна по функционалу. нужен ли он тут?|
|Chunk-Pregenerator|Добавьте описание|
|FastCraft|Добавьте описание|

> **TIP:** Некоторые моды имеют возможность отключить особо тяжёлый функционал, и снизив тем самым нагрузку на ПК.  
(для редакторов: нужно написать про пару модов в качестве примера.)

## Прочие оптимизации

### **Обновление библиотек для старых версий**

Если ты играешь в версию майнкрафта ниже 1.12.2, у тебя могут быть недостаточно новые версии библиотек. В новых, как правило, лучше производительность, поэтому имеет смысл обновить их.

Скачайте майнкрафт версии 1.12.2 и замените файлами из директорий minecraft/libraries/org/lwjgl/lwjgl .minecraft/libraries/java3d/vecmath и .minecraft/versions/Forge 1.12.2/natives такие же файлы в более старой версии. Именно замените новыми файлами старые, используя такое же название!
(для редакторов: способ весьма странный, разве что для форджа выглядит логично. Разве не все версии используют одинаковые библиотеки?)

### **Отключение логов**

Если ты — счастливый обладатель медленного HDD в 2020 году, то может помочь отключение логгирования в майнкрафте. Для этого допишите в комманду запуска **`-Dlog4j.configurationFile=log4j2.xml`** создайте в корне с игрой файл **`g4j2.xml`** со следующим содержанием:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="ERROR" packages="com.mojang.util">
    <Loggers>
        <Root level="OFF" additivity="false">
        </Root>
    </Loggers>
</Configuration>
```

### **Ram-диск**

Если у тебя ещё остаётся оперативная память, после запуска майнкрафта, ты можешь перенести мир на ram-диск. Также я слышал слух, про то, что имеет смысл перенести JVM на рамдиск и пользуюсь этим советом, но доказательств пользы у меня нет. (для редакторов: возможно это может принести больше вреда, чем пользы, ведь во время загрузки новых чанков оперативы будет становиться всё меньше и меньше, и рано или поздно выкинет OutOfMemoryException. ВОЗМОЖНО.)

> **TIP:** Не пользуйтесь фичей, если собираетесь прегенерировать чанки! Оперативная память закончится моментально. Сейв, с оверворлдом, прогруженным на радиус ~300 чанков, запросто съедает больше гигабайта места!

В Linux используется tmpfs и автобекап. [Этот гайд](https://wiki.archlinux.org/index.php/Improving_performance#Relocate_files_to_tmpfs) хоть и находится на вики арча, но подойдёт для 99% линуксов.

Для Windows есть [огромный зоопарк](https://en.wikipedia.org/wiki/List_of_RAM_drive_software#Microsoft_Windows) какого-то софта для рамдисков, тот, кто сейчас это пишет, не может ничего порекомендовать из него.