---
title: Exceptions générées par le compilateur - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 1d2d561df3e496893657b050fa93b44c56542d97
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240729"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Exceptions générées par le compilateur (Guide de programmation C#)

Certaines exceptions sont levées automatiquement par le Runtime .NET lors de l’échec des opérations de base. Ces exceptions et leurs conditions d’erreur sont répertoriées dans le tableau suivant.  
  
|Exception|Description|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Levée quand un tableau ne peut pas stocker un élément donné, car le type réel de l’élément est incompatible avec le type réel du tableau.|  
|<xref:System.DivideByZeroException>|Levée lors d’une tentative de division d’une valeur intégrale par zéro.|  
|<xref:System.IndexOutOfRangeException>|Levée lors d’une tentative d’indexation d’un tableau à l’aide d’un index qui est inférieur à zéro ou en dehors des limites du tableau.|  
|<xref:System.InvalidCastException>|Levée quand une conversion explicite d’un type de base en interface ou en un type dérivé échoue au moment de l’exécution.|  
|<xref:System.NullReferenceException>|Levée lorsqu’une tentative est faite pour référencer un objet dont la valeur est [null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Levée quand une tentative d’allocation de mémoire à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md) échoue. Cela indique que la mémoire disponible pour le Commun Language Runtime est épuisée.|  
|<xref:System.OverflowException>|Levée quand une opération dans un contexte `checked` engendre un dépassement.|  
|<xref:System.StackOverflowException>|Levée quand la pile d’exécution est épuisée par un trop grand nombre d’appels de méthode en attente ; cela indique généralement une récurrence très profonde ou infinie.|  
|<xref:System.TypeInitializationException>|Levée quand un constructeur statique lève une exception et qu’il n’existe aucune clause `catch` pour l’intercepter.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Exceptions et gestion des exceptions](./index.md)
- [Gestion des exceptions](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
