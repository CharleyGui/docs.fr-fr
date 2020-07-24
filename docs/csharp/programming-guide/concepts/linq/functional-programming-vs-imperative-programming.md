---
title: Programmation fonctionnelle et programmation impérative (C#)
description: Cet article compare la programmation fonctionnelle en C# et l’approche procédurale. La programmation fonctionnelle applique l’immuabilité par le biais de fonctions pures.
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: bc421d654e532293b522dab9d43920d0fffd7b92
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103747"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Programmation fonctionnelle et programmation impérative (C#)
Cette rubrique compare et contraste la programmation fonctionnelle avec la programmation impérative (procédurale) plus traditionnelle.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Comparaison de la programmation fonctionnelle et de la Programmation impérative  
 Le paradigme *programmation fonctionnelle* a été créé explicitement afin de prendre en charge une approche fonctionnelle pure de la résolution des problèmes. La programmation fonctionnelle est une forme de *programmation déclarative*. Par contraste, la plupart des langages courants, y compris des langages de programmation orientés objets tels que C#, Visual Basic, C++ et Java, ont été conçus principalement pour prendre en charge la programmation *impérative* (procédurale).  
  
 Avec une approche impérative, un développeur écrit du code qui décrit exactement et en détail les étapes que l'ordinateur doit effectuer pour atteindre l'objectif. On appelle parfois cela la programmation *algorithmique*. Par contraste, une approche fonctionnelle suppose la composition du problème sous la forme d'un ensemble de fonctions à exécuter. Vous définissez soigneusement l'entrée de chaque fonction et ce que chaque fonction retourne. Le tableau suivant décrit quelques-unes des différences générales entre ces deux approches.  
  
|Caractéristique|Approche impérative|Approche fonctionnelle|  
|--------------------|-------------------------|-------------------------|  
|Focus du programmeur|Comment effectuer des tâches (algorithmes) et comment assurer le suivi des modifications d'état.|Les informations souhaitées et les transformations requises.|  
|Modifications d'état|Important.|Non-existantes.|  
|Ordre d'exécution|Important.|Peu important.|  
|Contrôle de flux principal|Boucles, conditions et appels de fonctions (méthodes).|Appels de fonctions, y compris la récursivité.|  
|Unité de manipulation principale|Instances de structures ou classes.|Fonctions en tant que collectes de données et objets de première classe.|  
  
 Bien que la plupart des langages aient été conçus pour prendre en charge un paradigme de programmation spécifique, de nombreux langages généraux sont suffisamment flexibles pour prendre en charge plusieurs paradigmes. Par exemple, la plupart des langages qui contiennent des pointeurs fonction peuvent être utilisés pour prendre en charge de manière crédible la programmation fonctionnelle. En outre, C# inclut des extensions de langage explicites qui prennent en charge la programmation fonctionnelle, y compris les expressions lambda et l’inférence de type. La technologie LINQ est une forme de programmation déclarative fonctionnelle.  
  
## <a name="functional-programming-using-xslt"></a>Programmation fonctionnelle à l'aide de XSLT  
 De nombreux développeurs XSLT connaissent l'approche fonctionnelle pure. La manière la plus efficace de développer une feuille de style XSLT consiste à traiter chaque modèle comme une transformation composable et isolée. L'ordre d'exécution n'est pas du tout mis en évidence. XSLT n'autorise pas les effets secondaires (hormis le fait que les mécanismes d'échappement pour l'exécution de procédures de code peuvent introduire des effets secondaires qui entraînent une impureté fonctionnelle). Toutefois, même si XSLT est un outil efficace, certaines de ses caractéristiques ne sont pas optimales. Par exemple, l'expression de constructions de programmation en XML rend le code relativement détaillé, et par conséquent difficile à maintenir. De plus, la forte dépendance envers la récursivité pour le contrôle de flux peut nuire à la lisibilité du code. Pour plus d’informations sur XSLT, consultez [Transformations XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 Toutefois, le langage XSLT a prouvé la valeur de l'utilisation d'une approche fonctionnelle pure pour la transformation de code XML d'une forme en une autre. La programmation fonctionnelle pure à l'aide de LINQ to XML est semblable en de nombreux points au langage XSLT. Cependant, les constructions de programmation introduites par LINQ to XML et le langage C# vous permettent d’écrire des transformations fonctionnelles pures plus lisibles et gérables que XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Avantages des fonctions pures  
 La raison principale pour implémenter des transformations fonctionnelles en tant que fonctions pures est que celles-ci sont composables, autrement dit autonomes et sans état. Ces caractéristiques apportent un certain nombre d'avantages, notamment les suivants :  
  
- Une meilleure lisibilité et facilité de maintenance. Cela est dû au fait que chaque fonction est conçue pour accomplir une tâche spécifique étant donné ses arguments. La fonction ne repose pas sur un état externe.  
  
- Un développement réitératif plus simple. Le code étant plus facile à refactoriser, les modifications de conception sont souvent plus faciles à implémenter. Par exemple, supposez que vous écrivez une transformation compliquée et que vous vous rendez compte par la suite que du code est répété à plusieurs reprises dans la transformation. Si vous refactorisez par le biais d'une méthode pure, vous pouvez appeler votre méthode pure comme bon vous semble sans vous soucier des effets secondaires.  
  
- Une plus grande facilité de test et de débogage. Les fonctions pures étant plus faciles à tester de manière isolée, vous pouvez écrire du code test qui appelle la fonction pure avec des valeurs typiques, des cases de bord valides et des cases de bord non valides.  
  
## <a name="transitioning-for-oop-developers"></a>Transition pour les développeurs OOP  
 Dans la programmation traditionnelle orientée objets (OOP), la plupart des développeurs sont habitués à programmer dans le style impératif/procédural. Pour passer au développement de style fonctionnel pur, ils doivent modifier leur manière de pensée et leur approche du développement.  
  
 Pour résoudre les problèmes, les développeurs OOP conçoivent des hiérarchies de classes, se concentrent sur l'encapsulation correcte et pensent en termes de contrats de classes. Le comportement et l'état des types d'objets sont essentiels et les caractéristiques de langage, telles que les classes, les interfaces, l'héritage et le polymorphisme, sont fournies pour mieux gérer ces problèmes.  
  
 Par contraste, la programmation fonctionnelle traite les problèmes de calcul comme un exercice d'évaluation de transformations fonctionnelles pures de collectes de données. La programmation fonctionnelle évite l'état et les données mutables, et insiste plutôt sur l'application de fonctions.  
  
 Heureusement, les langages C# et Visual Basic ne nécessitent pas de transition totale vers la programmation fonctionnelle, car ils prennent en charge les approches de programmation impératives et fonctionnelles. Un développeur peut choisir quelle approche convient le mieux à un scénario particulier. En fait, les programmes combinent souvent les deux approches.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux transformations fonctionnelles pures (C#)](./introduction-to-pure-functional-transformations.md)
- [Transformations XSLT](../../../../standard/data/xml/xslt-transformations.md)
- [Refactorisation dans des fonctions pures (C#)](./refactoring-into-pure-functions.md)
