# IncClocks
**Плагин на цифровые часы из блоков для конкурса плагинов от _BeBr0_**
- **Версия:** _1.20_
- **Автор:** _Jone501_

## Информация
**IncClocks** - это плагин, добавляющий цифровые часы, таймеры и секундомеры, которые можно легко настроить под свои нужды! Вы можете использовать любые шрифты, форматирование, настройки размера символов и т.д., чтобы разнообразить текст на часах, а также можете настроить корпус часов начиная с материалов, из которого он состоит, и заканчивая внутренним отступом и скруглением краёв!!!

## Структура
При запуске, плагин создаёт папку `plugins/IncClocks`, в которой будут находиться все файлы плагина. Эта папка содержит:

- Папку `fonts`, в которой будут находиться доступные шрифты формата _**.ttf**_
- Папку `clocks`, в которой будут находиться конфиги с настройками часов
- Папку `stopwatches`, в которой будут находиться конфиги с настройками секундомеров
- Папку `timers`, в которой будут находиться конфиги с настройками таймеров
- Папку `actions`, в которой будут находиться кастомные скрипты действий, совершаемых при остановке таймеров

Все эти папки, а так же их содержимое будет подробнее рассмотренно ниже

## Шрифты
Плагин может отображать текст с абсолютно любым шрифтом формата _**.ttf**_. Чтобы использовать свой шрифт, его нужно переместить в папку `fonts`, после чего его можно будет указать в настройках часов, таймеров и секундомеров, указав в параметре `text.font` название файла шрифта (без расширения _.ttf_)

