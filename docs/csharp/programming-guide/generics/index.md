---
title: Génériques - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167490"
---
# <a name="generics-c-programming-guide"></a>Génériques (guide de programmation C#)

Les génériques introduisent le concept de paramètres de type dans le cadre .NET, qui permettent de concevoir des classes et des méthodes qui reportent la spécification d’un ou plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instantanée par le code client. Par exemple, en utilisant `T`un paramètre de type générique, vous pouvez écrire une seule classe que l’autre code client peut utiliser sans encourir le coût ou le risque de moulages en temps d’exécution ou d’opérations de boxe, comme indiqué ici:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Les classes et les méthodes génériques combinent la réutilisabilité, la sécurité de type et l’efficacité d’une manière que leurs homologues non génériques ne peuvent pas. Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux. L’espace <xref:System.Collections.Generic> de nom contient plusieurs classes de collecte génériques. Les collections non génériques, telles que <xref:System.Collections.ArrayList> ne sont pas recommandées et sont maintenues à des fins de compatibilité. Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).

Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé. L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration. (Dans la plupart des <xref:System.Collections.Generic.List%601> cas, vous devriez utiliser la classe fournie par la bibliothèque de classe cadre .NET au lieu de créer votre propre.) Le paramètre de `T` type est utilisé à plusieurs endroits où un type concret serait normalement utilisé pour indiquer le type de l’article stocké dans la liste. Il est utilisé de la façon suivante :

- Comme le type d’un paramètre de méthode dans la méthode`AddHead`.
- Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.
- Comme le type de membre privé `data` de la classe imbriquée.

 Notez `T` que c’est `Node` à la disposition de la classe imbriquée. Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers. En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Aperçu des génériques

- Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.
- L’utilisation la plus courante des génériques est de créer des classes de collection.
- La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>. Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.
- Vous pouvez créer vos propres interfaces génériques, classes, méthodes, événements et délégués.
- Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.
- Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.

## <a name="related-sections"></a>Sections connexes

- [Paramètres de type générique](generic-type-parameters.md)
- [Contraintes sur les paramètres de type](constraints-on-type-parameters.md)
- [Classes génériques](generic-classes.md)
- [Interfaces génériques](generic-interfaces.md)
- [Méthodes génériques](generic-methods.md)
- [Délégués génériques](generic-delegates.md)
- [Différences entre les modèles C++ et les génériques C#](differences-between-cpp-templates-and-csharp-generics.md)
- [Génériques et réflexion](generics-and-reflection.md)
- [Génériques dans le runtime](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/types.md#constructed-types).

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Types](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [Génériques en .NET](../../../standard/generics/index.md)
