---
title: Variables locales implicitement typées - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399825"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Variables locales implicitement typées (Guide de programmation C#)

Les variables locales peuvent être déclarées sans donner de type explicite. Le mot clé `var` indique au compilateur de déduire le type de la variable à partir de l’expression située à droite de l’instruction d’initialisation. Le type déduit peut être un type intégré, un type anonyme, un type défini par l’utilisateur ou un type défini dans la bibliothèque de classes .NET Framework. Pour plus d’informations sur l’initialisation des tableaux avec `var`, consultez [Tableaux implicitement typés](../arrays/implicitly-typed-arrays.md).

Les exemples suivants montrent différentes manières de déclarer des variables locales avec `var` :

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Il est important de comprendre que le mot clé `var` n’est pas « variant » et qu’il n’indique pas que la variable est peu typée ou à liaison tardive. Cela signifie simplement que le compilateur détermine et assigne le type qui convient le mieux.

Le mot clé `var` peut être utilisé dans les contextes suivants :

- Dans des variables locales (variables déclarées dans la portée de la méthode), comme indiqué dans l’exemple précédent.

- Dans une instruction d’initialisation [for](../../language-reference/keywords/for.md)

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- Dans une instruction d’initialisation [foreach](../../language-reference/keywords/foreach-in.md)

    ```csharp
    foreach (var item in list) {...}
    ```

- Dans une instruction [using](../../language-reference/keywords/using-statement.md)

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Pour plus d’informations, voir [Comment utiliser des variables et des tableaux locaux dactylographiés implicitement dans une expression de requête](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>Types var et anonymes

Dans de nombreux cas, l’utilisation de `var` est facultative et sert uniquement à simplifier la syntaxe. Toutefois, lorsqu’une variable est initialisée avec un type anonyme, vous devez déclarer la variable en tant que `var` si vous savez déjà que vous aurez besoin d’accéder aux propriétés de l’objet. Il s’agit d’un scénario courant dans les expressions de requête LINQ. Pour plus d’informations, voir [Anonymous Types](anonymous-types.md).

Du point de vue de votre code source, un type anonyme n’a pas de nom. Par conséquent, si une variable de requête a été initialisée avec `var`, la seule façon d’accéder aux propriétés de la séquence d’objets retournée consiste à utiliser `var` comme type pour la variable d’itération de l’instruction `foreach`.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Notes 

Les restrictions suivantes s’appliquent aux déclarations de variables implicitement typées :

- `var` peut être utilisé uniquement lorsqu’une variable locale est déclarée et initialisée dans la même instruction. La variable ne peut pas être initialisée vers la valeur Null, vers un groupe de méthodes ou vers une fonction anonyme.

- `var` ne peut pas être utilisé dans les champs situés dans la portée de la classe.

- Les variables déclarées à l’aide de `var` ne peuvent pas être utilisées dans l’expression d’initialisation. En d’autres termes, `int i = (i = 20);` cette expression est légale : mais cette expression produit une erreur de compilation :`var i = (i = 20);`

- Il n’est pas possible d’initialiser plusieurs variables implicitement typées dans la même instruction.

- Si un type nommé `var` se trouve dans la portée, le mot clé `var` est résolu en ce nom de type et n’est pas considéré comme faisant partie d’une déclaration de variable locale implicitement typée.

Le typage implicite avec le mot clé `var` ne peut être appliqué qu’aux variables comprises dans la portée de la méthode locale. Le typage implicite n’est pas disponible pour les champs de classe, car le compilateur C# rencontrerait un paradoxe logique pendant le traitement du code : le compilateur a besoin de connaître le type du champ, mais il ne peut pas déterminer le type tant que l’expression d’assignation n’est pas analysée, et l’expression ne peut pas être évaluée sans connaître le type. Examinons le code ci-dessous.

```csharp
private var bookTitles;
```

`bookTitles` est un champ de classe de type `var`. Le champ n’ayant aucune expression à évaluer, le compilateur ne peut pas déduire le type que `bookTitles` est censé avoir. De plus, l’ajout d’une expression au champ (comme vous le feriez pour une variable locale) est également insuffisant :

```csharp
private var bookTitles = new List<string>();
```

Quand le compilateur rencontre des champs pendant la compilation du code, il enregistre le type de chaque champ avant de traiter toutes les expressions associées. Le compilateur rencontre le même paradoxe en essayant d’analyser `bookTitles` : il doit connaître le type du champ, mais il détermine normalement le type de `var` en analysant l’expression, ce qui est impossible sans connaître le type au préalable.

`var` peut également être utile avec les expressions de requête dans lesquelles il est difficile de déterminer le type construit exact de la variable de requête. Cela peut se produire avec les opérations de regroupement et de classement.

Le mot clé `var` peut également être utile lorsque le type de la variable est fastidieux à taper, ou bien lorsqu’il est évident ou lorsqu’il n’aide pas à la lisibilité du code. Par exemple, `var` est utile avec les types génériques imbriqués tels que ceux utilisés avec les opérations de groupe. Dans la requête suivante, le type de la variable de requête est `IEnumerable<IGrouping<string, Student>>`. Tant que les personnes qui doivent gérer votre code comprennent ceci, le typage implicite peut tout à fait être utilisé pour rendre votre code plus concis et simplifier sa gestion.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

L’utilisation `var` d’aide à simplifier votre code, mais son utilisation doit être limitée aux cas où il est nécessaire, ou quand il rend votre code plus facile à lire. Pour plus d’informations `var` sur le moment d’utiliser correctement, consultez la section [des variables locales dactylographie implicitement](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) sur l’article des Lignes directrices sur le codage C.

## <a name="see-also"></a>Voir aussi

- [Référence C](../../language-reference/index.md)
- [Tableaux implicitement typés](../arrays/implicitly-typed-arrays.md)
- [Comment utiliser des variables et des tableaux locaux dactylographiés implicitement dans une expression de requête](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Types anonymes](anonymous-types.md)
- [Initialiseurs d’objets et de collections](object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ en C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Pour](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [à l’aide de l’Énoncé](../../language-reference/keywords/using-statement.md)
