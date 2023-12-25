## Моделирование кривой процентных ставок и сравнение подходов

# План по проекту 

1. Изучить классические модели построения кривой % ставок:
   - Бутстрэп моделей
   - Нельсона - Зигеля
   - Модель G - кривой (использует ММВБ)

2. Описать проблематику:
   - выбраать облигации
   - восстановить кривую % ставок
3. Реализация:
   - на рыночных данных обучить и проверить качество модели
4. Результат:
   - выбрать модель с лучшим качеством 

# Введение 

Проблема моделирования структуры процентных ставок на практике и в теории имеет долгую историю и продолжает привлекать внимание. Различные ученые, такие как Дж. М. Кейнс, П. Самуэльсон, Р. Мертон, Ф. Модильяни, М. Шоулз, Е. Фама и другие, в разное время занимались этим вопросом. Несмотря на значительные успехи, проблема создания моделей, которые достоверно отражали бы реальные условия, по-прежнему далека от окончательного решения и требует дальнейших исследований [4, Лукасевич, 2016].

Анализ литературы [3, 4, 5] позволяет нам выделить следующие направления использования модели кривой процентных ставок:
   - прогнозирование и оценка текущих и будущих экономических условий;
   - индикатор ожиданий рынка относительно будущей инфляции;
   - оценка стоимости кредитования, доступности кредитных ресурсов, состояния ликвидности в банковском секторе;
   - бенчмарк при принятии инвестиционных решений;
   - используется для определения справедливой стоимости облигаций, расчета кредитных спредов, актуарного оценивания и других задач риск-менеджмента и финансовой инженерии.

Наилучшим образом модели кривой процентных ставок подходят для рынка облигаций правительства США, для которого свойственно «большое число ликвидных выпусков, на развивающихся рынках ситуация с ликвидностью облигаций обстоит сложнее. Облигации торгуются в неоднородных объемах, в данных по котировкам часто встречаются пропуски, а иногда на рынке просто нет достаточного количества выпусков для оценки срочной структуры процентных ставок» [5, Макушкин, Лапшин, 2021]. Построение кривой процентных ставок для Еврозоны осложняется необходимостью использования облигаций разного кредитного качества, связанного неоднородностью эмитентов [6, Смирнов и др., 2007].

Перечисленные выше ограничения «ведут к возникновению неадекватных результатов при применении численных процедур, а иногда и к невозможности их применения. Решение этой проблемы может быть достигнуто двумя способами: либо за счет учета в модели возможности наличия пропущенных данных и сделок, выделяющихся на фоне основного количества нетипичными значениями или объемами, либо за счет проведения процедуры предварительной подготовки данных» [2, Косьяненко, 2007].

# Сфера применения моделей 

Разработка достоверных методов моделирования срочной структуры процентных ставок и их применение имеют огромную важность для всех участников финансового рынка. Центральные банки используют срочную структуру для прогнозирования и оценки текущих и будущих экономических условий. Кривая доходности облигаций является индикатором ожиданий рынка относительно будущей инфляции и позволяет оценить экономическую стабильность. Точные оценки кривой доходности необходимы для эффективной денежно-кредитной политики центральных банков.

Кроме того, с помощью срочной структуры можно оценить стоимость кредитования, доступность кредитных ресурсов, состояние ликвидности в банковском секторе и другие аспекты экономической ситуации. Кривые доходности являются основой теории оценки активов с фиксированным доходом и играют важную роль при принятии инвестиционных решений. Они используются для определения справедливой стоимости облигаций, расчета кредитных спредов, актуарного оценивания и других задач риск-менеджмента и финансовой инженерии. Также с помощью срочной структуры можно разрабатывать инвестиционные стратегии, учитывая срочность заимствования, уровень риска, хеджирование и оценку спекулятивных стратегий.

Таким образом, срочная структура процентных ставок позволяет глубоко исследовать финансовый рынок и его состояние. Она является неотъемлемым инструментом для всех участников финансового рынка, обеспечивая надежные прогнозы и помогая принимать обоснованные решения.
# Порядок выбора подходящей модели

В финансовой сфере часто необходимо оценивать риск и доходность актива в будущем, исходя из текущих условий. Проблема моделирования срочной структуры состоит в том, чтобы как можно лучше описать кривую доходности с учетом рыночных цен финансовых инструментов и обещанных денежных потоков по ним. Эта задачу довольно трудно выполнить для условий, близких к реальности. Одним из препятствий для подобной оценки является отсутствие достаточного объема данных.

