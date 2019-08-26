---
title: into - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608638"
---
# <a name="into-c-reference"></a>into (Référence C#)

Le mot clé contextuel `into` permet de créer un identificateur temporaire pour stocker les résultats d’une clause [group](group-clause.md), [join](join-clause.md) ou [select](select-clause.md) dans un nouvel identificateur. Cet identificateur peut lui-même être un générateur pour d’autres commandes de requête. Quand il est utilisé dans une clause `group` ou `select`, le nouvel identificateur est parfois appelé *continuation*.

## <a name="example"></a>Exemples

L’exemple suivant illustre l’utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` dont le type déduit est `IGrouping`. En utilisant l’identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> dans chaque groupe et sélectionner uniquement les groupes qui contiennent deux mots ou plus.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

L’utilisation de `into` dans une clause `group` n’est nécessaire que si vous voulez effectuer des opérations de requête supplémentaires dans chaque groupe. Pour plus d’informations, consultez [group, clause](group-clause.md).

Pour obtenir un exemple d’utilisation de `into` dans une clause `join`, consultez [join, clause](join-clause.md).

## <a name="see-also"></a>Voir aussi

- [Mots clés de requête (LINQ)](query-keywords.md)
- [Expressions de requête LINQ](../../programming-guide/linq-query-expressions/index.md)
- [group, clause](group-clause.md)
