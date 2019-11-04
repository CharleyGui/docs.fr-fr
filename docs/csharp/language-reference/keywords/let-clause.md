---
title: let, clause - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422700"
---
# <a name="let-clause-c-reference"></a>let, clause (Référence C#)

Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures. Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez. Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur. Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.

## <a name="example"></a>Exemple

Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :

1. Pour créer un type énumérable qui peut lui-même être interrogé.

2. Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`. Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../../language-reference/index.md)
- [Mots clés de requête (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Mise en route de LINQ en C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Gérer des exceptions dans des expressions de requête](../../linq/handle-exceptions-in-query-expressions.md)
