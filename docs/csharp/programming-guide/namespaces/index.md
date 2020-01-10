---
title: Espaces de noms - Guide de programmation C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: e3e9dc22186e5e319c63e34bd85e5e317effde88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712011"
---
# <a name="namespaces-c-programming-guide"></a>Espaces de noms (Guide de programmation C#)

Les espaces de noms sont largement utilisés de deux façons dans la programmation avec C#. Premièrement, le .NET Framework utilise des espaces de noms pour organiser ses nombreuses classes, comme suit :  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
`System` est un espace de noms et `Console` est une classe de cet espace de noms. Vous pouvez utiliser le mot clé `using`. Ainsi, le nom complet n’est pas obligatoire, comme dans l’exemple suivant :  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
Pour plus d’informations, consultez [Directive using](../../language-reference/keywords/using-directive.md).  
  
Deuxièmement, la déclaration de vos propres espaces de noms peut vous aider à contrôler l’étendue des noms de classes et de méthodes dans les projets de programmation plus vastes. Utilisez le mot clé [namespace](../../language-reference/keywords/namespace.md) pour déclarer un espace de noms, comme dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Le nom de l’espace de noms doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide.

## <a name="namespaces-overview"></a>Vue d'ensemble des espaces de noms  

Les espaces de noms ont les propriétés suivantes :  
  
- Ils organisent les projets de code de taille importante.  
- Ils sont délimités à l’aide de l’opérateur `.`.  
- La directive `using` évite de devoir spécifier le nom de l’espace de noms pour chaque classe.  
- L’espace de noms `global` est l’espace de noms « racine » : `global::System` fait toujours référence à l’espace de noms <xref:System> .NET.  

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Espace de noms](~/_csharplang/spec/namespaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Utilisation d’espaces de noms](using-namespaces.md)
- [Utilisation de l’espace de noms My](how-to-use-the-my-namespace.md)
- [Noms d’identificateur](../inside-a-program/identifier-names.md)
- [using, directive](../../language-reference/keywords/using-directive.md)
- [::, opérateur](../../language-reference/operators/namespace-alias-qualifier.md)
