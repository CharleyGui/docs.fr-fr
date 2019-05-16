---
title: Opérateurs autorisant la valeur Null
description: En savoir plus sur les opérateurs nullables qui sont disponibles dans le F# langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 79165f35258b414624174153d2cd729b301cf389
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642091"
---
# <a name="nullable-operators"></a>Opérateurs autorisant la valeur Null

Opérateurs nullables sont des opérateurs arithmétiques ou de comparaison binaires qui fonctionnent avec les types arithmétiques nullable sur un ou deux côtés. Types Nullable surviennent fréquemment lorsque vous travaillez avec des données à partir de sources telles que les bases de données acceptant les valeurs NULL à la place des valeurs réelles. Opérateurs nullables sont fréquemment utilisées dans les expressions de requête. Outre les opérateurs nullables pour les opérations arithmétiques et de comparaison, les opérateurs de conversion utilisable pour effectuer des conversions entre types nullable. Il existe également des versions nullables de certains opérateurs de requête.

## <a name="table-of-nullable-operators"></a>Tableau d’opérateurs Nullable

Le tableau suivant répertorie les opérateurs nullables pris en charge dans les F# langage.

|Nullable sur la gauche|Nullable sur la droite|Les deux côtés nullables|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Notes

Les opérateurs nullables sont inclus dans le [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) module dans l’espace de noms [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Le type de données nullables est `System.Nullable<'T>`.

Dans les expressions de requête, les types nullable surviennent lors de la sélection des données à partir d’une source de données qui autorise des valeurs NULL au lieu de valeurs. Dans une base de données SQL Server, chaque colonne de données dans une table possède un attribut qui indique si les valeurs NULL sont autorisées. Si les valeurs NULL sont autorisées, les données retournées à partir de la base de données peuvent contenir les valeurs NULL ne peut pas être représentées par un type de données primitifs comme `int`, `float`, et ainsi de suite. Par conséquent, les données sont retournées en tant qu’un `System.Nullable<int>` au lieu de `int`, et `System.Nullable<float>` au lieu de `float`. La valeur réelle peut être obtenue à partir une `System.Nullable<'T>` objet à l’aide de la `Value` propriété et vous pouvez déterminer si un `System.Nullable<'T>` objet a une valeur en appelant le `HasValue` (méthode). Une autre méthode utile est la `System.Nullable<'T>.GetValueOrDefault` (méthode), ce qui vous permet d’obtenir la valeur ou une valeur par défaut du type approprié. La valeur par défaut est une forme de valeur « zéro », telle que 0, 0.0, ou `false`.

Types Nullable peuvent être convertis en des types primitifs non nullable à l’aide des opérateurs de conversion habituelles comme `int` ou `float`. Il est également possible de convertir d’un type nullable à un autre type nullable à l’aide des opérateurs de conversion pour les types nullables. Les opérateurs de conversion appropriée ont le même nom que la norme ceux, mais elles se trouvent dans un module séparé, la [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) module dans le [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) espace de noms. En règle générale, vous ouvrir cet espace de noms lorsque vous travaillez avec des expressions de requête. Dans ce cas, vous pouvez utiliser les opérateurs de conversion nullable en ajoutant le préfixe `Nullable.` à l’opérateur de conversion appropriée, comme indiqué dans le code suivant.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Le résultat est `10.000000`.

Sur les champs de données autorise la valeur null, les opérateurs de requête comme `sumByNullable`, existent également pour une utilisation dans les expressions de requête. Les opérateurs de requête pour les types non nullables ne sont pas compatible avec le type avec les types nullable, vous devez donc utiliser la version nullable de l’opérateur de requête approprié lorsque vous travaillez avec des valeurs de données autorise la valeur null. Pour plus d’informations, consultez [Expressions de requête](../query-expressions.md).

L’exemple suivant illustre l’utilisation des opérateurs nullables dans un F# expression de requête. La première requête montre comment écrire une requête sans opérateur nullable ; la deuxième requête montre une requête équivalente qui utilise un opérateur nullable. Pour le contexte complet, y compris comment configurer la base de données à utiliser cet exemple de code, consultez [procédure pas à pas : L’accès à une base de données SQL à l’aide de fournisseurs de Type](../../tutorials/type-providers/accessing-a-sql-database.md).

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
