---
title: Espaces de noms - Guide de programmation C#
description: En savoir plus sur les espaces de noms en programmation C#. Consultez une vue d’ensemble des propriétés d’espace de noms et affichez des ressources supplémentaires.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440339"
---
# <a name="namespaces-c-programming-guide"></a>Espaces de noms (Guide de programmation C#)

Les espaces de noms sont largement utilisés de deux façons dans la programmation avec C#. Tout d’abord, .NET utilise des espaces de noms pour organiser ses nombreuses classes, comme suit :  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System> est un espace de noms et <xref:System.Console> est une classe de cet espace de noms. Vous pouvez utiliser le mot clé `using`. Ainsi, le nom complet n’est pas obligatoire, comme dans l’exemple suivant :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Pour plus d’informations, consultez [Directive using](../../language-reference/keywords/using-directive.md).

Deuxièmement, la déclaration de vos propres espaces de noms peut vous aider à contrôler l’étendue des noms de classes et de méthodes dans les projets de programmation plus vastes. Utilisez le mot clé [namespace](../../language-reference/keywords/namespace.md) pour déclarer un espace de noms, comme dans l’exemple suivant :

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Le nom de l’espace de noms doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide.

## <a name="namespaces-overview"></a>Vue d’ensemble des espaces de noms

Les espaces de noms ont les propriétés suivantes :

- Ils organisent les projets de code de taille importante.
- Ils sont délimités à l’aide de l’opérateur `.`.
- La directive `using` évite de devoir spécifier le nom de l’espace de noms pour chaque classe.
- L’espace de noms `global` est l’espace de noms « racine » : `global::System` fait toujours référence à l’espace de noms <xref:System> .NET.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Utilisation d’espaces de noms](using-namespaces.md)
- [Comment utiliser l’espace de noms My](how-to-use-the-my-namespace.md)
- [Noms d’identificateurs](../inside-a-program/identifier-names.md)
- [using, directive](../../language-reference/keywords/using-directive.md)
- [::, Opérateur](../../language-reference/operators/namespace-alias-qualifier.md)
