---
title: Délégués - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 62785753cf0eb11965f93e517d6a784081b41a13
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363800"
---
# <a name="delegates-c-programming-guide"></a>Délégués (Guide de programmation C#)
Un [délégué](../../../csharp/language-reference/keywords/delegate.md) est un type qui représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Lorsque vous instanciez un délégué, vous pouvez associer son instance à toute méthode ayant une signature et un type de retour compatibles. Vous pouvez appeler la méthode par le biais l'instance de délégué.  
  
 Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes. Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués. Vous créez une méthode personnalisée, et une classe telle qu'un contrôle Windows peut appeler votre méthode lorsqu'un certain événement se produit. L'exemple suivant illustre une déclaration de délégué :  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Toute méthode de n'importe quelle classe ou structure accessible qui correspond au type de délégué, peut être assignée au délégué. La méthode peut être une méthode d'instance ou statique. Cela permet de modifier par programme les appels de méthode, mais également d'insérer du nouveau code dans les classes existantes.  
  
> [!NOTE]
>  Dans le contexte de surcharge de méthodes, la signature d'une méthode n'inclut pas la valeur de retour. Mais dans le contexte des délégués, la signature inclut la valeur de retour. En d'autres termes, une méthode doit avoir le même type de retour que le délégué.  
  
 Cette capacité à faire référence à une méthode en tant que paramètre fait des délégués les instruments idéaux pour définir des méthodes de rappel. Par exemple, une référence à une méthode qui compare deux objets peut être passée comme argument à un algorithme de tri. Étant donné que le code de comparaison est dans une procédure distincte, l'algorithme de tri peut être écrit de façon plus générale.  
  
## <a name="delegates-overview"></a>Vue d'ensemble des délégués  
 Les délégués ont les propriétés suivantes :  
  
- Les délégués sont comparables aux pointeurs de fonction C++, sauf que les délégués sont totalement orientés objet, et contrairement aux pointeurs C++ vers les fonctions membres, les délégués encapsulent une instance d’objet et une méthode.
  
- Les délégués permettent aux méthodes d'être transmises comme des paramètres.  
  
- Les délégués peuvent être utilisés pour définir des méthodes de rappel.  
  
- Les délégués peuvent être chaînés ; par exemple, plusieurs méthodes peuvent être appelées sur un seul événement.  
  
- Les méthodes ne doivent pas correspondre exactement au type du délégué. Pour plus d’informations, consultez [Utilisation de la variance dans les délégués](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C# version 2.0 a introduit le concept de [méthodes anonymes](../../../csharp/language-reference/operators/delegate-operator.md), qui permet de passer des blocs de code en tant que paramètres à la place d'une méthode définie séparément. C# 3.0 a introduit les expressions lambda comme un moyen plus concis d’écrire des blocs de code inline. Les méthodes anonymes et les expressions lambda (dans certains contextes) sont toutes deux compilées en types de délégué. Ces fonctionnalités sont désormais conjointement désignées par l’expression « fonctions anonymes ». Pour plus d’informations sur les expressions lambda, voir [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>Dans cette section  
  
- [Utilisation de délégués](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
- [Quand utiliser des délégués à la place d’interfaces (Guide de programmation C#)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Délégués avec méthodes nommées et méthodes anonymes](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
- [Utilisation de la variance dans les délégués](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Guide pratique pour combiner des délégués (délégués multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
- [Guide pratique pour déclarer, instancier et utiliser un délégué](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  

## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Délégués](~/_csharplang/spec/delegates.md) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="featured-book-chapters"></a>Chapitres proposés  
 [Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Delegate>
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Événements](../../../csharp/programming-guide/events/index.md)
