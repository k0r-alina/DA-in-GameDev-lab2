# DA-in-GameDev-lab2
Отчет по лабораторной работе #2 выполнил(а):
- Корепова Алина Вадимовна
- НМТ-233719
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Научиться передавать в Unity данные из Google Sheets с помощью Python.

## Задание 1
###  Выберите одну из игровых переменных в игре СПАСТИ РТФ: Выживание (HP, SP, игровая валюта, здоровье и т.д.), опишите её роль в игре, условия изменения / появления и диапазон допустимых значений. Постройте схему экономической модели в игре и укажите место выбранного ресурса в ней.
Ход работы:
- Выбрана переменная HP в игре СПАСТИ РТФ: Выживание, описана её роль условия изменения / появления и диапазон допустимых значений. Построена схема экономической модели в игре и указано место выбранного ресурса в ней.
Переменная HP в игре СПАСТИ РТФ: Выживание

Health Points (HP) — это количественное значение, которое отображает уровень здоровья или жизненных сил персонажа в компьютерных играх. 
Роль переменной Health Points в игре СПАСТИ РТФ: Выживание состоит в том, что она является ключевым параметром для определения выживаемости персонажа в игре. Когда здоровье персонажа опускается до нуля, персонаж умирает или проигрывает. Изначально уровень здоровья составляет 30 очков, но может быть увеличен за счет приобретения улучшений. Противники при попадании отнимают 10 очков от уровня здоровья, однако одновременно могут ударить сразу несколько противников. Поэтому игрокам важно следить за уровнем здоровья своего персонажа, избегать урон и стараться восстанавливать здоровье с помощью аптечек, улучшений или других источников. 
В целом, переменная Health Points играет важную роль в играх, определяя выживаемость персонажа, а также требуя от игрока стратегического подхода к управлению здоровьем.

Схема экономической модели в игре с указанием HP
![image](https://github.com/user-attachments/assets/6f04f048-bef7-4c7c-926b-2c7292d497b4)




## Задание 2
### С помощью скрипта на языке Python заполните google-таблицу данными, описывающими выбранную игровую переменную в игре “СПАСТИ РТФ:Выживание”. Средствами google-sheets визуализируйте данные в google-таблице (постройте график / диаграмму и пр.) для наглядного представления выбранной игровой величины. Опишите характер изменения этой величины, опишите недостатки в реализации этой величины (например, в игре может произойти условие наступления эксплойта) и предложите до 3-х вариантов модификации условий работы с переменной, чтобы сделать игровой опыт лучше.
Ход работы: 
- С помощью скрипта на языке Python заполнена google-таблицу данными, описывающими выбранную игровую переменную HP в игре “СПАСТИ РТФ:Выживание”. Средствами google-sheets визуализированны данные в google-таблице для наглядного представления выбранной игровой величины. Описан характер изменения этой величины, описаны недостатки в реализации этой величины и предложены до варианты модификации условий работы с переменной, чтобы сделать игровой опыт лучше.

```py

import gspread
import numpy as np
gc = gspread.service_account(filename='unitydatascience-445500-1adbd8f9b4f1.json')
sh = gc.open("UnityWorkshop2")
HP = 30
i = 0
while HP >= 0:
    i += 1
    HPBar = HP
    sh.sheet1.update(('A' + str(i)), i)
    sh.sheet1.update(('B' + str(i)), HP)
    print(HPBar)
    HP -= 10
```
https://docs.google.com/spreadsheets/d/1RSUVnzZQFFT3bl_iHXRs4Xz-09lavIW9PzWkmnlBtDY/edit?gid=0#gid=0
![image](https://github.com/user-attachments/assets/c4c055a8-f8dd-48ae-b124-d4c042b7bf85)

Характер изменения величины Health Point

Изначально у игрока 30 очков здоровья. С помощью улучшений уровень здоровья можно поднять, за покупку одного улучшения уровень здоровья увеличивается на 10. Так же здоровья можно восстановить за приобретение соответственного улучшения или постепенно за счет приобретения навыка, дающего несколько очков здоровья за попадание или устранение противника. Противники при попадании отнимают 10 очков здоровья. При достижении 0 игра заканчивается.
Недостатки
Несколько врагов могут нанести урон здоровью одновременно, из-за чего игра может быстро закончится. Навык вампиризм восстанавливает мало здоровья при его последующем улучшении.
Предложения
Ввести некоторые время неуязвимости после получении урона для лучшего баланса.
Сбалансировать навыки, восстанавливающие здоровье.
Добавить механику последнего шанса, когда игрок, чье здоровье опустилось до нуля, получает возможность получить очки здоровья за выполнение каких-либо действий.

## Задание 3
### Настройте на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. Например, если выбрано здоровье главного персонажа вы можете выводить сообщения, связанные с его состоянием.
![image](https://github.com/user-attachments/assets/1100165d-29f5-4201-94c2-dd9dbe900644)



## Выводы
Я научилась передавать в Unity данные из Google Sheets с помощью Python.
## Powered by

**Алина