Для построения кривой бескупонной доходности обычно используются облигации с нулевым купоном и ставки денежного рынка. Если на рынке нет желаемого количества бескупонных облигаций, то они могут быть искусственно сконструированы, когда каждая купонная облигация рассматривается как портфель бескупонных облигаций. А на рынках, где в краткосрочной перспективе недостаточно ликвидности, используются и ставки межбанковского денежного рынка. 

На практике может также возникнуть необходимость в извлечении спот-ставок из более сложных ценных бумаг, например, свопов и соглашений о форвардной ставке (FRA). Прибегают и к таким рыночным инструментам, как денежные депозиты и фьючерсы.

После определения выборки облигаций, нужной для построения срочной структуры процентных ставок, инвестор может воспользоваться одним из подходов к ее построению. Так, методы оценки срочной структуры можно разделить на три больших класса: «инженерные», параметрические и сплайновые методы [3, Лапшин, Терещенко, 2018].

«Инженерные» методы не имеют четкого обоснования и в основном представляют собой определенную последовательность действий, которая должна приводить к результату, похожему на искомую кривую бескупонной доходности. Такие методы обычно не обладают теоретической базой, но они часто применяются в силу своей простоты. К ним относится метод последовательного определения процентных ставок – бутстрэп.

Параметрические методы предполагают, что кривая бескупонной доходности принадлежит к некоторому заранее выбранному классу параметрических функций. К ним прибегали еще в 1960-х гг., а в настоящее время это наиболее распространенный метод построения срочной структуры спот-ставок. Благодаря своей простоте широко используется модель Нельсона – Зигеля и ее расширение, предложенное Свенссоном.

Сплайновые методы предполагают, что истинная функция дисконтирования обладает некоторым свой- ством экстремума. Обычно это интерпретируется как максимальная гладкость по отношению к некоторому классу функций. Решение предстает в виде сплайна некоторой формы – функции, область определения которой разбита на конечное число отрезков, и на каждом она совпадает с некоторым алгебраическим многочленом. Эти методы сейчас также применяются очень часто.

Выбор модели оценки срочной структуры регулируется требованиями пользователя. Для этого необходимо определить ключевые критерии выбора модели. На данный момент не существует единых, общепринятых критериев для сравнения моделей оценки срочной структуры процентных ставок. Исследователи этой проблемы производят анализ по тем параметрам, которые считают наиболее подходящими в каждом конкретном случае. 

Будем исходить из того, что сравнение моделей вполне можно осуществлять по следующему набору критериев:
1) точность (величина стандартной ошибки);
2) гладкость (критерий максимума гладкости);
3) возникновение отрицательных форвардных ставок (наличие арбитража);
4) простота реализации (количество параметров);
5) гибкость (возможность включать дополнительные параметры, фиксируя изменения структуры);
6) стабильность (небольшие изменения в данных для одного срока погашения не оказывают непропорционального влияния на ставки для других сроков).
   
Два первых критерия – количественные, они определяются по данным рынка, а оставшиеся – качественные, отражают характеристики выбранной модели. Критерии 1–4 взяты из статьи Г. Гамбарова, И. Шевчука и А. Балабушкина «Оценка срочной структуры процентных ставок» [1, Гамбаров и др., 2004]. Критерии 5–6 отражены в заметке Дж. Слиса “New Estimates of the UK Term Structure of Interest Rates” [7, Sleath, 2001].

Выбранная модель обязательно должна отвечать требованиям точности и гладкости, что определяется экономическими соображениями. 

Точность имеет первостепенное значение для изучения ценообразования инструмента, но степень точности часто оказывается обратно пропорциональной уровню полезности полученной модели. Свойство гладкости основное при анализе рыночных ожиданий: определенная степень гладкости дает возможность исследовать форвардные процентные ставки на предмет ожидаемой динамики краткосрочной ставки и инфляции. 

Самой оптимальной будет такая срочная структура, которая максимально сочетает в себе эти два показателя. Однако на практике между ними чаще всего обнаруживается обратная связь.

Учитывая вышесказанное, можно попытаться подобрать такую модель, которая в наибольшей степени будет соответствовать поставленной перед исследователем задаче. 

# Используемые модели и их свойства 

# 1. Модель Нельсона – Зигеля

