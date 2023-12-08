# curve

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

# История 
   Проблема моделирования структуры процентных ставок на практике и в теории имеет долгую историю и продолжает привлекать внимание ученых и практиков. Различные ученые, такие как Дж. М. Кейнс, П. Самуэльсон, Р. Мертон, Ф. Модильяни, М. Шоулз, Е. Фама и другие, в разное время занимались этим вопросом. Несмотря на значительные успехи в этой области, проблема создания моделей, которые достоверно отражали бы реальные условия, по-прежнему далека от окончательного решения и требует дальнейших исследований.

   Структуру процентных ставок широко используют для исследования цен и доходности облигаций, а также для оценки справедливости рыночных прогнозов. Кривые процентных ставок крайне важны при изучении экономических процессов, поэтому необходимы надежные модели для их оценки. Фактически, процентные ставки по кредитам и займам в конкретный момент времени невозможно наблюдать. Поэтому единственным способом является моделирование на основе доступных данных о государственных или корпоративных облигациях и других финансовых инструментах, чтобы решить задачу, стоящую перед исследователем.

   Каждая модель имеет свои преимущества и недостатки, поэтому специалист должен определить цель исследования и выбрать подходящую модель, учитывая ее характеристики. Модели рассматриваются в порядке их разработки. Каждая последующая модель в каждом классе пыталась исправить недостатки предыдущей версии, однако не всегда это удавалось, и часто новая модель усиливала слабые стороны предыдущей или создавала новые.

   Необходимо предложить алгоритм выбора модели, исходя из ее основных характеристик, которые могут быть наиболее важными для успешного решения задачи, стоящей перед специалистом.
   
# Введение 

Выбор правильной методики конструирования упрощенной структуры процентных ставок, учитывая ее особенности и характеристики рынка, играет важную роль в принятии инвестиционных и финансовых решений. Создание качественной структуры процентных ставок имеет ключевое значение для эффективного функционирования всего рынка, а не только его отдельных компонентов. В настоящий момент развития мировой экономики особое влияние имеет тот факт, что кривая доходности безкупонных государственных ценных бумаг может быть использована для успешного прогноза наступающих финансово-экономических кризисов и выявления связанных с ними рисков. В развитых рыночных условиях оценка кривой процентных ставок безкупонных облигаций по рыночным данным не вызывает трудностей: наличие достаточного количества ликвидных облигаций и достоверных биржевых котировок облегчает этот процесс. Однако для развивающихся стран, где речь идет о государственных облигациях, эти условия некоторыми свойствами не сопровождаются. Поэтому важно выбрать подходящую модель, которая наиболее полно отражает интересующие особенности в каждом конкретном случае. В данном проекте мы рассматриваем только статические модели, но следует понимать, что термин "модель" относится к аппроксимации и интерполяции данных, поскольку речь идет о способах приближения кривых процентных ставок.
# Сфера применения моделей 

Разработка достоверных методов моделирования срочной структуры процентных ставок и их применение имеют огромную важность для всех участников финансового рынка. Центральные банки используют срочную структуру для прогнозирования и оценки текущих и будущих экономических условий. Кривая доходности облигаций является индикатором ожиданий рынка относительно будущей инфляции и позволяет оценить экономическую стабильность. Точные оценки кривой доходности необходимы для эффективной денежно-кредитной политики центральных банков.

Кроме того, с помощью срочной структуры можно оценить стоимость кредитования, доступность кредитных ресурсов, состояние ликвидности в банковском секторе и другие аспекты экономической ситуации. Кривые доходности являются основой теории оценки активов с фиксированным доходом и играют важную роль при принятии инвестиционных решений. Они используются для определения справедливой стоимости облигаций, расчета кредитных спредов, актуарного оценивания и других задач риск-менеджмента и финансовой инженерии. Также с помощью срочной структуры можно разрабатывать инвестиционные стратегии, учитывая срочность заимствования, уровень риска, хеджирование и оценку спекулятивных стратегий.

Таким образом, срочная структура процентных ставок позволяет глубоко исследовать финансовый рынок и его состояние. Она является неотъемлемым инструментом для всех участников финансового рынка, обеспечивая надежные прогнозы и помогая принимать обоснованные решения.
# Порядок выбора подходящей модели

В финансовой сфере часто необходимо оценивать риск и доходность актива в будущем, исходя из текущих условий. Проблема моделирования срочной структуры состоит в том, чтобы как можно лучше описать кривую доходности с учетом рыночных цен финансовых инструментов и обещанных денежных потоков по ним. Эта задачу довольно трудно выполнить для условий, близких к реальности. Одним из препятствий для подобной оценки является отсутствие достаточного объема данных.

Для построения кривой бескупонной доходности обычно используются облигации с нулевым купоном и ставки денежного рынка. Если на рынке нет желаемого количества бескупонных облигаций, то они могут быть искусственно сконструированы, когда каждая купонная облигация рассматривается как портфель бескупонных облигаций. А на рынках, где в краткосрочной перспективе недостаточно ликвидности, используются и ставки межбанковского денежного рынка. 

