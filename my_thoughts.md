
обзор “парадигм” МО
SL (Timeseries), USL, SSL, в аспекте нашей задачи
-> нам годится unsupervised learning
-> потому что задача кластеризации  - выяснить на какие кластеры липидограммы разбиваются, чтобы выяснить, что полученные группы можно соотносить к методам терапии
Например, имеем 1000 векторов липидограмм, получили 8  кластеров, из них 3  соотносятся с методом терапии
umap, dtree, …


1) Весь сет векторов анализов кластеризуем
2) очередной семпл анализов уже тогда соотносим

---

Было голубым текстом:



6.3.1 Unsupervised machine learning models for phenotyping of MASLD
Unsupervised learning models are widely used to discover liver aging phenotypes without predefined labels, making them particularly valuable in aging research where ground truth phenotypes are often unknown.
Clustering algorithms
Examples: k-means, hierarchical clustering, Gaussian mixture models (GMM), spectral clustering
Use: Identification of discrete liver aging subgroups based on imaging features, laboratory values, or multi-omics profiles.
Pros Hypothesis-free phenotype discovery, Simple to implement and computationally efficient, Useful for exploratory analyses and cohort stratification
Cons Require subjective selection of cluster number, Sensitive to feature scaling and noise, Often assume static phenotypes and struggle with temporal dynamics
Dimensionality reduction and latent factor models
Examples: Principal component analysis (PCA), independent component analysis (ICA), non-negative matrix factorization (NMF), topic modeling
Use: Identification of latent biological processes underlying liver aging, such as metabolic decline or fibrotic remodeling.
Pros Reduce high-dimensional biomarker space, Improve interpretability of aging axes, Facilitate downstream clustering
Cons Linear methods may miss non-linear aging patterns, Components may not correspond to clinically meaningful phenotypes, Limited capacity to model complex interactions


---


В п. 6.1 говорится следующее простыми словами:

если у нас есть данные наблюдения за пациентами во времени и известно, какие болезни у них потом развились, то можно поставить задачу как ML-предсказание нескольких исходов сразу.

То есть:
на вход подаются исходные данные пациента: анализы, показатели, результаты визуализации;

на выходе модель предсказывает не одну болезнь, а сразу несколько возможных коморбидных состояний (вероятности);

для каждого состояния ответ обычно формулируется как вероятность «разовьется / не разовьется».

Почему именно так:

у пациентов с MASLD часто возникают несколько сопутствующих болезней одновременно;

многие показатели естественно объединяются в смысловые группы, например:

липидный обмен,

инсулинорезистентность;

и эту структуру признаков тоже можно использовать в модели, чтобы она училась более осмысленно.

Идея пункта в том, что MASLD-пациентов можно фенотипировать и стратифицировать по риску, обучая модель по исходным клиническим данным предсказывать, какие сочетания сопутствующих заболеваний могут появиться позже.

В этом контексте:

Фенотипировать — значит выделять типы пациентов по их реальным признакам и профилям.
То есть не просто сказать «у всех MASLD», а понять, что внутри этой группы есть разные подтипы: например, у одних сильнее выражены нарушения липидного обмена, у других — инсулинорезистентность, у третьих — другой биологический профиль.

Стратифицировать по риску — значит разделять пациентов на группы по вероятности неблагоприятных исходов.
Например: низкий риск, средний риск, высокий риск развития определенных сопутствующих болезней в будущем.

Связь между ними такая:
 - фенотипирование отвечает на вопрос «какой это тип пациента?»,
 - а стратификация риска — «насколько для него вероятны проблемы дальше?».