Одна из самых популярных на практике моделей была предложена Ч. Нельсоном и Э. Зигелем в 1987 г. Она хорошо интерпретирует параметры с экономической точки зрения, достаточно точно описывает имеющиеся данные, имеет мало параметров, поэтому очень компактна. Нельсон и Зигель поставили перед собой цель ввести в обращение как можно более простую модель с минимальным количеством параметров, которая была бы настолько гибкой, чтобы описать типичные в зависимости от рыночной ситуации формы кривой доходности: монотонную, выпуклую и S-образную [Nelson, Siegel, 1987].

<img width="412" alt="Снимок экрана 2023-12-08 в 16 21 07" src="https://github.com/MolchanovSergey/curve/assets/96715157/3432189f-8f97-4805-9607-16e91aea1800">

где t – срок до погашения облигации;
$\beta_0$, $\beta_1$, $\beta_2$, $\tau_1$ – подлежащие оценке неизвестные параметры.
Первый член уравнения – константа $\beta_0$ > 0, которую можно рассматривать как уровень кривой доходности. 
Вторая составляющая – экспоненциальный член $\beta_1\times exp(- \frac{t}{\tau_1})$, который задает наклон кривой
доходности (кривая монотонно убывает при $\beta_1$ > 0 и возрастает при $\beta_1$ < 0). Третья составляющая –
$\beta_2\times \frac{t}{\tau_1} \times exp(- \frac{t}{\tau_1})$, которая определяет форму кривой доходности («горб» при $\beta_2$ > 0 и U-образная форма при $\beta_2$ < 0). Константа $\tau_1$ > 0 показывает, при каком сроке до погашения «горб» функции достигает максимума [Svensson, 1994; Берзон, 2016].

В итоге получается семейство кривых форвардных ставок, которые принимают разные формы в зависимости от значений $\beta_1$ и $\beta_2$, а также имеют асимптоту $(\beta_0 + \beta_1)$ при t → 0 и $\beta_0$ при t → ∞ [Nelson, Siegel, 1987]. Такая горизонтальная асимптота позволяет избежать проблем с неустойчивыми оценками форвардных ставок большого срока погашения, которые часто наблюдаются при сплайн-методах [Svensson, 1995].
Важным преимуществом модели Нельсона – Зигеля является прямая трактовка ее параметров. Экономически интерпретировать коэффициенты модели можно как кратко-, средне- и долгосрочные компоненты кривой форвардных ставок, а, значит, и кривой доходности [Nelson, Siegel, 1987].

Путем интегрирования кривой форвардных ставок получают кривую непрерывно начисляемых спот-ставок r(t):

Кривая форвардных ставок f(t) задается с помощью следующего уравнения:

<img width="468" alt="Снимок экрана 2023-12-08 в 16 29 40" src="https://github.com/MolchanovSergey/curve/assets/96715157/f7da4e76-6a9e-407f-a409-e1dc95bd3aad">

Получившуюся регрессию лучше всего оценивать с помощью метода наименьших квадратов (МНК). Параметры модели определяются путем минимизации квадратов отклонения теоретических цен от наблюдаемых, и целевая функция принимает следующий вид:

<img width="422" alt="Снимок экрана 2023-12-08 в 16 32 14" src="https://github.com/MolchanovSergey/curve/assets/96715157/ace97524-074d-4566-872c-679260227e59">

Согласно данным Банка международных расчетов за 2005 г. метод Нельсона – Зигеля очень распространен в Центральных банках стран Европы. Он использовался для оценки срочной структуры процентных ставок в Бельгии, Финляндии, Франции, Италии и до 1995 г. в Испании [BIS Paper No 25, 2005]. Модель успешно зарекомендовала себя и на российском рынке.

# 2. Бутстрэп 

На рынках, где торгуется ограниченное число облигаций с нулевым купоном, обычно хватает купонных облигаций для применения стандартных процедур бутстрэпа. Так, по данным [Smit, 2000], в Южной Африке на рынке облигаций имеется очень мало ликвидных инструментов для построения кривой бескупонной доходности. 

При наличии на рынке страны достаточно большого разнообразия инструментов с различными сроками до погашения задачу построения кривой доходности можно решить с помощью бутстрэпа.

Практическая реализация бутстрэпа принципиально зависит от того, считаются ли доходности инструментов зависимыми или нет. Если предполагается их независимость, то используется стандартный бутстрэп (standard bootstrap). В противном случае применяют блочный бутстрэп (block bootstrap).

