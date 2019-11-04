---
title: Opérateurs autorisant la valeur Null
description: En savoir plus sur les opérateurs Nullable qui sont disponibles F# dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 9c747cf5c2e07ca9f80cef741d71d892fb437b3a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424045"
---
# <a name="nullable-operators"></a>Opérateurs autorisant la valeur Null

Les opérateurs Nullable sont des opérateurs arithmétiques binaires ou de comparaison qui fonctionnent avec des types arithmétiques Nullable sur l’un ou les deux côtés. Les types Nullable se produisent fréquemment lorsque vous travaillez avec des données provenant de sources telles que des bases de données qui autorisent les valeurs NULL à la place des valeurs réelles. Les opérateurs Nullable sont fréquemment utilisés dans les expressions de requête. En plus des opérateurs Nullable pour les opérations arithmétiques et de comparaison, les opérateurs de conversion peuvent être utilisés pour effectuer une conversion entre des types Nullable. Il existe également des versions Nullable de certains opérateurs de requête.

## <a name="table-of-nullable-operators"></a>Tableau des opérateurs Nullable

Le tableau suivant répertorie les opérateurs Nullable pris F# en charge dans le langage.

|Nullable à gauche|Nullable à droite|Les deux côtés Nullable|
|---|---|---|
|[? > =](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[> = ?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[? > = ?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[? >](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[? >?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[? < =](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[< = ?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[? < = ?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[? <](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[? <?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[? < >](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[< >?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[? < >?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Notes

Les opérateurs Nullable sont inclus dans le module [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) dans l’espace de noms [Microsoft. FSharp. Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Le type des données Nullable est `System.Nullable<'T>`.

Dans les expressions de requête, les types Nullable surviennent lors de la sélection de données à partir d’une source de données qui autorise les valeurs NULL au lieu des valeurs. Dans une base de données SQL Server, chaque colonne de données d’une table possède un attribut qui indique si les valeurs NULL sont autorisées. Si les valeurs NULL sont autorisées, les données retournées à partir de la base de données peuvent contenir des valeurs NULL qui ne peuvent pas être représentées par un type de données primitif, tel que `int`, `float`, etc. Par conséquent, les données sont retournées en tant que `System.Nullable<int>` au lieu de `int`, et `System.Nullable<float>` au lieu de `float`. La valeur réelle peut être obtenue à partir d’un objet `System.Nullable<'T>` à l’aide de la propriété `Value`, et vous pouvez déterminer si un objet `System.Nullable<'T>` a une valeur en appelant la méthode `HasValue`. Une autre méthode utile est la méthode `System.Nullable<'T>.GetValueOrDefault`, qui vous permet d’obtenir la valeur ou une valeur par défaut du type approprié. La valeur par défaut est une forme de valeur « zéro », par exemple 0, 0,0 ou `false`.

Les types Nullable peuvent être convertis en types primitifs non Nullable à l’aide des opérateurs de conversion habituels, tels que `int` ou `float`. Il est également possible de convertir un type Nullable en un autre type Nullable à l’aide des opérateurs de conversion pour les types Nullable. Les opérateurs de conversion appropriés ont le même nom que les opérateurs standard, mais ils se trouvent dans un module séparé, le module [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) dans l’espace de noms [Microsoft. FSharp. Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) . En général, vous ouvrez cet espace de noms lors de l’utilisation d’expressions de requête. Dans ce cas, vous pouvez utiliser les opérateurs de conversion Nullable en ajoutant le préfixe `Nullable.` à l’opérateur de conversion approprié, comme indiqué dans le code suivant.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Le résultat est `10.000000`.

Les opérateurs de requête sur des champs de données Nullable, tels que `sumByNullable`, existent également pour une utilisation dans les expressions de requête. Les opérateurs de requête pour les types non Nullable ne sont pas compatibles avec les types Nullable. vous devez donc utiliser la version Nullable de l’opérateur de requête approprié lorsque vous travaillez avec des valeurs de données Nullable. Pour plus d’informations, consultez [expressions de requête](../query-expressions.md).

L’exemple suivant illustre l’utilisation d’opérateurs Nullable dans une F# expression de requête. La première requête montre comment écrire une requête sans opérateur Nullable. la deuxième requête affiche une requête équivalente qui utilise un opérateur Nullable. Pour obtenir le contexte complet, y compris comment configurer la base de données pour utiliser cet exemple de code, consultez [procédure pas à pas : accès à une SQL Database à l’aide de fournisseurs de type](../../tutorials/type-providers/index.md).

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
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de type](../../tutorials/type-providers/index.md)
- [Expressions de requête](../query-expressions.md)
