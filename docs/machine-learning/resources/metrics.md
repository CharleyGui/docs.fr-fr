---
title: Métriques ML.NET
description: Découvrir les métriques qui sont utilisées pour évaluer les performances d’un modèle ML.NET
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399216"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Évaluez votre modèle ML.NET avec des mesures

Comprendre les mesures utilisées pour évaluer un modèle ML.NET.

Les mesures d’évaluation sont spécifiques au type de tâche d’apprentissage automatique qu’un modèle effectue.

Par exemple, pour la tâche de classification, le modèle est évalué en mesurant dans quelle mesure une catégorie prédite correspond à la catégorie réelle. Et pour le regroupement, l’évaluation est basée sur la proximité des éléments groupés les uns aux autres, et combien de séparation il ya entre les clusters.

## <a name="evaluation-metrics-for-binary-classification"></a>Mesures d’évaluation pour la classification binaire

| Mesures   |      Description      |  Recherche |
|-----------|-----------------------|-----------|
| **Précision** |  La [précision](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) est la proportion de prédictions correctes avec un jeu de données de test. Elle représente le rapport entre le nombre de prédictions correctes et le nombre total d’échantillons d’entrée. Il fonctionne bien s’il y a un nombre similaire d’échantillons appartenant à chaque classe.| **Plus la précision est proche de 1,00, meilleure est la qualité**. Toutefois, la valeur exacte 1,00 indique un problème (en règle générale, une fuite d’étiquette/cible, un surapprentissage ou un test avec des données d’entraînement). Lorsque les données de test sont déséquilibrées (lorsque la plupart des instances appartiennent à l’une des classes), le jeu de données est petit, ou les scores approchent 0,00 ou 1,00, alors la précision ne saisit pas vraiment l’efficacité d’un classificateur et vous devez vérifier des mesures supplémentaires. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) ou *zone sous la courbe* mesure la zone sous la courbe créée en balayant le taux positif réel par rapport au taux de faux positifs.  |   **Plus la précision est proche de 1,00, meilleure est la qualité**. Il devrait être supérieur à 0,50 pour qu’un modèle soit acceptable. Un modèle avec AUC de 0,50 ou moins est sans valeur. |
| **Zone sous une courbe de précision/rappel** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) ou *zone sous la courbe d’une courbe de précision-rappel*: mesure utile du succès de la prédiction lorsque les classes sont déséquilibrées (ensembles de données fortement biaisés). |  **Plus la précision est proche de 1,00, meilleure est la qualité**. Des scores élevés proches de 1,00 montrent que le classifieur retourne des résultats précis (précision élevée) ainsi que la majorité de tous les résultats positifs (rappel élevé). |
| **Score F1** | [Score F1](https://en.wikipedia.org/wiki/F1_score) également appelé *balanced F-score or F-measure*. Il s’agit de la moyenne harmonique de la précision et du rappel. Le score F1 est utile quand vous souhaitez rechercher un équilibre entre la précision et le rappel.| **Plus la précision est proche de 1,00, meilleure est la qualité**.  Un score F1 atteint sa meilleure valeur à 1,00 et la pire à 0,00. Il vous indique le degré de précision de votre classifieur. |

Pour plus d’informations sur les métriques de classification binaire, consultez les articles suivants :

- [Précision, précision, rappel ou F1 ?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Classe BinaryClassificationMetrics](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [The Relationship Between Precision-Recall and ROC Curves](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Mesures d’évaluation pour la classification multiclasse

| Mesures   |      Description      |  Recherche |
|-----------|-----------------------|-----------|
| **Micro-précision** |  La [précision micro-moyenne](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agrège les contributions de toutes les classes pour calculer la métrique moyenne. Il s’agit de la fraction d’instances correctement prédites. La micro-moyenne ne tient pas compte de l’appartenance aux classes. Fondamentalement, chaque paire exemple-classe contribue de manière égale à la métrique de précision. | **Plus la précision est proche de 1,00, meilleure est la qualité**. Dans une tâche de classification multiclasse, la micro-précision est préférable à la macro-précision si vous suspectez un déséquilibre de classes éventuel ( vous avez peut-être beaucoup plus d’exemples d’une classe que d’autres classes).|
| **Macro-précision** | La [précision macro-moyenne](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) est la précision moyenne au niveau de la classe. La précision pour chaque classe est calculée et la macro-précision est la moyenne de ces précisions. Fondamentalement, chaque classe contribue de manière égale à la métrique de précision. Les classes minoritaires sont aussi importantes que les classes plus grandes. La métrique de macro-moyenne donne la même pondération à chaque classe, quel que soit le nombre d’instances de cette classe contenues dans le jeu de données. |  **Plus la précision est proche de 1,00, meilleure est la qualité**.  La métrique est calculée de manière indépendante pour chaque classe, puis la moyenne est calculée (toutes les classes étant ainsi traitées de façon égale) |
| **Perte de journal**| La [perte logarithmique](http://wiki.fast.ai/index.php/Log_Loss) mesure les performances d’un modèle de classification où l’entrée de prédiction est une valeur de probabilité comprise entre 0,00 et 1,00. La perte logarithmique augmente à mesure que la probabilité prédite diffère de l’étiquette réelle. | **Plus la précision est proche de 0,00, meilleure est la qualité**. Un modèle parfait aurait une perte logarithmique de 0,00. L’objectif de nos modèles Machine Learning consiste à réduire cette valeur.|
| **Réduction de la perte logarithmique** | La [réduction de la perte logarithmique](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) peut être interprétée comme exprimant l’avantage du classifieur par rapport à une prédiction aléatoire.| **Elle est comprise entre -inf et 1,00, où 1,00 correspond à des prédictions parfaites et 0,00 à des prédictions moyennes**. Par exemple, si la valeur est égale à 0,20, elle peut être interprétée comme « la probabilité d’une prédiction correcte est 20 % meilleure qu’une estimation aléatoire ».|

La micro-précision est généralement mieux alignée sur les besoins métier de prédictions de ML. Si vous souhaitez sélectionner une seule métrique pour choisir la qualité d’une tâche de classification multiclasse, ce doit généralement être la micro-précision.

Prenons l’exemple d’une tâche de classification de ticket de support (mappage des tickets entrants aux équipes de support technique) :

- Micro-précision : avec quelle fréquence un ticket entrant est-il orienté vers l’équipe appropriée ?
- Macro-précision : pour une équipe moyenne, avec quelle fréquence un ticket entrant est-il correct pour l’équipe concernée ?

Macro-précision surpoids petites équipes dans cet exemple; une petite équipe qui obtient seulement 10 billets par an compte autant qu’une grande équipe avec 10k billets par an. Dans ce cas, la micro-précision présente une meilleure corrélation avec le besoin métier exprimé par « combien de temps et d’argent l’entreprise peut-elle économiser en automatisant mon processus de routage des tickets ».

Pour plus d’informations sur les métriques de classification multiclasse, consultez les articles suivants :

- [Micro- et Macro-moyenne de précision, rappel et F-Score](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Multiclass Classification with Imbalanced Dataset](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Mesures d’évaluation pour la régression et la recommandation

Les tâches de régression et de recommandation prédisent un nombre. Dans le cas de la régression, le nombre peut être n’importe quelle propriété de sortie qui est influencée par les propriétés d’entrée. Pour recommandation, le nombre est généralement une valeur de notation (entre 1 et 5 par exemple), ou une recommandation oui/non (représentée par 1 et 0 respectivement).

| Métrique   |      Description      |  Recherche |
|----------|-----------------------|-----------|
| **R carré** |  Le *coefficient de détermination*, ou [R carré (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination), représente la puissance prédictive du modèle sous la forme d’une valeur comprise entre -inf et 1,00. 1,00 signifie un ajustement parfait ; l’ajustement peut être arbitrairement médiocre, les scores pouvant alors être négatifs. Un score de 0,00 signifie que le modèle devine la valeur attendue pour l’étiquette. R2 mesure la proximité des valeurs de données de test réelles des valeurs prédites. | **Plus la précision est proche de 1,00, meilleure est la qualité**. Cependant, de faibles valeurs de coefficient de détermination (par exemple 0,50) peuvent parfois être tout à fait normales ou suffisantes pour votre scénario, alors que des valeurs élevées ne conviennent pas toujours et peuvent être suspectes. |
| **Perte absolue** |  La [perte absolue](https://en.wikipedia.org/wiki/Mean_absolute_error) ou *erreur d’absolue moyenne (MAE)* mesure la proximité des prédictions des résultats réels. Il s’agit de la moyenne de toutes les erreurs du modèle, où l’erreur de modèle est la distance absolue entre la valeur d’étiquette prédite et la valeur d’étiquette correcte. Cette erreur de prédiction est calculée pour chaque enregistrement du jeu de données de test. Enfin, la valeur moyenne est calculée pour toutes les erreurs d’absolue enregistrées.| **Plus la précision est proche de 0,00, meilleure est la qualité**. L’erreur absolue moyenne utilise la même échelle que les données mesurées (n’est pas normalisée à une plage spécifique). Vous ne pouvez utiliser l’erreur absolue, l’erreur quadratique moyenne et la racine de l’erreur quadratique moyenne que pour comparer des modèles pour le même jeu de données ou pour un jeu de données présentant une distribution similaire des valeurs d’étiquette. |
| **Perte carrée** |  [Perte carrée](https://en.wikipedia.org/wiki/Mean_squared_error) ou *erreur carrée moyenne (MSE)*, également appelée *Mean Squared Deviation (MSD)*, vous indique à quel point une ligne de régression est proche d’un ensemble de valeurs de données de test en prenant les distances entre les points et la ligne de régression (ces distances sont les erreurs E) et en les quadranant. L’élévation au carré attribue une pondération supérieure aux différences plus grandes. | Elle est toujours non négative, et **plus les valeurs sont proches de 0,00, meilleure est la qualité**. En fonction de vos données, il peut s’avérer impossible d’obtenir une valeur très petite pour l’erreur quadratique moyenne.|
| **Racine de l’erreur quadratique** |  [RMS-loss](https://en.wikipedia.org/wiki/Root-mean-square_deviation) ou *Root Mean Squared Error (RMSE)* (également appelé *Root Mean Square Deviation, RMSD*), mesure la différence entre les valeurs prédites par un modèle et les valeurs observées à partir de l’environnement qui est modélisé. La racine de l’erreur quadratique moyenne est la racine carrée de l’erreur quadratique moyenne et a les mêmes unités que l’étiquette, à l’image de l’erreur absolue, bien que les différences plus grandes se voient attribuer une pondération supérieure. La racine de l’erreur quadratique moyenne est couramment utilisée dans les domaines de la climatologie, des prévisions et de l’analyse de régression pour vérifier des résultats expérimentaux. | Elle est toujours non négative, et **plus les valeurs sont proches de 0,00, meilleure est la qualité**. La racine de l’erreur quadratique moyenne est une mesure de précision, qui compare les erreurs de prévision de différents modèles pour un jeu de données particulier et non entre plusieurs jeux de données, étant dépendante de l’échelle.|

Pour plus d’informations sur les métriques de régression, consultez les articles suivants :

- [Analyse de régression : Comment interpréter R-squared et évaluer la bonté de l’ajustement?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-Squared Definition](https://www.investopedia.com/terms/r/r-squared.asp)
- [Mean Squared Error Definition](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [What are Mean Squared Error and Root Mean Squared Error?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Mesures d’évaluation pour le clustering

| Métrique   |      Description      |  Recherche |
|----------|-----------------------|-----------|
|**Distance moyenne**|Moyenne de la distance entre les points de données et le centre de leur cluster assigné. La distance moyenne est une mesure de la proximité des points de données aux centroïdes de cluster. C’est une mesure de la façon dont «serré» le cluster est.|Les valeurs plus proches de **0** sont meilleures. Plus la distance moyenne est proche de zéro, plus les données sont regroupées. Notez cependant que cette mesure diminuera si le nombre de clusters est augmenté, et dans le cas extrême (où chaque point de données distinct est son propre cluster), il sera égal à zéro.
|**Indice Davies Bouldin**|Le rapport moyen des distances à l’intérieur du cluster par rapport aux distances entre les grappes. Plus le cluster est serré et plus les clusters sont éloignés, plus cette valeur est faible.|Les valeurs plus proches de **0** sont meilleures. Les grappes qui sont plus éloignées les unes des autres et moins dispersées se traduiront par un meilleur score.|
|**Informations mutuelles normalisées**|Peut être utilisé lorsque les données de formation utilisées pour former le modèle de clustering est également livré avec des étiquettes de vérité au sol (c’est-à-dire, clustering supervisé). La mesure de l’information mutuelle normalisée mesure si des points de données similaires sont attribués au même cluster et des points de données disparates sont attribués à différents groupes. L’information mutuelle normalisée est une valeur comprise entre 0 et 1|Les valeurs plus proches de **1** sont meilleures|

## <a name="evaluation-metrics-for-ranking"></a>Mesures d’évaluation pour le classement

| Métrique   |      Description      |  Recherche |
|----------|-----------------------|-----------|
|**Gains cumulatifs actualisés**|Le gain cumulatif réduit (DCG) est une mesure de la qualité de classement. Il est dérivé de deux hypothèses. Un: Les éléments très pertinents sont plus utiles lors de l’apparition plus élevée dans l’ordre de classement. Deux : L’utilité suit la pertinence qui est, plus la pertinence est élevée, plus un élément est utile. Le gain cumulatif actualisé est calculé pour une position particulière dans l’ordre de classement. Il résume la pertinence du classement divisé par le logarithme de l’indice de classement jusqu’à la position d’intérêt. Il est calculé à sum_ l’aide de $0 <1> 'i'0 'p' 'frac 'rel_i' 'log_ 'e 'i '1 ' $ Classements de pertinence sont fournis à un algorithme de formation de classement comme étiquettes de vérité au sol. Une valeur DCG est fournie pour chaque position dans le tableau de classement, d’où le nom Discounted Cumulative **Gains**. |**Les valeurs plus élevées sont meilleures**|
|**Gains cumulatifs à prix réduit normalisés**|La normalisation du DCG permet de comparer la métrique pour les listes de classement de différentes longueurs|**Les valeurs plus proches de 1 sont meilleures**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Mesures d’évaluation pour la détection des anomalies

| Métrique   |      Description      |  Recherche |
|----------|-----------------------|-----------|
|**Zone sous la courbe ROC**|La zone sous la courbe de l’opérateur du récepteur mesure la façon dont le modèle sépare les points de données anormaux et habituels.|**Les valeurs plus proches de 1 sont meilleures**. Seules des valeurs supérieures à 0,5 démontrent l’efficacité du modèle. Les valeurs de 0,5 ou moins indiquent que le modèle n’est pas meilleur que d’allouer au hasard les intrants aux catégories anormales et habituelles|
|**Taux de détection au faux nombre positif**|Le taux de détection à un faux décompte positif est le rapport entre le nombre d’anomalies correctement identifiées et le nombre total d’anomalies dans un ensemble de tests, indexé par chaque faux positif. Autrement dit, il ya une valeur pour le taux de détection à un faux compte positif pour chaque élément faux positif.|**Les valeurs plus proches de 1 sont meilleures**. S’il n’y a pas de faux positifs, alors cette valeur est de 1|
