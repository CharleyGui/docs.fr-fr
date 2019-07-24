---
title: Fonctions anonymes - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 4d266584e1867a512e4b61e8839fe948aafb007f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363917"
---
# <a name="anonymous-functions-c-programming-guide"></a>Fonctions anonymes (Guide de programmation C#)

Une fonction anonyme est une instruction ou expression « inline » qui peut être utilisée partout où un type délégué est attendu. Vous pouvez l’utiliser pour initialiser un délégué nommé ou la passer à la place d’un type délégué nommé comme paramètre de méthode.

Vous pouvez utiliser une [expression lambda](lambda-expressions.md) ou une [méthode anonyme](../../language-reference/operators/delegate-operator.md) pour créer une fonction anonyme. Nous vous recommandons d’utiliser des expressions lambda, car elles fournissent un moyen plus concis et plus expressif d’écrire du code en ligne. Contrairement aux méthodes anonymes, certains types d’expressions lambda peuvent être convertis en types d’arborescence d’expression.

## <a name="the-evolution-of-delegates-in-c"></a>Évolution des délégués en C\#

 Dans C# 1.0, vous pouviez créer une instance d’un délégué en l’initialisant explicitement avec une méthode déjà définie à un autre endroit dans le code. C# 2.0 a introduit le concept des méthodes anonymes, qui vous permettent d’écrire des blocs d’instructions inline sans nom pouvant être exécutés dans un appel de délégué. C# 3.0 a introduit les expressions lambda, qui sont semblables aux méthodes anonymes d’un point de vue conceptuel, mais qui sont plus expressives et concises. Ces deux fonctionnalités sont désignées collectivement comme des *fonctions anonymes*. En général, les applications qui ciblent la version 3.5 ou une version ultérieure du .NET Framework utilisent des expressions lambda.  
  
 L’exemple suivant montre l’évolution de la création de délégués entre C# 1.0 et C# 3.0 :  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Voir aussi

- [Instructions, expressions et opérateurs](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Délégués](../../../csharp/programming-guide/delegates/index.md)
- [Arborescences d’expressions (C#)](../concepts/expression-trees/index.md)