Стандартный бутстрэп – это достаточно простой метод, когда кривая бескупонной доходности рассчитывается рекуррентно, т.е. в порядке увеличения срока до погашения облигаций. Для каждого последующего шага верно:

<img width="148" alt="Снимок экрана 2023-12-08 в 14 50 37" src="https://github.com/MolchanovSergey/curve/assets/96715157/3b21ce5a-e960-4bcf-ac6d-d51686afd526">


<img width="318" alt="Снимок экрана 2023-12-08 в 14 52 42" src="https://github.com/MolchanovSergey/curve/assets/96715157/fab14425-5cb7-4876-8f21-58f6765ba82c">

Отсюда поочередно находим ставки $r_1$, $r_2$, $r_3$ и т.д.

Один из вариантов этого метода описали в своей работе Е. Фама и Р. Блисс [Fama, Bliss, 1987]. Данный метод не позволяет построить всю кривую целиком, но он дает возможность найти отдельные спот-ставки, необходимые для дальнейшей оценки.

Наибольшая эффективность бутстрэпа достигается, когда эмиссия облигаций происходит согласно долгосрочным программам выпусков, что присуще главным образом государственным и крупным институциональным заемщикам. Тогда облигации эмитируются регулярно в одни и те же даты, и купоны по облигациям, выпущенным в рамках одной программы, выплачиваются в один и тот же день. Этот метод можно применять для оценки облигаций с малым сроком до погашения только тогда, когда на рынке есть много сопоставимых ценных бумаг, которые выпускаются с определенной регулярностью [Берзон, 2016].

Чаще всего бутстрэп применяют для получения кривых доходности облигаций и свопов. Этот метод используется для ежедневного расчета кривых бескупонной доходности по казначейским облигациям США (US Treasuries) [Hull, 2015].

Финансовые инструменты, используемые при построении кривой, можно применить для хеджирования других инструментов [Hagan, West, 2008]. Изначально трейдер держит портфель более сложных инструментов. Тогда он будет иметь возможность хеджировать их против движений кривой доходности с помощью ликвидно торгуемых инструментов.

# 3. G-кривая

У модели Нельсона – Зигеля есть много модификаций, которые были предложены для разных целей. Так, в России для расчета срочной структуры процентных ставок на Московской бирже применяют кривую бескупонной доходности по государственным ценным бумагам (G-кривую) [Гамбаров и др., 2006].

Она была получена при помощи добавления к модели Нельсона – Зигеля трех корректирующих членов для более точного описания начального участка кривой спот-ставок:

<img width="273" alt="формала1" src="https://github.com/MolchanovSergey/curve/assets/96715157/a89e1881-e268-4bc1-8328-ac9cd4a41cf5">

В большинстве случаев эти добавки численно малы и G-кривая может быть хорошо описана с помощью модели Нельсона – Зигеля, но иногда они привносят заметное улучшение. Получившаяся модель полу-динамическая, поскольку состоит из двух частей: статическая осталась от базовой модели, а динамическая необходима для учета исторических данных из предыдущих периодов (t−1) и (t−2). В этом случае неизвестные параметры оцениваются посредством фильтра Калмана.
G-кривая – один из главных индикаторов состояния финансового рынка и базовый эталон для оценки различных облигаций и других финансовых инструментов. В настоящее время разработан проект новой, уточненной G-кривой. С 2018 г. расчеты будут производиться именно по ней.

Расчет динамических параметро G - кривой Московкой бирджи: $\beta_0$, $\beta_1$, $\beta_2$, $\tau$ $g_1$ ÷ $g_9$ осуществляется в режиме реального времени по сделкам и заявкам на рынке государственных ценных бумаг. Слагаемые до знака суммы, соответствующие модели Нельсона-Сигеля, определяют "скелет" кривой, добавочные члены возникают только по мере необходимости и на каждой итерации расчёта кривой демпфируются во избежание накопления добавок.

Теоретическая доходность к погашению каждого выпуска ОФЗ, включённого в базу расчёта, равняется сумме доходности к погашению, рассчитанной на основании КБД Московской биржи, и корректирующей поправки. Часть выпусков назначается опорными выпусками ("бенчмарками"), к ним КБД Московской биржи подстраивается без корректирующих поправок (для этих выпусков корректирующие поправки равны нулю). По теоретическим доходностям к погашению определяются теоретические цены.

Список облигаций, включаемых в базу расчёта, определяется в следующем порядке.

