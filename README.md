# Локации с высоким уровнем загрязнения окружающей среды (Москва)
![header pic]

[1. Введение](#1-введение "вступление")

[2. Необходимые модули](#2-необходимые-модули "подключаемые модули")

[3. Dataset](#3-dataset "описание dataset'а")

[3.1. Источники данных](#31-источники-данных "описание источников данных")

[3.2. Автоматические станции контроля загрязнения атмосферы](#32-автоматические-станции-контроля-загрязнения-атмосферы "описание стационарных и модильных станций контроля")

[3.3. Карта расположения автоматических станций](#33-карта-расположения-автоматических-станций "карта, с отображением мест размещения автоматических станций контроля")

[3.4. Изменение формата данных](#34-изменение-формата-данных "описание результирующего формата данных")

[3.5. Тепловая карта локаций с высоким уровнем загрязнения окружающей среды](#35-тепловая-карта-локаций-с-высоким-уровнем-загрязнения-окружающей-среды "визуализация локаций с высоким уровнем загрязнения")

[3.6. Тепловая карта локаций с экологически благоприятной средой](#36-тепловая-карта-локаций-c-экологически-благоприятной-средой "визуализация локаций с экологически благоприятной средой")


## 1. Введение
<details>
<summary>Click this to collapse/fold.</summary>

These details _remain_ **hidden** until expanded.

```
PASTE LOGS HERE
```

</details>

## 2. Необходимые модули
* pandas *- для работы с источниками данных*  
* numpy  
* matplotlib *- для визуализации графиков* 
* datetime  
* folium *- для визуализации зон на карте* 


## 3. Dataset

### 3.1. Источники данных

В качестве источников данных использовались данные департамента природопользования и охраны окружающей среды города Москва:
1.  [Автоматические станции контроля загрязнения атмосферы.](#автоматические-станции-контроля-загрязнения-атмосферы)
2.  [Данные передвижной лаборатории контроля загрязнения атмосферного воздуха.](#данные-передвижной-лаборатории-контроля-загрязнения-атмосферного-воздуха)
3.  [Среднемесячные показатели загрязнения атмосферного воздуха](#среднемесячные-показатели-загрязнения-атмосферного-воздуха)
4.  [Экологическая карта районов Москвы](#экологическая-карта-районов-москвы)

#### Автоматические станции контроля загрязнения атмосферы
Формат: [CSV](https://data.mos.ru/opendata/7704221753-parametry-zagryazneniya-atmosfernogo-vozduha/passport?versionNumber=1&releaseNumber=45 "Паспорт набора данных портала открытых данных Правительства Москвы")

Набор данных содержит информацию о местах расположения автоматических станций контроля загрязнения атмосферы (АСКЗА) на территории Москвы.

В Москве функционирует  современная, на уровне европейских городов и мировых мегаполисов система экологического мониторинга атмосферного воздуха, представленная сетью АСКЗА, которая создана с соблюдением нормативных требований РФ и директив Европейского Союза.

АСКЗА - это автоматические станции контроля загрязнения атмосферы, функционирующие в круглосуточном непрерывном автоматизированном режиме. Автоматизированные измерения – это современный и эффективный подход, реализованный в крупных городах мира, который позволяет оперативно выявлять сверхнормативные загрязнения атмосферного воздуха, практически исключает статистические ошибки оценки средних значений и обеспечивает высокую достоверность данных. Приборы на АСКЗА регулярно калибруются, а также проходят межлабораторные сравнительные испытания при участии лабораторий стран Европейского региона Всемирной организации здравоохранения.

АСКЗА расположены во всех округах Москвы, на разном удалении от центра города и охватывают различные функциональные зоны. Станции мониторинга размещаются на территориях вблизи автомагистралей, в том числе на Третьем транспортном кольце, на жилых территориях, находящихся под влиянием смешанных антропогенных источников загрязнений, природных территориях. Также организован мониторинг атмосферного воздуха на территории «новой» Москвы.

Всего на территории г. Москвы размещены 43 АСКЗА:

| Административный округ | Количество станций АСКЗА |
| ------ | ------ |
|Центральный АО | 5 | 
|Северный АО| 5 |
|Северо-Восточный АО| 2|
|Восточный АО| 4|
|Юго-Восточный АО| 4|
|Южный АО |6|
|Юго-Западный АО| 3|
|Западный АО|  3|
|Северо-Западный АО|  2|
|Зеленоградский АО|  3|
|Новомосковский АО| 2|
|Троицкий АО|  4|
АСКЗА в круглосуточном непрерывном режиме измеряют содержание в атмосферном воздухе основных загрязняющих веществ, характерных для выбросов антропогенных источников Москвы, а также метеопараметры, определяющие условия рассеивания примесей в атмосфере.

Характерные для выбросов большинства антропогенных источников загрязняющие вещества, такие как оксид углерода, диоксид азота, оксид азота, сумма углеводородных соединений, озон, диоксид серы, контролируются на всей территории города. Содержание таких загрязняющих веществ, как сероводород и аммиак, контролируется на территориях, находящихся под воздействием очистных сооружений и нефтеперерабатывающего завода. На Третьем транспортном кольце, кроме основных параметров, характерных для выбросов автотранспорта, измеряются специфические загрязняющие вещества (формальдегид, фенол, бензол). Организован мониторинг взвешенных частиц РМ10 и РМ2.5, отнесенных Всемирной организацией здравоохранения к приоритетным по уровню воздействия на здоровье.

Ниже представлена информация о перечне загрязняющих веществ, контролируемых с помощью автоматических станций контроля загрязнения атмосферного воздуха на территории Москвы, значениях ПДКмр и ПДКсс, установленных санитарными нормами классификации опасных веществ.

В Российской Федерации санитарными нормами и правилами для атмосферного воздуха населенных мест установлены нормативы более чем для 1000 загрязняющих веществ. Многие из  них содержатся в выбросах производств, отсутствующих на территории города, и в атмосферном воздухе города Москвы никогда не встречаются.

Для Москвы, как и для большинства крупных мегаполисов мира,  характерными источниками выбросов в атмосферу являются автотранспорт, предприятия теплоэнергетики, производство строительных материалов, включая асфальто-бетонные заводы, городские очистные сооружения, нефтеперерабатывающий завод (на юго-востоке города) и другие.

Учитывая схожесть характерных для городов источников выбросов, Всемирная организация здравоохранения (ВОЗ) выделила перечень приоритетных загрязняющих веществ, контроль которых необходимо осуществлять в городах. Это  оксиды азота, оксид углерода, диоксид серы, озон, мелкие взвешенные частицы, полициклические ароматические углеводороды.  Для Москвы, учитывая выбросы городских очистных сооружений и нефтеперерабатывающего производства,  перечень приоритетных веществ был дополнен  сероводородом, метаном и аммиаком.

В настоящий момент на территории Москвы в непрерывном круглосуточном режиме контролируется содержание в атмосферном воздухе загрязняющих веществ, характерных для выбросов автотранспорта и промышленных предприятий города Москвы. Надо отметить, что это практически все загрязняющие вещества, для которых разработаны надежные автоматизированные методы контроля содержания в атмосферном воздухе.

Для оценки качества воздуха используются нормативные значения содержания загрязняющих веществ, ниже которых качество воздуха считается приемлемым и неопасным для здоровья людей. В настоящее время в мире единой позиции по данным нормативам нет. В Российской Федерации для загрязняющих веществ установлено 2 вида нормативов:

ПДКмр - предельно допустимая максимальная разовая концентрация химического вещества в воздухе населённых мест, мг/м3. Эта концентрация при вдыхании в течение 20-30 мин. не должна вызывать рефлекторных реакций в организме человека.

ПДКсс — предельно допустимая среднесуточная концентрация химического вещества в воздухе населённых мест, мг/м3. Эта концентрация не должна оказывать на человека прямого или косвенного воздействия при неопределённо долгом (годы) вдыхании.

Также в датасете представлена информация о классах опасности контролируемых загрязняющих веществ. Класс опасности – показатель, характеризующий степень опасности для человека веществ, загрязняющих атмосферный воздух. Вещества делятся на следующие классы опасности:
| Название параметра | Единицы измерения | ПДК максимальное | ПДК среднесуточное | Класс опасности |
| ------ | ------ | ------ | ------ | ------ |
|`Оксид углерода` | мг/м3 | 5 | 3 | 4 |
| `Диоксид серы` | мг/м3 |  0.5 | 0 | 3 |
| `Аммиак` | мг/м3 | 0.2 | 0 | 4 |
| `Сероводород` | мг/м3 | 0 |  | 2 |
| `Озон` | мг/м3 | 0.16 | 0 | 1 |
| `Метан` | мг/м3 | 50 |  |  |
| `Формальдегид` | мг/м3 | 0 | 0 | 2 |
| `Бензол` | мг/м3 | 0.3 | 0.1 | 2 |
| `Сумма углеводородных соединений за вычетом метана` | мг/м3 |  |  |  |
| `Диоксид азота` | мг/м3 | 0.2 | 0 | 3 |
| `Сумма углеводородных соединений` | мг/м3 |  |  |  |
| `Толуол` | мг/м3 | 0.6 |  | 3 |
| `Оксид азота` | мг/м3 | 0.4 | 0 | 3 |
| `Фенол` | мг/м3 | 0 | 0 | 2 |
| `Нафталин` | мг/м3 | 0 |  | 4 |
| `Взвешенные частицы РМ10` | мг/м3 | 0.3 | 0 |  |
| `Стирол` | мг/м3 | 0 | 0 | 2 |
| `Кислород` | % |  |  |  |
| `Диоксид углерода` | ppm |  |  | 2 |
| `Взвешенные частицы РМ2.5` | мг/м3 | 0.16 | 0 |  |
| `Взвешенные частицы РМ10 (суточные измерения)` | мг/м3 |  | 0 |  |
| `Взвешенные частицы РМ2.5 (суточные измерения)` | мг/м3 |  | 0 |  |


Нормативы и классы опасности загрязняющих веществ разработаны на основании комплексных токсиколого-гигиенических и эпидемиологических исследований с учетом международного опыта и утверждены  ГН 2.1.6.1338-03 «Предельно допустимые концентрации (ПДК) загрязняющих веществ в атмосферном воздухе населенных мест».

#### Данные передвижной лаборатории контроля загрязнения атмосферного воздуха
Формат: [CSV](https://data.mos.ru/opendata/7704221753-dannye-peredvijnoy-laboratorii-kontrolya-zagryazneniya-atmosfernogo-vozduha/passport?versionNumber=1&releaseNumber=43 "Паспорт набора данных портала открытых данных Правительства Москвы")

Набор данных позволяет получить информацию о месте отбора проб атмосферного воздуха, дате проведения отбора, основных результатах исследования. Для удобства ориентирования предусмотрена возможность просмотра местоположения контрольной точки исследования атмосферного воздуха на карте города Москвы.

Передвижная лаборатория – это автомобиль, оснащенный современным оборудованием, которое позволяет измерять загрязняющие вещества в режиме реального времени по основным загрязняющим веществам и отбирать пробы воздуха для последующего анализа в лаборатории на расширенный перечень веществ.

#### Среднемесячные показатели загрязнения атмосферного воздуха
Формат: [CSV](https://data.mos.ru/opendata/7704221753-srednemesyachnye-pokazateli-zagryazneniya-atmosfernogo-vozduha/passport?versionNumber=2&releaseNumber=41 "Паспорт набора данных портала открытых данных Правительства Москвы")

Набор данных содержит информацию о средних за месяц концентрациях загрязняющих веществ в атмосферном воздухе Москвы, измеряемых автоматическими станциями контроля загрязнения атмосферы (АСКЗА).

Датасет позволяет получить информацию в разрезе каждой отдельной АСКЗА о средних за месяц концентрациях загрязняющих веществ в абсолютных единицах и в сравнении с предельно допустимыми среднесуточными концентрациями.

Основу мониторинга атмосферного воздуха города Москвы составляет сеть стационарных АСКЗА, которые в круглосуточном непрерывном режиме (с периодичностью один раз в двадцать минут) измеряют содержание в атмосферном воздухе загрязняющих веществ, характерных для выбросов автотранспорта и промышленных предприятий города Москвы.

Сеть автоматических станций мониторинга атмосферного воздуха включает в себя стационарные станции, место размещение которых сохраняется постоянно на протяжении долгого времени, и мобильные станции, размещаемые временно для решения локальных задач (выявление источника загрязнения, определение эффективности природоохранных мероприятий и т.д.).

Датасет включает информацию по стационарным АСКЗА, постоянность размещения которых на одной территории позволяет контролировать динамику содержания загрязняющих веществ в долговременной перспективе.

При ознакомлении с данными датасета важно учитывать, что АСКЗА в системе мониторинга атмосферного воздуха города Москвы ориентированы на контроль загрязнения воздуха на территориях различного функционального назначения: территории вблизи автомагистралей, жилые территории, находящиеся под влиянием смешанных антропогенных источников загрязнений; природные территории, «новая» Москва.

Перечень загрязняющих веществ на АСКЗА определяется функциональным назначением контролируемой территории. Наибольшее количество загрязняющих веществ измеряется вблизи автотрасс и на территориях, находящихся под воздействием очистных сооружений и нефтеперерабатывающего завода.

В общем, список измеряемых на станции загрязняющих веществ может широко варьироваться от 3-х основных параметров (оксид углерода, диоксид и оксид азота) до 10, включая специфические, такие как сероводород (индикатор выбросов нефтехимических производств и эмиссии очистных сооружений канализации).

Среднемесячные концентрации контролируемых параметров представлены как в абсолютных единицах (мг/м3), так и в долях ПДКсс (предельно допустимая среднесуточная концентрация химического вещества в воздухе населённых мест). Концентрация кислорода (О2) выражена в процентной плотности (%).

#### Экологическая карта районов Москвы
[Источник](https://mwmoskva.ru/ekologicheskaya-karta-moskvy.html "Справочник с интерактивной картой") 
Формат: [JSON](https://mwmoskva.ru/js/eco.json "Прямая ссылка на слой")

Предприятия-загрязнители окружающей среды.
  

 
### 3.3. Карта расположения автоматических станций

### 3.6. Тепловая карта локаций с экологически благоприятной средой

![good place pic]

   [good place pic]: <gut_place_heatmap.png>
   [header pic]: <https://live.staticflickr.com/5016/5492243495_b296955bc9_k_d.jpg> 
   Header Pic "Smoke" by Tree Leaf Clover is licensed with CC BY 2.0. To view a copy of this license, visit https://creativecommons.org/licenses/by/2.0/