На практике может также возникнуть необходимость в извлечении спот-ставок из более сложных ценных бумаг, например, свопов и соглашений о форвардной ставке (FRA). Прибегают и к таким рыночным инструментам, как денежные депозиты и фьючерсы.

После определения выборки облигаций, нужной для построения срочной структуры процентных ставок, инвестор может воспользоваться одним из подходов к ее построению. Так, методы оценки срочной структуры можно разделить на три больших класса: «инженерные», параметрические и сплайновые методы.

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
   
Два первых критерия – количественные, они определяются по данным рынка, а оставшиеся – качественные, отражают характеристики выбранной модели. Критерии 1–4 взяты из статьи Г. Гамбарова, И. Шевчука и А. Балабушкина «Оценка срочной структуры процентных ставок» [Гамбаров и др., 2004]. Критерии 5–6 отражены в заметке Дж. Слиса “New Estimates of the UK Term Structure of Interest Rates” [Sleath, 2001].

Выбранная модель обязательно должна отвечать требованиям точности и гладкости, что определяется экономическими соображениями. 

Точность имеет первостепенное значение для изучения ценообразования инструмента, но степень точности часто оказывается обратно пропорциональной уровню полезности полученной модели. Свойство гладкости основное при анализе рыночных ожиданий: определенная степень гладкости дает возможность исследовать форвардные процентные ставки на предмет ожидаемой динамики краткосрочной ставки и инфляции. 

Самой оптимальной будет такая срочная структура, которая максимально сочетает в себе эти два показателя. Однако на практике между ними чаще всего обнаруживается обратная связь.

Учитывая вышесказанное, можно попытаться подобрать такую модель, которая в наибольшей степени будет соответствовать поставленной перед исследователем задаче. 

# Используемые модели и их свойства 

# 1. Модель Нельсона – Зигеля

Одна из самых популярных на практике моделей была предложена Ч. Нельсоном и Э. Зигелем в 1987 г. Она хорошо интерпретирует параметры с экономической точки зрения, достаточно точно описывает имеющиеся данные, имеет мало параметров, поэтому очень компактна. Нельсон и Зигель поставили перед собой цель ввести в обращение как можно более простую модель с минимальным количеством параметров, которая была бы настолько гибкой, чтобы описать типичные в зависимости от рыночной ситуации формы кривой доходности: монотонную, выпуклую и S-образную [Nelson, Siegel, 1987].

<img width="412" alt="Снимок экрана 2023-12-08 в 16 21 07" src="https://github.com/MolchanovSergey/curve/assets/96715157/3432189f-8f97-4805-9607-16e91aea1800">

где t – срок до погашения облигации;
$\beta_0$, $\beta_1$, $\beta_2$, $\tau_1$ – подлежащие оценке неизвестные пара- метры.
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

У модели Нельсона – Зигеля есть много модификаций, которые были предложены для разных целей. Так, в России для расчета срочной структуры про- центных ставок на Московской бирже применяют кривую бескупонной доходности по государственным ценным бумагам (G-кривую) [Гамбаров и др., 2006].

Она была получена при помощи добавления к модели Нельсона – Зигеля трех корректирующих членов для более точного описания начального участка кривой спот-ставок:

<img width="273" alt="формала1" src="https://github.com/MolchanovSergey/curve/assets/96715157/a89e1881-e268-4bc1-8328-ac9cd4a41cf5">

В большинстве случаев эти добавки численно малы и G-кривая может быть хорошо описана с помощью модели Нельсона – Зигеля, но иногда они привносят заметное улучшение. Получившаяся модель полу-динамическая, поскольку состоит из двух частей: статическая осталась от базовой модели, а динамическая необходима для учета исторических данных из предыдущих периодов (t−1) и (t−2). В этом случае неизвестные параметры оцениваются посредством фильтра Калмана.
G-кривая – один из главных индикаторов состояния финансового рынка и базовый эталон для оценки различных облигаций и других финансовых инструментов. В настоящее время разработан проект новой, уточненной G-кривой. С 2018 г. расчеты будут производиться именно по ней.

# Обзор литературы

Кривая бескупонной доходности // Сайт Московской Биржи. 2023. URL: [http://www.moex.com/a80](https://www.moex.com/s2532?ysclid=lpwbzctp3j788468955)https://www.moex.com/s2532?ysclid=lpwbzctp3j788468955

Методика определения КБД Московской биржи // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Презентация методики расчета КБД Московской биржи // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Статья. Оценка срочной структуры процентных ставок, 2004г. // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Гамбаров Г.М., Шевчук И.В., Балабушкин А.Н., Ники- тин А.В. Кривая бескупонной доходности на рынке ГКО-ОФЗ // Рынок ценных бумаг. 2006. No 3. С. 68–77.
