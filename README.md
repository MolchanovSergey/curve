# curve

## Моделирование кривой процентных ставок и сравнение подходов

# План по проекту 

1. Изучить классические модели построения кривой % ставок:
   - Бутстрэп моделей
   - Нельсона - Зигеля
   - Модель G - кривой (использует ММВБ)
   - Модель Свенссона
   - Сплайн модели
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
...
# 2. Бутстрэп 
...
# 3. G-кривая

У модели Нельсона – Зигеля есть много модифика- ций, которые были предложены для разных целей. Так, в России для расчета срочной структуры про- центных ставок на Московской бирже применяют кривую бескупонной доходности по государственным ценным бумагам (G-кривую) [Гамбаров и др., 2006].
Она была получена при помощи добавления к модели Нельсона – Зигеля трех корректирующих членов для более точного описания начального участка кривой спот-ставок:


В большинстве случаев эти добавки численно малы и G-кривая может быть хорошо описана с помощью модели Нельсона – Зигеля, но иногда они привносят заметное улучшение. Получившаяся модель полу- динамическая, поскольку состоит из двух частей: статическая осталась от базовой модели, а динами- ческая необходима для учета исторических данных из предыдущих периодов (t−1) и (t−2). В этом случае неизвестные параметры оцениваются посредством фильтра Калмана.
G-кривая – один из главных индикаторов состояния финансового рынка и базовый эталон для оценки различных облигаций и других финансовых инстру- ментов. В настоящее время разработан проект новой, уточненной G-кривой. С 2018 г. расчеты будут произ- водиться именно по ней.




# Обзор литературы

Кривая бескупонной доходности // Сайт Московской Биржи. 2023. URL: [http://www.moex.com/a80](https://www.moex.com/s2532?ysclid=lpwbzctp3j788468955)https://www.moex.com/s2532?ysclid=lpwbzctp3j788468955

Методика определения КБД Московской биржи // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Презентация методики расчета КБД Московской биржи // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Статья. Оценка срочной структуры процентных ставок, 2004г. // Сайт Московской Биржи. 2023. URL: https://www.moex.com/a3644

Гамбаров Г.М., Шевчук И.В., Балабушкин А.Н., Ники- тин А.В. Кривая бескупонной доходности на рынке ГКО-ОФЗ // Рынок ценных бумаг. 2006. No 3. С. 68–77.
