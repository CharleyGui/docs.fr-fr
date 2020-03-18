---
title: let, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173586"
---
# <a name="let-clause-c-reference"></a>let, clause (Référence C#)

Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures. Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez. Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur. Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.

## <a name="example"></a> Exemple

Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :

1. Pour créer un type énumérable qui peut lui-même être interrogé.

2. Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`. Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../../language-reference/index.md)
- [Mots-clés de requête (LINQ)](query-keywords.md)
- [LINQ en C#](../../linq/index.md)
- [Requête intégrée linguistique (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Gérer des exceptions dans des expressions de requête](../../linq/handle-exceptions-in-query-expressions.md)