Облигации подразделяются на три группы, исходя из срока до погашения облигаций на 15-е число месяца ввода в действие новой базы расчёта:

- облигации со сроком до погашения свыше 2 месяцев, но не более 2 лет;
- облигации со сроком до погашения свыше 2 лет, но не более 10 лет;
- облигации со сроком до погашения свыше 10 лет.

При определении новой базы расчёта учитываются объёмы торгов и количества сделок, заключенных с облигациями в Режиме основных торгов. 

Приближенный вид данных для рачета:

<img width="523" alt="image" src="https://github.com/MolchanovSergey/curve/assets/96715157/644c0018-7057-4434-8877-78e70e331852">


Приближенный вид кривой, ожидаемый в результате расчета:

![image](https://github.com/MolchanovSergey/curve/assets/96715157/d04ebcf3-8fd6-4ef3-877f-5b7fcc50b5a5)


# Построение кривой на рыночных данных 

# 1. Выбор данных для построения кривых 

Для учебных целей построения кривых процентных ставок, предлагается использовать данные по ОФЗ Московской Биржи. 

Примерный вид табличных данных:


<img width="675" alt="Снимок экрана 2023-12-15 в 11 53 56" src="https://github.com/MolchanovSergey/curve/assets/96715157/8b3dd7c0-839c-4ca1-90f4-b5e0e6d2dfb3">

# Система уравне для определения базовой кривой процентных ставок

Исходя из того, что рыночная стоимость ОФЗ в момент t = 0, составляет:

<img width="128" alt="Снимок экрана 2023-12-22 в 13 49 18" src="https://github.com/MolchanovSergey/curve/assets/96715157/676ef23b-26c2-4388-a41b-727936665f9a">


Каждый платеж по ОФЗ индивидуально дисконтируется по соответствующей безрисковой процентной ставке.

Выбираем следующие выпуски ОФЗ:

1. SU26223RMFS6 Рыночная цена: 985,6, Срок до погашения, дн: 68 Номинал: 1000 , Сумма купона: 32,41, Срок до выплаты купона: 68  

2. SU26227RMFS7 Рыночная цена: 969,6, Срок до погашения, дн: 201 Номинал: 1000 , Сумма купона: 36,90  , Срок до выплаты купона: 26, 201
   
3. SU26222RMFS8 Рыночная цена: 963,2 Срок до погашения, дн: 293 Номинал: 1000  , Сумма купона: 35,40 , Срок до выплаты купона: 117, 293.  

4. SU26234RMFS3 Рыночная цена: 888,1, Срок до погашения, дн: 545 Номинал: 1000 , Сумма купона: 22,44 , Срок до выплаты купона: 26, 206, 386, 545.   


Система уравнений будет иметь вид:

1. $985,6 = \dfrac{1032,41}{(1 - t_1)^{\frac{68}{365}}}$

2. $969,9 = \dfrac{36,90}{(1 - t_1)^{\frac{26}{365}}} + \dfrac{1036,9}{(1 - t_2)^{\frac{201}{365}}}$

3. $963,2 = \dfrac{35,40}{(1 - t_2)^{\frac{117}{365}}} + \dfrac{1035,40}{(1 - t_3)^{\frac{293}{365}}}$

4. $888,1 = \dfrac{22,44}{(1 - t_1)^{\frac{26}{365}}} + \dfrac{22,44}{(1 - t_2)^{\frac{206}{365}}} + \dfrac{22,44}{(1 - t_3)^{\frac{386}{365}}} + \dfrac{1022,44}{(1 - t_4)^{\frac{545}{365}}}$

5. ...
6. ...

Решением данной сиситемы, будут значения близкие к расчетным занчениям доходнотси по данным Московской Биржи

Кривая с заданными параметрами на дату расчета будет иметь вид:

<img width="585" alt="Снимок экрана 2023-12-25 в 13 23 41" src="https://github.com/MolchanovSergey/curve/assets/96715157/cd713a5c-528c-40c3-af2e-8f7f14b39325">

Точку пересечения кривых целесообразно использовать для смены модели. 

<img width="574" alt="Снимок экрана 2023-12-25 в 16 34 20" src="https://github.com/MolchanovSergey/curve/assets/96715157/d5ac7b0f-f383-48c0-a836-8b6f5e9d66d1">


Значение показателя MSE составляет 0,14

# 2. Модель Нельсона – Зигеля

Для моделирования структуры процентных ставок с помощью модели Нельсона – Зигеля мы использовали пакет nelson_siegel_svensson для Python. Чтобы рассчитать параметры модели мы использовали функцию calibrate_ns_ols, в результате были получены следующие коэффициенты: beta0=11.943095288097345, beta1=3.2999508897837297, beta2=-4.429806342870336, tau=0.9227123179751332, MSE = 0.062.

Вид кривой:

<img width="675" alt="Кривая" src="https://github.com/MolchanovSergey/curve/blob/main/Кривая%20НЗ.png">


Ниже приведён весь код расчёта параметров модели и построения кривой:

- "Настройка пространства"
- pip install nelson_siegel_svensson
- import numpy as np
- import pandas as pd
- from matplotlib.pyplot import plot
- import matplotlib.pyplot as plt
- from sklearn.metrics import mean_squared_error
- from nelson_siegel_svensson.calibrate import calibrate_ns_ols
- from nelson_siegel_svensson import NelsonSiegelCurve
- "Подготовка данных"
- df = pd.read_csv('DataCurve.csv')
- term = df['Term'].astype (float)
- yieldRZD = df['Yield'].astype (float)
- df = df.sort_values(by=['Term'])
- term = np.array(df['Term'])
- yieldRZD = np.array(df['Yield'])
- "Расчёт параметров модели и построения кривой"
- curve, status = calibrate_ns_ols(term, yieldRZD, tau0=1.0)
- assert status.success
- y = curve
- t = np.linspace(0, 26, 2000)
- print (curve)
- plot(t, y(t), yieldRZD)
- mean_squared_error(yieldRZD, y(term))
# 3. Построение бутстрепа кривой доходности
Шаги для построения бутстрепа кривой доходности:
1. Загрузка данных из файла Excel с помощью библиотеки Pandas.
2. Преобразование даты погашения в сроки (в годах) относительно текущей даты.
3. Выделение столбцов сроков (terms) и расчётных доходностей (rates) из загруженных данных.
4. Определение функции bootstrap_yield_curve(terms, rates), которая будет использоваться для выполнения бутстрепа кривой доходности. Внутри функции используется кубический сплайн (CubicSpline) для интерполяции между точками на кривой.
5. Создание кривой доходности с помощью функции бутстрепа, которая возвращает интерполяцию на основе исходных данных.
6. Генерация значений для графика с более высокой плотностью сроков (terms_fine) и соответствующих доходностей (rates_fine) с использованием полученной бутстреп-кривой.
7. Построение графика, на котором отображается бутстреп-кривая доходности и исходные данные. График предоставляет визуализацию кривой доходности облигаций на основе данных Московской биржи на заданную дату (22.12.2023).
 ![image](https://github.com/MolchanovSergey/curve/assets/147549211/2c7ef480-d45c-443f-ac0a-2ab9e7863969)

Этот код помогает анализировать и визуализировать кривую доходности с использованием метода бутстрепа. 
Далее необходимо выполнить следующие шаги для анализа и оценки модели кривой доходности:
1.	Импорт необходимых библиотек для анализа и дополнения модели, включая Pandas, NumPy, datetime, Scipy, и Matplotlib.
2.	Определение функции calculate_standard_error(terms, rates, spline), которая вычисляет стандартную ошибку интерполяции кривой доходности 
на основе предсказанных и фактических значений.
3.	Определение функции evaluate_smoothness(spline, terms), которая оценивает гладкость кривой доходности, вычисляя вторую производную 
и находя ее максимальное значение.
4.	Определение функции check_negative_forward_rates(spline, terms), которая проверяет наличие отрицательных форвардных ставок на кривой доходности.
5.	Определение функции evaluate_stability(terms, rates, delta=0.01), которая оценивает стабильность модели с помощью случайных шумовых возмущений.
6.	Преобразование даты погашения в срок (в годах) относительно текущей даты.
7.	Выделение столбцов сроков (terms) и расчётных доходностей (rates) из загруженных данных.
8.	Создание кривой доходности с помощью интерполяции CubicSpline на основе исходных данных.
9.	Расчет различных критериев для оценки модели, включая стандартную ошибку, гладкость, наличие отрицательных форвардных ставок, стабильность и простоту реализации (количество параметров).
10.	Вывод результатов оценки модели в виде словаря results, который содержит указанные критерии и их значения.

Результат: 
'Стандартная ошибка': 0.0, 
'Гладкость': 31.537434827478457,
'Отрицательные форвардные ставки: False
'Стабильность': 0.025150530306630614, 
'Простота реализации (количество параметров)': 26 

Модифицированный итеративный бутстрэп



![image](https://github.com/MolchanovSergey/curve/assets/147549211/9ac86f1d-a61b-4881-8ad2-7fd4e6c35456)

Блочный бутстреп



![image](https://github.com/MolchanovSergey/curve/assets/147549211/46133609-c6f5-4aff-a38c-21ec13683f0b)

# Вывод 
В исследовании по моделированию кривой процентных ставок ОФЗ РФ с использованием моделей Bootstrap, Nelson-Siegel и G-кривой, не было выявлено однозначно "лучшей" модели. Это подчеркивает, что различные модели предоставляют уникальные преимущества в зависимости от конкретных целей анализа и доступных данных. Каждая модель имеет свои сильные и слабые стороны, что делает их применение гибким в разных экономических контекстах. Таким образом, выбор модели должен основываться на конкретных потребностях анализа, учитывая специфику и цели исследования.
Модель Bootstrap:
Плюсы: Позволяет точно воссоздать кривую доходности, основываясь на рыночных данных. Эффективна для коротких и средних сроков.
Минусы: Меньшая эффективность на длительных сроках и при недостатке данных.

Модель Nelson-Siegel:
Плюсы: Обеспечивает гибкость в адаптации к различным формам кривой. Хорошо подходит для анализа долгосрочных трендов.
Минусы: Может быть менее точной на коротких сроках или при резких рыночных колебаниях.

G-кривая (Московская биржа):
Плюсы: Подходит для анализа специфики российского рынка. Полезна при оценке рыночных условий в России.
Минусы: Ограниченность применения за пределами российского контекста и возможные искажения при глобальных экономических изменениях.
   
# Обзор литературы

1. Гамбаров Г.М., Шевчук И.В., Балабушкин А.Н., Никитин А.В. Кривая бескупонной доходности на рынке ГКО-ОФЗ // Рынок ценных бумаг. 2006. № 3. С. 68–77.
2. Гамбаров Г.М., Шевчук И.В., Балабушкин А.Н. Оценка срочной структуры процентных ставок. Роль рынка государственных ценных бумаг в оценке срочной структуры процентных ставок // Рынок ценных бумаг. 2004. № 13. С. 1–33.
3. Дедова М.С. Сравнение методов бутстрапа временных рядов для целей бэктестирования моделей оценки банковских рисков // Экономический журнал ВШЭ. 2018. Том 22, № 1. Страницы 84–109.
4. Анатольев С., Дэвидсон Р., Бюльман П., Корради В. Эконометрический ликбез: бутстрап // Квантиль. 2007. №3. Сентябрь. С. 1-57.
5. Косьяненко А.В. Опыт восстановления пропущенной рыночной информации на основе байесовского подхода: Препринт WP16/2007/02. М.: ГУ ВШЭ, 2007.
6. Лапшин В.А., Терещенко М.Ю. Выбор модели срочной структуры процентных ставок на основе ее свойств // Корпоративные финансы. 2018. Т. 12. № 2. С. 53–69.
7. Лукасевич И. Я. Моделирование временной структуры процентных ставок. Экономика. Налоги. Право, 2016.
8. Макушкин М.С., Лапшин В.А. Кривые доходностей на низколиквидных рынках облигаций: особенности оценки. Экономический журнал ВШЭ. 2021; 25(2): 177–195.
9. Ang A., Piazzesi M. A no-arbitrage vector autoregression of term structure dynamics with macroeconomic and latent variables // Journal of Monetary Economics. 2003. Vol. 50. P. 20-26."
10. "Forecasting Yield Curve with Macro-Driven Models: A Comparison Between Machine Learning and Traditional Statistical Approaches" // RStudio Pubs. 2023. URL:https://rstudio-pubs-static.s3.amazonaws.com/796411_53a9fecd06ab4e7990716b0e8066ab27.html
11. Кривая бескупонной доходности [Электронный ресурс] // Сайт Московской Биржи. 2023. URL: http://www.moex.com/a80https://www.moex.com/s2532.
12. Методика определения КБД Московской биржи [Электронный ресурс] // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644.
13. Презентация методики расчета КБД Московской биржи [Электронный ресурс] // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644.
14. Статья. Оценка срочной структуры процентных ставок, 2004г. [Электронный ресурс] // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644.
