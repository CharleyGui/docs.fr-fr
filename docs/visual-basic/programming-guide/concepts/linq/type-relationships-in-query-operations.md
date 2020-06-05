---
title: Relations des types dans des opérations de requête
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406727"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relations des types dans des opérations de requête (Visual Basic)

Les variables utilisées dans les opérations de requête LINQ (Language-Integrated Query) sont fortement typées et doivent être compatibles les unes avec les autres. Le typage fort est utilisé dans la source de données, dans la requête elle-même et dans l’exécution de la requête. L’illustration suivante identifie les termes utilisés pour décrire une requête LINQ. Pour plus d’informations sur les parties d’une requête, consultez [opérations de requête de base (Visual Basic)](basic-query-operations.md).

![Capture d’écran montrant une requête de pseudocode avec les éléments mis en surbrillance.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Le type de la variable de portée dans la requête doit être compatible avec le type des éléments dans la source de données. Le type de la variable de requête doit être compatible avec l’élément Sequence défini dans la `Select` clause. Enfin, le type des éléments de séquence doit également être compatible avec le type de la variable de contrôle de boucle utilisé dans l' `For Each` instruction qui exécute la requête. Ce typage fort facilite l’identification des erreurs de type au moment de la compilation.

Visual Basic rend le typage fort commode en implémentant l’inférence de type local, également appelée *typage implicite*. Cette fonctionnalité est utilisée dans l’exemple précédent, et vous verrez qu’elle est utilisée dans les exemples et la documentation LINQ. Dans Visual Basic, l’inférence de type local est effectuée simplement à l’aide d’une `Dim` instruction sans `As` clause. Dans l’exemple suivant, `city` est fortement typé en tant que chaîne.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> L’inférence de type local fonctionne uniquement lorsque `Option Infer` a la valeur `On` . Pour plus d’informations, consultez [instruction Option Infer](../../../language-reference/statements/option-infer-statement.md).

Toutefois, même si vous utilisez l’inférence de type local dans une requête, les mêmes relations de type sont présentes parmi les variables dans la source de données, la variable de requête et la boucle d’exécution de la requête. Il est utile d’avoir une compréhension de base de ces relations de types lorsque vous écrivez des requêtes LINQ, ou d’utiliser les exemples et des exemples de code dans la documentation.

Vous devrez peut-être spécifier un type explicite pour une variable de portée qui ne correspond pas au type retourné par la source de données. Vous pouvez spécifier le type de la variable de portée à l’aide d’une `As` clause. Toutefois, cela génère une erreur si la conversion est une [conversion restrictive](../../language-features/data-types/widening-and-narrowing-conversions.md) et a la `Option Strict` valeur `On` . Par conséquent, nous vous recommandons d’effectuer la conversion sur les valeurs récupérées à partir de la source de données. Vous pouvez convertir les valeurs de la source de données en type de variable de portée explicite à l’aide de la <xref:System.Linq.Enumerable.Cast%2A> méthode. Vous pouvez également effectuer un cast des valeurs sélectionnées dans la `Select` clause en un type explicite différent du type de la variable de portée. Ces points sont illustrés dans le code suivant.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Requêtes qui retournent des éléments entiers des données sources

L’exemple suivant montre une opération de requête LINQ qui retourne une séquence d’éléments sélectionnés à partir des données sources. La source, `names` , contient un tableau de chaînes et le résultat de la requête est une séquence contenant des chaînes qui commencent par la lettre M.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Cela est équivalent au code suivant, mais est beaucoup plus petit et plus facile à écrire. La dépendance à l’inférence de type local dans les requêtes est le style par défaut dans Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Les relations suivantes existent dans les deux exemples de code précédents, que les types soient déterminés implicitement ou explicitement.

1. Le type des éléments dans la source de données, `names` , est le type de la variable de portée, `name` , dans la requête.

2. Le type de l’objet sélectionné, `name` , détermine le type de la variable de requête, `mNames` . Voici `name` une chaîne, donc la variable de requête est IEnumerable (Of String) dans Visual Basic.

3. La requête définie dans `mNames` est exécutée dans la `For Each` boucle. La boucle itère au sein du résultat de l’exécution de la requête. Étant donné que `mNames` , lorsqu’il est exécuté, retourne une séquence de chaînes, la variable d’itération de la boucle, `nm` , est également une chaîne.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Requêtes qui retournent un champ à partir des éléments sélectionnés

L’exemple suivant montre une [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] opération de requête qui retourne une séquence contenant une seule partie de chaque élément sélectionné à partir de la source de données. La requête prend une collection d' `Customer` objets comme source de données et projette uniquement la `Name` propriété dans le résultat. Étant donné que le nom du client est une chaîne, la requête produit une séquence de chaînes en sortie.

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

Les relations entre les variables sont similaires à celles de l’exemple plus simple.

1. Le type des éléments dans la source de données, `customers` , est le type de la variable de portée, `cust` , dans la requête. Dans cet exemple, ce type est `Customer` .

2. L' `Select` instruction retourne la `Name` propriété de chaque `Customer` objet au lieu de l’objet entier. Étant donné que `Name` est une chaîne, la variable de requête, `custNames` , sera à nouveau IEnumerable (Of String), et non de `Customer` .

3. Étant donné que `custNames` représente une séquence de chaînes, la `For Each` variable d’itération de la boucle, `custName` , doit être une chaîne.

Sans inférence de type local, l’exemple précédent serait plus fastidieux à écrire et à comprendre, comme le montre l’exemple suivant.

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a>Requêtes qui requièrent des types anonymes

L’exemple suivant illustre une situation plus complexe. Dans l’exemple précédent, il était fastidieux de spécifier explicitement des types pour toutes les variables. Dans cet exemple, il est impossible. Au lieu de sélectionner des éléments entiers `Customer` dans la source de données, ou un champ unique à partir de chaque élément, la `Select` clause de cette requête retourne deux propriétés de l’objet d’origine `Customer` : `Name` et `City` . En réponse à la `Select` clause, le compilateur définit un type anonyme qui contient ces deux propriétés. Le résultat de l’exécution de `nameCityQuery` la `For Each` boucle est une collection d’instances du nouveau type anonyme. Étant donné que le type anonyme n’a pas de nom utilisable, vous ne pouvez pas spécifier le type de `nameCityQuery` ou `custInfo` explicitement. Autrement dit, avec un type anonyme, vous n’avez pas de nom de type à utiliser à la place de `String` dans `IEnumerable(Of String)` . Pour plus d’informations, consultez [types anonymes](../../language-features/objects-and-classes/anonymous-types.md).

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

Bien qu’il ne soit pas possible de spécifier des types pour toutes les variables dans l’exemple précédent, les relations restent les mêmes.

1. Le type des éléments dans la source de données est de nouveau le type de la variable de portée dans la requête. Dans cet exemple, `cust` est une instance de `Customer` .

2. Étant donné que l' `Select` instruction produit un type anonyme, la variable de requête, `nameCityQuery` , doit être implicitement typée comme un type anonyme. Un type anonyme n’a pas de nom utilisable et, par conséquent, ne peut pas être spécifié explicitement.

3. Le type de la variable d’itération dans la `For Each` boucle est le type anonyme créé à l’étape 2. Étant donné que le type n’a pas de nom utilisable, le type de la variable d’itération de la boucle doit être déterminé implicitement.

## <a name="see-also"></a>Voir aussi

- [Mise en route de LINQ dans Visual Basic](getting-started-with-linq.md)
- [Types anonymes](../../language-features/objects-and-classes/anonymous-types.md)
- [Inférence de type local](../../language-features/variables/local-type-inference.md)
- [Introduction à LINQ en Visual Basic](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Requêtes](../../../language-reference/queries/index.md)