## Часы
В папке `clocks` вы можете создавать шаблоны часов. Позднее вы сможете по этим шаблонам создавать часы в любой точке своего мира используя команду [_**incclocks place clocks <название>**_](#incclocks-place-clockstimerstopwatch-название)

### Конфиг
```yaml
time-type: REAL # REAL - реальное время | GAME - игровое время
time-zone: 0 # часовой пояс относительно локального времени сервера (только в режиме REAL)

# %h - часы
# %m - минуты
# %s - секунды (только в режиме REAL)
# ${block} - изменить материал следующих символов
format: '${LIME_CONCRETE}%h:%m' # текст, выводимый на дисплей

# настройки текста
text:
  offset: 0 # общий сдвиг текста
  # или
  offset:
    x: 0 # горизонтальный сдвиг текста
    y: 0 # вертикальный сдвиг текста
  font: Nunito # шрифт
  text-size: 16 # размер текста
  letter-spacing: -8 # межсимвольный интервал

# настройки материалов
materials:
  back: BLACK_CONCRETE # блок заднего фона текста
  sides: GRAY_CONCRETE # блок стенок корпуса

# настройки формы
form:
  padding: 0 # общий внутренний отступ
  # или
  padding:
    horizontal: 0 # горизонтальный внутренний отступ
    vertical: 0 # вертикальный внутренний отступ
  border-radius: 5 # скругление углов
  width: 5 # ширина
```
### Взаимодействие
_Доступно только игрокам с привелегией **incclocks.admin**_

При клике по часам левой кнопкой мыши открывается меню, в котором вы можете удалить часы

## Секундомер
В папке `stopwatches` вы можете создавать шаблоны секундомеров. Позднее вы сможете по этим шаблонам создавать секундомеры в любой точке своего мира используя команду [_**incclocks place stopwatch <название>**_](#incclocks-place-clockstimerstopwatch-название)

### Конфиг
```yaml
time-type: REAL # REAL - реальное время | GAME - игровое время

# %d - дни
# %h - часы
# %m - минуты
# %s - секунды (только в режиме REAL)
# ${block} - изменить материал следующих символов
format: '${LIME_CONCRETE}%h:%m' # текст, выводимый на дисплей

# настройки текста
text:
  offset: 0 # общий сдвиг текста
  # или
  offset:
    x: 0 # горизонтальный сдвиг текста
    y: 0 # вертикальный сдвиг текста
  font: Nunito # шрифт
  text-size: 16 # размер текста
  letter-spacing: -8 # межсимвольный интервал

# настройки материалов
materials:
  back: BLACK_CONCRETE # блок заднего фона текста
  sides: GRAY_CONCRETE # блок стенок корпуса

# настройки формы
form:
  padding: 0 # общий внутренний отступ
  # или
  padding:
    horizontal: 0 # горизонтальный внутренний отступ
    vertical: 0 # вертикальный внутренний отступ
  border-radius: 5 # скругление углов
  width: 5 # ширина
```
### Взаимодействие
_Доступно только игрокам с привелегией **incclocks.admin**_

При клике по секундомеру левой кнопкой мыши открывается меню, в котором вы можете запустить, остановить или удалить секундомер

## Таймер
В папке `timers` вы можете создавать шаблоны таймеров. Позднее вы сможете по этим шаблонам создавать таймеры в любой точке своего мира используя команду [_**incclocks place timer <название>**_](#incclocks-place-clockstimerstopwatch-название)

### Конфиг
```yaml
time-type: REAL # REAL - реальное время | GAME - игровое время

# %d - дни
# %h - часы
# %m - минуты
# %s - секунды (только в режиме REAL)
# ${block} - изменить материал следующих символов
format: '${LIME_CONCRETE}%h:%m' # текст, выводимый на дисплей
actions: [] # действия, выполняемые при остановке таймера (см. Действия)

# формат: 1d|2h|...|10m
# xd - x дней
# xh - x часов
# xm - x минут
# xs - x секунд (только в режиме REAL)
time: 1h # время таймера

# настройки текста
text:
  offset: 0 # общий сдвиг текста
  # или
  offset:
    x: 0 # горизонтальный сдвиг текста
    y: 0 # вертикальный сдвиг текста
  font: Nunito # шрифт
  text-size: 16 # размер текста
  letter-spacing: -8 # межсимвольный интервал

# настройки материалов
materials:
  back: BLACK_CONCRETE # блок заднего фона текста
  sides: GRAY_CONCRETE # блок стенок корпуса

# настройки формы
form:
  padding: 0 # общий внутренний отступ
  # или
  padding:
    horizontal: 0 # горизонтальный внутренний отступ
    vertical: 0 # вертикальный внутренний отступ
  border-radius: 5 # скругление углов
  width: 5 # ширина
```
### Взаимодействие
_Доступно только игрокам с привелегией **incclocks.admin**_

При клике по таймеру левой кнопкой мыши открывается меню, в котором вы можете запустить, сбросить или удалить таймер

## Команды
_Команды доступны только игрокам с привелегией **incclocks.admin**_
### incclocks help
**_Помощь по командам_**
### incclocks reload
**_Перезагрузка плагина и обновление часов, таймеров и секундомеров_**
### incclocks place <clocks|timer|stopwatch> <название>
**_Установка часов/таймера/секундомера по шаблону `название.yml`_**

При вводе команды у вас появится предпросмотр будущего положения объекта, отображаемый при помощи частиц. Установить часы можно только если на месте будущих часов не находятся блоки. Если установка невозможна из-за мешающих блоков, то частицы будут красные. В противном случае они будут зелёными.

Устанавливать объект можно только на твёрдые блоки и только в радиусе 100 блоков, в противном случае предпросмотр не будет отображаться, а установка будет невозможна. Пока идёт установка, вы не можете ломать, ставить и вообще как либо взаимодействовать с блоками

- Чтобы отменить установку, нужно нацелиться на нетвёрдый блок (или в небо) или на блок, находящийся дальше 100 блоков и нажать **ЛКМ**
- Если нажать **ЛКМ**, будучи наведённым на блок в радиусе 100 блоков, то можно поворачивать объект на 90 градусов против часовой стрелки (Только в горизонтальной плоскости! В противном случае поворот не окажет никакого эффекта).
- Если нажать **ЛКМ + SHIFT** и территория не будет содержать мешающих блоков (частицы должны быть зелёными), то установка будет завершена, а объект будет размещён в мире. В противном случае процесс установки продолжится
- Если во время установки игрок отключится от сервера, процесс установки будет отменён