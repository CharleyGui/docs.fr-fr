---
title: Délégués - Guide de programmation C#
description: Un délégué en C# est un type qui fait référence aux méthodes avec une liste de paramètres et un type de retour. Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.
ms.date: 02/02/2021
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 86f7908501c075881786d16caffdd765b8aaf6b5
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548069"
---
# <a name="delegates-c-programming-guide"></a>Délégués (Guide de programmation C#)

Un [délégué](../../language-reference/builtin-types/reference-types.md) est un type qui représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Lorsque vous instanciez un délégué, vous pouvez associer son instance à toute méthode ayant une signature et un type de retour compatibles. Vous pouvez appeler la méthode par le biais l'instance de délégué.

Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes. Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués. Vous créez une méthode personnalisée, et une classe telle qu'un contrôle Windows peut appeler votre méthode lorsqu'un certain événement se produit. L'exemple suivant illustre une déclaration de délégué :

[!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]

Toute méthode de n'importe quelle classe ou structure accessible qui correspond au type de délégué, peut être assignée au délégué. La méthode peut être une méthode d'instance ou statique. Cette flexibilité signifie que vous pouvez modifier par programme les appels de méthode ou intégrer du nouveau code à des classes existantes.

> [!NOTE]
> Dans le contexte de surcharge de méthodes, la signature d'une méthode n'inclut pas la valeur de retour. Mais dans le contexte des délégués, la signature inclut la valeur de retour. En d'autres termes, une méthode doit avoir le même type de retour que le délégué.

Cette capacité à faire référence à une méthode en tant que paramètre fait des délégués les instruments idéaux pour définir des méthodes de rappel. Vous pouvez écrire une méthode qui compare deux objets dans votre application. Cette méthode peut être utilisée dans un délégué pour un algoritym de tri. Étant donné que le code de comparaison est séparé de la bibliothèque, la méthode de tri peut être plus générale.

Des [pointeurs de fonction](~/_csharplang/proposals/csharp-9.0/function-pointers.md) ont été ajoutés à C# 9 pour des scénarios similaires, où vous avez besoin de davantage de contrôle sur la Convention d’appel. Le code associé à un délégué est appelé à l’aide d’une méthode virtuelle ajoutée à un type délégué. À l’aide de pointeurs de fonction, vous pouvez spécifier différentes conventions.

## <a name="delegates-overview"></a>Vue d'ensemble des délégués

Les délégués ont les propriétés suivantes :

- Les délégués sont comparables aux pointeurs de fonction C++, sauf que les délégués sont totalement orientés objet, et contrairement aux pointeurs C++ vers les fonctions membres, les délégués encapsulent une instance d’objet et une méthode.
- Les délégués permettent aux méthodes d'être transmises comme des paramètres.
- Les délégués peuvent être utilisés pour définir des méthodes de rappel.
- Les délégués peuvent être chaînés ; par exemple, plusieurs méthodes peuvent être appelées sur un seul événement.
- Les méthodes ne doivent pas nécessairement correspondre exactement au type délégué. Pour plus d’informations, consultez [Utilisation de la variance dans les délégués](../concepts/covariance-contravariance/using-variance-in-delegates.md).
- Les expressions lambda sont un moyen plus concis d’écrire des blocs de code inline. Les expressions lambda (dans certains contextes) sont compilées en types délégués. Pour plus d’informations sur les expressions lambda, voir [Expressions lambda](../../language-reference/operators/lambda-expressions.md).

## <a name="in-this-section"></a>Dans cette section

- [Utilisation de délégués](./using-delegates.md)
- [Quand utiliser des délégués à la place d’interfaces (Guide de programmation C#)](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))
- [Délégués avec méthodes nommées et Méthodes anonymes](./delegates-with-named-vs-anonymous-methods.md)
- [Utilisation de la variance dans les délégués](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Comment combiner des délégués (délégués multicast)](./how-to-combine-delegates-multicast-delegates.md)
- [Comment déclarer, instancier et utiliser un délégué](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Délégués](~/_csharplang/spec/delegates.md) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="featured-book-chapters"></a>Chapitres proposés

- [Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))
- [Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))

## <a name="see-also"></a>Voir aussi

- <xref:System.Delegate>
- [Guide de programmation C#](../index.md)
- [Événements](../events/index.md)
