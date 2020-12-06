---
title: Opérateurs autorisant la valeur Null
description: 'En savoir plus sur les opérateurs Nullable qui sont disponibles dans le langage de programmation F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 9ac6afc2c3f4277ee6e93b1ccb3d21f892926b4b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740365"
---
# <a name="nullable-operators"></a>Opérateurs autorisant la valeur Null

Les opérateurs Nullable sont des opérateurs arithmétiques binaires ou de comparaison qui fonctionnent avec des types arithmétiques Nullable sur l’un ou les deux côtés. Les types Nullable se produisent fréquemment lorsque vous travaillez avec des données provenant de sources telles que des bases de données qui autorisent les valeurs NULL à la place des valeurs réelles. Les opérateurs Nullable sont fréquemment utilisés dans les expressions de requête. En plus des opérateurs Nullable pour les opérations arithmétiques et de comparaison, les opérateurs de conversion peuvent être utilisés pour effectuer une conversion entre des types Nullable. Il existe également des versions Nullable de certains opérateurs de requête.

## <a name="table-of-nullable-operators"></a>Tableau des opérateurs Nullable

Le tableau suivant répertorie les opérateurs Nullable pris en charge dans le langage F #.

|Nullable à gauche|Nullable à droite|Les deux côtés Nullable|
|---|---|---|
|[? >=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=%20))|[>= ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E=?%20))|[? >= ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=?%20))|
|[? >](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E%20))|[> ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E?%20))|[? > ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E?%20))|
|[? <=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=%20))|[<= ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C=?%20))|[? <= ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=?%20))|
|[? <](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%20))|[< ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C?%20))|[? < ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C?%20))|
|[?=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=%20))|[=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20=?%20))|[?=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=?%20))|
|[? <>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E%20))|[<> ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C%3E?%20))|[? <> ?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E?%20))|
|[?+](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+%20))|[+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20+?%20))|[?+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+?%20))|
|[?-](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-%20))|[-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20-?%20))|[?-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-?%20))|
|[?*](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*%20))|[*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20*?%20))|[?*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*?%20))|
|[?/](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/%20))|[/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20/?%20))|[?/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/?%20))|
|[?%](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%%20))|[%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%?%20))|[?%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%?%20))|

## <a name="remarks"></a>Remarques

Les opérateurs Nullable sont inclus dans le module [NullableOperators](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html) de l’espace de noms [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html). Le type des données Nullable est `System.Nullable<'T>` .

Dans les expressions de requête, les types Nullable surviennent lors de la sélection de données à partir d’une source de données qui autorise les valeurs NULL au lieu des valeurs. Dans une base de données SQL Server, chaque colonne de données d’une table possède un attribut qui indique si les valeurs NULL sont autorisées. Si les valeurs NULL sont autorisées, les données retournées à partir de la base de données peuvent contenir des valeurs NULL qui ne peuvent pas être représentées par un type de données primitif comme `int` , `float` , et ainsi de suite. Par conséquent, les données sont retournées en tant que `System.Nullable<int>` au lieu de `int` , et `System.Nullable<float>` au lieu de `float` . La valeur réelle peut être obtenue à partir d’un `System.Nullable<'T>` objet à l’aide de la `Value` propriété, et vous pouvez déterminer si un `System.Nullable<'T>` objet a une valeur en appelant la `HasValue` méthode. Une autre méthode utile est la `System.Nullable<'T>.GetValueOrDefault` méthode, qui vous permet d’obtenir la valeur ou une valeur par défaut du type approprié. La valeur par défaut est une forme de valeur « zéro », par exemple 0, 0,0 ou `false` .

Les types Nullable peuvent être convertis en types primitifs non Nullable à l’aide des opérateurs de conversion habituels, tels que `int` ou `float` . Il est également possible de convertir un type Nullable en un autre type Nullable à l’aide des opérateurs de conversion pour les types Nullable. Les opérateurs de conversion appropriés ont le même nom que les opérateurs standard, mais ils se trouvent dans un module séparé, le module [Nullable](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullablemodule.html) dans l’espace de noms [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html) . En général, vous ouvrez cet espace de noms lors de l’utilisation d’expressions de requête. Dans ce cas, vous pouvez utiliser les opérateurs de conversion Nullable en ajoutant le préfixe `Nullable.` à l’opérateur de conversion approprié, comme indiqué dans le code suivant.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn $"%f{float nullableFloat}"
```

La sortie est `10.000000`.

Les opérateurs de requête sur des champs de données Nullable, tels que `sumByNullable` , existent également pour une utilisation dans les expressions de requête. Les opérateurs de requête pour les types non Nullable ne sont pas compatibles avec les types Nullable. vous devez donc utiliser la version Nullable de l’opérateur de requête approprié lorsque vous travaillez avec des valeurs de données Nullable. Pour plus d’informations, consultez [expressions de requête](../query-expressions.md).

L’exemple suivant illustre l’utilisation d’opérateurs Nullable dans une expression de requête F #. La première requête montre comment écrire une requête sans opérateur Nullable. la deuxième requête affiche une requête équivalente qui utilise un opérateur Nullable. Pour obtenir le contexte complet, y compris comment configurer la base de données pour utiliser cet exemple de code, consultez [procédure pas à pas : accès à une SQL Database à l’aide de fournisseurs de type](../../tutorials/type-providers/index.md).

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn $"%d{row.TestData1.Value} %s{row.Name}")

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d{row.TestData1.GetValueOrDefault()} %s{row.Name}")
```

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de type](../../tutorials/type-providers/index.md)
- [Expressions de requête](../query-expressions.md)
