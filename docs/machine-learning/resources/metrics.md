---
title: Métriques ML.NET
description: Découvrir les métriques qui sont utilisées pour évaluer les performances d’un modèle ML.NET
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 362f2f382d050ff9ae246af2dffe3e15d22452eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460729"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Métriques d’évaluation de modèle dans ML.NET

## <a name="metrics-for-binary-classification"></a>Métriques de classification binaire

| Métriques   |      Description      |  Recherche |
|-----------|-----------------------|-----------|
| **Précision** |  La [précision](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) est la proportion de prédictions correctes avec un jeu de données de test. Elle représente le rapport entre le nombre de prédictions correctes et le nombre total d’échantillons d’entrée. Elle n’est efficace que s’il existe un nombre similaire d’échantillons dans chaque classe.| **Plus la précision est proche de 1,00, meilleure est la qualité**. Toutefois, la valeur exacte 1,00 indique un problème (en règle générale, une fuite d’étiquette/cible, un surapprentissage ou un test avec des données d’entraînement). Quand les données de test sont asymétriques (la plupart des instances appartiennent à une des classes), que le jeu de données est très petit ou que les scores approchent 0,00 ou 1,00, la précision ne capture pas vraiment l’efficacité d’un classifieur, ce qui vous oblige à vérifier des métriques supplémentaires. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) ou *zone sous la courbe*: cela mesure la zone sous la courbe créée en balayant le taux réel positif par rapport au taux de faux positifs.  |   **Plus la précision est proche de 1,00, meilleure est la qualité**. La valeur doit être supérieure à 0,50 pour qu’un modèle soit acceptable ; un modèle avec une métrique AUC inférieure ou égale à 0,50 est sans intérêt. |
| **Zone sous une courbe de précision/rappel** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) ou *zone sous la courbe d’une courbe de rappel de précision*: mesure utile du succès de la prédiction lorsque les classes sont très déséquilibrées (jeux de données très faussés). |  **Plus la précision est proche de 1,00, meilleure est la qualité**. Des scores élevés proches de 1,00 montrent que le classifieur retourne des résultats précis (précision élevée) ainsi que la majorité de tous les résultats positifs (rappel élevé). |
| **Score F1** | [Score F1](https://en.wikipedia.org/wiki/F1_score) également appelé *balanced F-score or F-measure*. Il s’agit de la moyenne harmonique de la précision et du rappel. Le score F1 est utile quand vous souhaitez rechercher un équilibre entre la précision et le rappel.| **Plus la précision est proche de 1,00, meilleure est la qualité**.  Un score F1 atteint sa meilleure valeur à 1,00 et la pire à 0,00. Il vous indique le degré de précision de votre classifieur. |

Pour plus d’informations sur les métriques de classification binaire, consultez les articles suivants :

- [Accuracy, Precision, Recall or F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Classe BinaryClassificationMetrics](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [The Relationship Between Precision-Recall and ROC Curves](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Métriques de classification multiclasse

| Métriques   |      Description      |  Recherche |
|-----------|-----------------------|-----------|
| **Micro-précision** |  La [précision micro-moyenne](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agrège les contributions de toutes les classes pour calculer la métrique moyenne. Il s’agit de la fraction d’instances correctement prédites. La micro-moyenne ne tient pas compte de l’appartenance aux classes. Fondamentalement, chaque paire exemple-classe contribue de manière égale à la métrique de précision. | **Plus la précision est proche de 1,00, meilleure est la qualité**. Dans une tâche de classification multiclasse, la micro-précision est préférable à la macro-précision si vous suspectez un déséquilibre de classes éventuel ( vous avez peut-être beaucoup plus d’exemples d’une classe que d’autres classes).|
| **Macro-précision** | La [précision macro-moyenne](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) est la précision moyenne au niveau de la classe. La précision pour chaque classe est calculée et la macro-précision est la moyenne de ces précisions. Fondamentalement, chaque classe contribue de manière égale à la métrique de précision. Les classes minoritaires sont aussi importantes que les classes plus grandes. La métrique de macro-moyenne donne la même pondération à chaque classe, quel que soit le nombre d’instances de cette classe contenues dans le jeu de données. |  **Plus la précision est proche de 1,00, meilleure est la qualité**.  La métrique est calculée de manière indépendante pour chaque classe, puis la moyenne est calculée (toutes les classes étant ainsi traitées de façon égale) |
| **Perte logarithmique**| La [perte logarithmique](http://wiki.fast.ai/index.php/Log_Loss) mesure les performances d’un modèle de classification où l’entrée de prédiction est une valeur de probabilité comprise entre 0,00 et 1,00. La perte logarithmique augmente à mesure que la probabilité prédite diffère de l’étiquette réelle. | **Plus la précision est proche de 0,00, meilleure est la qualité**. Un modèle parfait aurait une perte logarithmique de 0,00. L’objectif de nos modèles Machine Learning consiste à réduire cette valeur.|
| **Réduction de la perte logarithmique** | La [réduction de la perte logarithmique](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) peut être interprétée comme exprimant l’avantage du classifieur par rapport à une prédiction aléatoire.| **Elle est comprise entre -inf et 1,00, où 1,00 correspond à des prédictions parfaites et 0,00 à des prédictions moyennes**. Par exemple, si la valeur est égale à 0,20, elle peut être interprétée comme « la probabilité d’une prédiction correcte est 20 % meilleure qu’une estimation aléatoire ».|

La micro-précision est généralement mieux alignée sur les besoins métier de prédictions de ML. Si vous souhaitez sélectionner une seule métrique pour choisir la qualité d’une tâche de classification multiclasse, ce doit généralement être la micro-précision.

Prenons l’exemple d’une tâche de classification de ticket de support (mappage des tickets entrants aux équipes de support technique) :

- Micro-précision : avec quelle fréquence un ticket entrant est-il orienté vers l’équipe appropriée ?
- Macro-précision : pour une équipe moyenne, avec quelle fréquence un ticket entrant est-il correct pour l’équipe concernée ?

La macro-précision accorde une pondération supérieure aux petites équipes dans cet exemple ; une petite équipe qui n’obtient que 10 tickets par an compte autant qu’une grande équipe qui obtient 10 000 tickets par an. Dans ce cas, la micro-précision présente une meilleure corrélation avec le besoin métier exprimé par « combien de temps et d’argent l’entreprise peut-elle économiser en automatisant mon processus de routage des tickets ».

Pour plus d’informations sur les métriques de classification multiclasse, consultez les articles suivants :

- [Micro- and Macro-average of Precision, Recall and F-Score](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Multiclass Classification with Imbalanced Dataset](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Métriques de régression

| Métriques   |      Description      |  Recherche |
|-----------|-----------------------|-----------|
| **R carré** |  Le *coefficient de détermination*, ou [R carré (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination), représente la puissance prédictive du modèle sous la forme d’une valeur comprise entre -inf et 1,00. 1,00 signifie un ajustement parfait ; l’ajustement peut être arbitrairement médiocre, les scores pouvant alors être négatifs. Un score de 0,00 signifie que le modèle devine la valeur attendue pour l’étiquette. R2 mesure la proximité des valeurs de données de test réelles des valeurs prédites. | **Plus la précision est proche de 1,00, meilleure est la qualité**. Cependant, de faibles valeurs de coefficient de détermination (par exemple 0,50) peuvent parfois être tout à fait normales ou suffisantes pour votre scénario, alors que des valeurs élevées ne conviennent pas toujours et peuvent être suspectes. |
| **Perte absolue** |  La [perte absolue](https://en.wikipedia.org/wiki/Mean_absolute_error) ou *erreur d’absolue moyenne (MAE)* mesure la proximité des prédictions des résultats réels. Il s’agit de la moyenne de toutes les erreurs du modèle, où l’erreur de modèle est la distance absolue entre la valeur d’étiquette prédite et la valeur d’étiquette correcte. Cette erreur de prédiction est calculée pour chaque enregistrement du jeu de données de test. Enfin, la valeur moyenne est calculée pour toutes les erreurs d’absolue enregistrées.| **Plus la précision est proche de 0,00, meilleure est la qualité**. Notez que l’erreur d’absolue moyenne utilise la même échelle que les données mesurées (elle n’est pas normalisée sur une plage spécifique). Vous ne pouvez utiliser l’erreur absolue, l’erreur quadratique moyenne et la racine de l’erreur quadratique moyenne que pour comparer des modèles pour le même jeu de données ou pour un jeu de données présentant une distribution similaire des valeurs d’étiquette. |
| **Erreur quadratique** |  L’[Erreur quadratique](https://en.wikipedia.org/wiki/Mean_squared_error) ou *Erreur quadratique moyenne (MSE)* , également appelée *Écart quadratique moyen (MSD)* , indique la proximité d’une ligne de régression d’un ensemble de valeurs de données de test. Elle élève au carré les distances entre les points et la ligne de régression (ces distances sont les erreurs E). L’élévation au carré attribue une pondération supérieure aux différences plus grandes. | Elle est toujours non négative, et **plus les valeurs sont proches de 0,00, meilleure est la qualité**. En fonction de vos données, il peut s’avérer impossible d’obtenir une valeur très petite pour l’erreur quadratique moyenne.|
| **Racine de l’erreur quadratique** |  La [racine de l’erreur quadratique](https://en.wikipedia.org/wiki/Root-mean-square_deviation) ou *racine de l’erreur quadratique moyenne*, également appelée *racine de l’écart quadratique moyen*, mesure la différence entre les valeurs prédites par un modèle et les valeurs réellement observées à partir de l’environnement en cours de modélisation. La racine de l’erreur quadratique moyenne est la racine carrée de l’erreur quadratique moyenne et a les mêmes unités que l’étiquette, à l’image de l’erreur absolue, bien que les différences plus grandes se voient attribuer une pondération supérieure. La racine de l’erreur quadratique moyenne est couramment utilisée dans les domaines de la climatologie, des prévisions et de l’analyse de régression pour vérifier des résultats expérimentaux. | Elle est toujours non négative, et **plus les valeurs sont proches de 0,00, meilleure est la qualité**. La racine de l’erreur quadratique moyenne est une mesure de précision, qui compare les erreurs de prévision de différents modèles pour un jeu de données particulier et non entre plusieurs jeux de données, étant dépendante de l’échelle.|

Pour plus d’informations sur les métriques de régression, consultez les articles suivants :

- [Analyse de régression : comment interpréter la R-squareie et évaluer l’adéquation ?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-Squared Definition](https://www.investopedia.com/terms/r/r-squared.asp)
- [Mean Squared Error Definition](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [What are Mean Squared Error and Root Mean Squared Error?](https://www.vernier.com/til/1014/)
