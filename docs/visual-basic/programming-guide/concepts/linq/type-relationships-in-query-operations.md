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
ms.openlocfilehash: 8c201abef924766d52b1adb084970a24ebea2b50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350568"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relations des types dans des opérations de requête (Visual Basic)

Les variables utilisées dans [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] opérations de requête sont fortement typées et doivent être compatibles entre elles. Le typage fort est utilisé dans la source de données, dans la requête elle-même et dans l’exécution de la requête. L’illustration suivante identifie les termes utilisés pour décrire une requête de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Pour plus d’informations sur les parties d’une requête, consultez [opérations de requête de base (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

![Capture d’écran montrant une requête de pseudocode avec les éléments mis en surbrillance.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Le type de la variable de portée dans la requête doit être compatible avec le type des éléments dans la source de données. Le type de la variable de requête doit être compatible avec l’élément séquence défini dans la clause `Select`. Enfin, le type des éléments de séquence doit également être compatible avec le type de la variable de contrôle de boucle utilisé dans l’instruction `For Each` qui exécute la requête. Ce typage fort facilite l’identification des erreurs de type au moment de la compilation.

Visual Basic rend le typage fort commode en implémentant l’inférence de type local, également appelée *typage implicite*. Cette fonctionnalité est utilisée dans l’exemple précédent et vous verrez qu’elle est utilisée dans les exemples et la documentation de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Dans Visual Basic, l’inférence de type local est effectuée simplement à l’aide d’une instruction `Dim` sans clause `As`. Dans l’exemple suivant, `city` est fortement typé en tant que chaîne.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> L’inférence de type local fonctionne uniquement lorsque `Option Infer` a la valeur `On`. Pour plus d’informations, consultez [instruction Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md).

Toutefois, même si vous utilisez l’inférence de type local dans une requête, les mêmes relations de type sont présentes parmi les variables dans la source de données, la variable de requête et la boucle d’exécution de la requête. Il est utile d’avoir une compréhension de base de ces relations de type lorsque vous écrivez des requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], ou que vous utilisez les exemples et des exemples de code dans la documentation.

Vous devrez peut-être spécifier un type explicite pour une variable de portée qui ne correspond pas au type retourné par la source de données. Vous pouvez spécifier le type de la variable de portée à l’aide d’une clause `As`. Toutefois, cela génère une erreur si la conversion est une [conversion restrictive](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et que `Option Strict` a la valeur `On`. Par conséquent, nous vous recommandons d’effectuer la conversion sur les valeurs récupérées à partir de la source de données. Vous pouvez convertir les valeurs de la source de données en type de variable de portée explicite à l’aide de la méthode <xref:System.Linq.Enumerable.Cast%2A>. Vous pouvez également effectuer un cast des valeurs sélectionnées dans la clause `Select` en un type explicite différent du type de la variable de portée. Ces points sont illustrés dans le code suivant.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Requêtes qui retournent des éléments entiers des données sources

L’exemple suivant montre une opération de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] qui retourne une séquence d’éléments sélectionnés à partir des données sources. La source, `names`, contient un tableau de chaînes et le résultat de la requête est une séquence contenant des chaînes qui commencent par la lettre M.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Cela est équivalent au code suivant, mais est beaucoup plus petit et plus facile à écrire. La dépendance à l’inférence de type local dans les requêtes est le style par défaut dans Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Les relations suivantes existent dans les deux exemples de code précédents, que les types soient déterminés implicitement ou explicitement.

1. Le type des éléments dans la source de données, `names`, est le type de la variable de portée, `name`, dans la requête.

2. Le type de l’objet sélectionné, `name`, détermine le type de la variable de requête, `mNames`. Ici `name` est une chaîne. par conséquent, la variable de requête est IEnumerable (Of String) dans Visual Basic.

3. La requête définie dans `mNames` est exécutée dans la boucle `For Each`. La boucle itère au sein du résultat de l’exécution de la requête. Étant donné que `mNames`, lorsqu’il est exécuté, retourne une séquence de chaînes, la variable d’itération de la boucle, `nm`, est également une chaîne.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Requêtes qui retournent un champ à partir des éléments sélectionnés

L’exemple suivant montre une opération de requête [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] qui retourne une séquence contenant une seule partie de chaque élément sélectionné à partir de la source de données. La requête prend une collection d’objets `Customer` comme source de données et projette uniquement la propriété `Name` dans le résultat. Étant donné que le nom du client est une chaîne, la requête produit une séquence de chaînes en sortie.

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

1. Le type des éléments dans la source de données, `customers`, est le type de la variable de portée, `cust`, dans la requête. Dans cet exemple, ce type est `Customer`.

2. L’instruction `Select` retourne la propriété `Name` de chaque objet `Customer` au lieu de l’objet entier. Étant donné que `Name` est une chaîne, la variable de requête, `custNames`, sera à nouveau IEnumerable (Of String), et non de `Customer`.

3. Étant donné que `custNames` représente une séquence de chaînes, la variable d’itération de la boucle `For Each`, `custName`, doit être une chaîne.

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

L’exemple suivant illustre une situation plus complexe. Dans l’exemple précédent, il était fastidieux de spécifier explicitement des types pour toutes les variables. Dans cet exemple, il est impossible. Au lieu de sélectionner des éléments `Customer` entiers dans la source de données, ou un champ unique à partir de chaque élément, la clause `Select` de cette requête retourne deux propriétés de l’objet `Customer` d’origine : `Name` et `City`. En réponse à la clause `Select`, le compilateur définit un type anonyme qui contient ces deux propriétés. Le résultat de l’exécution de `nameCityQuery` dans la boucle `For Each` est une collection d’instances du nouveau type anonyme. Étant donné que le type anonyme n’a pas de nom utilisable, vous ne pouvez pas spécifier le type de `nameCityQuery` ou `custInfo` explicitement. Autrement dit, avec un type anonyme, vous n’avez pas de nom de type à utiliser à la place de `String` dans `IEnumerable(Of String)`. Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

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

1. Le type des éléments dans la source de données est de nouveau le type de la variable de portée dans la requête. Dans cet exemple, `cust` est une instance de `Customer`.

2. Étant donné que l’instruction `Select` produit un type anonyme, la variable de requête, `nameCityQuery`, doit être implicitement typée en tant que type anonyme. Un type anonyme n’a pas de nom utilisable et, par conséquent, ne peut pas être spécifié explicitement.

3. Le type de la variable d’itération dans la boucle `For Each` est le type anonyme créé à l’étape 2. Étant donné que le type n’a pas de nom utilisable, le type de la variable d’itération de la boucle doit être déterminé implicitement.

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
