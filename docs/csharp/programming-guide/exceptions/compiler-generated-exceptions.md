---
title: Exceptions générées par le compilateur - Guide de programmation C#
description: En savoir plus sur les exceptions générées par le compilateur. Passez en revue la liste des exceptions levées automatiquement et leurs conditions d’erreur.
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110349"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Exceptions générées par le compilateur (Guide de programmation C#)

Certaines exceptions sont levées automatiquement par le Runtime .NET lors de l’échec des opérations de base. Ces exceptions et leurs conditions d’erreur sont répertoriées dans le tableau suivant.

|Exception|Description|
|---------------|-----------------|
|<xref:System.ArithmeticException>|Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.|
|<xref:System.ArrayTypeMismatchException>|Levée lorsqu’un tableau ne peut pas stocker un élément donné parce que le type réel de l’élément est incompatible avec le type réel du tableau.|
|<xref:System.DivideByZeroException>|Levée lors d’une tentative de division d’une valeur intégrale par zéro.|
|<xref:System.IndexOutOfRangeException>|Levée lors d’une tentative d’indexation d’un tableau à l’aide d’un index qui est inférieur à zéro ou en dehors des limites du tableau.|
|<xref:System.InvalidCastException>|Levée quand une conversion explicite d’un type de base en interface ou en un type dérivé échoue au moment de l’exécution.|
|<xref:System.NullReferenceException>|Levée lorsqu’une tentative est faite pour référencer un objet dont la valeur est [null](../../language-reference/keywords/null.md).|
|<xref:System.OutOfMemoryException>|Levée quand une tentative d’allocation de mémoire à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md) échoue. Cette exception indique que la mémoire disponible pour le common language runtime est épuisée.|
|<xref:System.OverflowException>|Levée quand une opération dans un contexte `checked` engendre un dépassement.|
|<xref:System.StackOverflowException>|Levée quand la pile d’exécution est épuisée par un trop grand nombre d’appels de méthode en attente ; cela indique généralement une récurrence très profonde ou infinie.|
|<xref:System.TypeInitializationException>|Levée quand un constructeur statique lève une exception et qu’il n’existe aucune clause `catch` pour l’intercepter.|

## <a name="see-also"></a>Voir aussi

- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
