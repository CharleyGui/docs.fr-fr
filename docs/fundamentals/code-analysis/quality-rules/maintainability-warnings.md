---
title: Règles de maintenabilité (analyse du code)
description: En savoir plus sur les règles de maintenabilité de l’analyse du code.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586960"
---
# <a name="maintainability-rules"></a>Règles de maintenabilité

Les règles de maintenabilité prennent en charge la gestion des bibliothèques et des applications.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
|-----------|-----------------------------------|
| [CA1501 : Éviter l'excès d'héritage](ca1501.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| [CA1502 : Éviter l'excès de complexité](ca1502.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| [CA1505 : Éviter le code impossible à maintenir](ca1505.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| [CA1506 : Éviter les couplages de classe excessifs](ca1506.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| [CA1507 : Utiliser nameof à la place de string](ca1507.md) | Un littéral de chaîne est utilisé en tant qu’argument dans lequel une `nameof` expression peut être utilisée. |
| [CA1508 : Éviter le code conditionnel mort](ca1508.md) | Une méthode a un code conditionnel qui prend toujours la valeur `true` ou `false` au moment de l’exécution. Cela provoque un code mort dans la `false` branche de la condition. |
| [CA1509 : Entrée non valide dans le fichier de configuration des métriques de code](ca1509.md) | Les règles de métrique du code, telles que [CA1501](ca1501.md), [CA1502](ca1502.md), [ca1505](ca1505.md) et [CA1506](ca1506.md), ont fourni un fichier de configuration nommé `CodeMetricsConfig.txt` qui a une entrée non valide. |

## <a name="see-also"></a>Voir aussi

- [Mesure de la complexité et de la facilité de maintenance du code managé](/visualstudio/code-quality/code-metrics-values)
