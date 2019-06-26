---
title: Conventions de codage F#
description: Découvrez des instructions générales et des idiomes lors de l’écriture F# code.
ms.date: 05/14/2018
ms.openlocfilehash: c8df654cbb94fff1ef7ffb909655439398f30bf5
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402363"
---
# <a name="f-coding-conventions"></a>Conventions de codage F#

Les conventions suivantes sont formulées à partir de l’expérience d’utilisation avec de grandes F# codes base. Le [cinq principes bonne F# code](index.md#five-principles-of-good-f-code) constituent la base de chaque recommandation. Elles sont liées à la [ F# les instructions de conception de composant](component-design-guidelines.md), mais sont applicables pour toute F# de code, pas seulement les composants telles que les bibliothèques.

## <a name="organizing-code"></a>Organisation du code

F#propose deux méthodes principales pour organiser le code : modules et les espaces de noms. Ceux-ci sont similaires, mais que vous n’ont pas les différences suivantes :

* Espaces de noms sont compilés en tant qu’espaces de noms .NET. Les modules sont compilés en tant que classes statiques.
* Espaces de noms sont toujours de niveau supérieur. Modules peuvent être imbriqués dans d’autres modules et de niveau supérieur.
* Espaces de noms peut s’étendre sur plusieurs fichiers. Les modules ne peuvent pas.
* Les modules peuvent être décorées avec `[<RequireQualifiedAccess>]` et `[<AutoOpen>]`.

Les instructions suivantes vous aideront à les utiliser pour organiser votre code.

### <a name="prefer-namespaces-at-the-top-level"></a>Préférez les espaces de noms au niveau supérieur

Pour tout code utilisable publiquement, les espaces de noms sont préférentiels aux modules au niveau supérieur. Car ils sont compilés en tant qu’espaces de noms .NET, ils sont consommables à partir de c# avec aucun problème.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

À l’aide d’un module de niveau supérieur peuvent être absentes différent lorsqu’elle est appelée uniquement à partir de F#, mais pour C# consommateurs, les appelants peuvent être surpris par devoir qualifier `MyClass` avec la `MyCode` module.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Appliquer avec soin `[<AutoOpen>]`

Le `[<AutoOpen>]` construction permettre polluent l’étendue de ce qui est disponible aux appelants, et la réponse à quelque chose de provenance est « magique ». Cela n’est généralement pas une bonne chose. Une exception à cette règle est la F# bibliothèque principale elle-même (bien que cela n’existe également un peu controversé).

Toutefois, il est pratique si vous disposez des fonctionnalités d’assistance pour une API publique que vous souhaitez organiser séparément à partir de cette API publique.

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

Vous pouvez ainsi les détails d’implémentation de distinct correctement à partir de l’API publique d’une fonction sans avoir à qualifier complètement une assistance à chaque fois que vous l’appelez.

En outre, exposer des méthodes d’extension et de générateurs d’expressions au niveau de l’espace de noms peut être parfaitement exprimée avec `[<AutoOpen>]`.

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Utilisez `[<RequireQualifiedAccess>]` chaque fois que les noms peuvent entrer en conflit ou si vous pensez qui vous aideront à la lisibilité

Ajout de la `[<RequireQualifiedAccess>]` attribut à un module indique que le module ne peut-être pas être ouverts et des références aux éléments du module doivent explicite qualifié d’accès. Par exemple, le `Microsoft.FSharp.Collections.List` module a cet attribut.

Cela est utile lorsque les valeurs dans le module et les fonctions ont des noms qui sont susceptibles d’entrer en conflit avec les noms dans d’autres modules. Nécessitant un accès complet peut augmenter considérablement la facilité de maintenance à long terme et aspects d’une bibliothèque.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Tri `open` instructions topologiquement

Dans F#, l’ordre des questions de déclarations, notamment avec `open` instructions. Contrairement à c#, où l’effet de `using` et `using static` est indépendante de l’ordre de ces instructions dans un fichier.

Dans F#, éléments ouverts dans une étendue peuvent masquer d’autres déjà présent. Cela signifie que la réorganisation `open` instructions pourraient modifier la signification du code. Par conséquent, toute arbitraire de tri de tous les `open` instructions (par exemple, dans l’ordre alphanumérique) n’est généralement pas recommandé, peur de vous générer un comportement différent que vous pourriez vous attendre.

Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting); autrement dit, commander votre `open` instructions dans l’ordre dans lequel _couches_ de votre système sont définis. Effectuant d’alphanumériques dans les différentes couches topologiques de tri peut également être considéré comme.

Par exemple, voici le tri topologique pour le F# fichier API publique de compilateur service :

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

Notez qu’un saut de ligne sépare les couches topologiques, avec chaque couche en cours de tri dans l’ordre alphanumérique par la suite. Code sont correctement organisées sans occultation accidentellement des valeurs.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Utiliser des classes pour contenir des valeurs qui ont des effets secondaires

Il existe plusieurs fois lorsque l’initialisation d’une valeur peut avoir des effets secondaires, tels que l’instanciation d’un contexte à une base de données ou une autre ressource à distance. Il est tentant de les initialiser des éléments dans un module et l’utiliser dans les fonctions suivantes :

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

Il s’agit généralement une mauvaise idée pour plusieurs raisons :

Tout d’abord, configuration de l’application est placée dans la base de code avec `dep1` et `dep2`. Il est difficile de maintenir dans des codes base supérieure.

Ensuite, initialisées de manière statique des données ne doivent pas inclure de valeurs qui ne sont pas thread-safe si votre composant lui-même utilise plusieurs threads. Cela constitue une infraction clairement à `dep3`.

Enfin, l’initialisation du module compile dans un constructeur statique pour l’unité de compilation entière. Si une erreur se produit dans l’initialisation de la valeur liée aux let dans ce module, il se manifeste comme un `TypeInitializationException` qui est ensuite mis en cache pour toute la durée de vie de l’application. Cela peut être difficile à diagnostiquer. Il existe généralement une exception interne que vous pouvez essayer d’analyser, mais s’il n’est pas, puis il est impossible de dire qu’est la cause racine.

Au lieu de cela, simplement utiliser une classe simple pour contenir les dépendances :

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Ainsi, les éléments suivants :

1. Envoi de n’importe quel état dépendant en dehors de l’API elle-même.
2. Configuration peut maintenant être effectuée en dehors de l’API.
3. Erreurs dans l’initialisation de valeurs dépendantes ne sont pas susceptibles de se manifester par un `TypeInitializationException`.
4. L’API est maintenant plus facile à tester.

## <a name="error-management"></a>Gestion des erreurs

Gestion des erreurs dans les systèmes volumineux s’avérer complexe et subtils, et il n’y a aucune silver puces garantir vos systèmes à tolérance de pannes et se comportent correctement. Les instructions suivantes doivent offrir des conseils pour la navigation dans cet espace difficile.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Représentent les cas d’erreur et l’état non conforme dans les types intrinsèques à votre domaine

Avec [Unions discriminées](../language-reference/discriminated-unions.md), F# vous donne la possibilité pour représenter l’état du programme défectueux dans votre système de type. Exemple :

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Dans ce cas, il existe trois façons connus dont le retrait d’argent à partir d’un compte bancaire peut échouer. Chaque cas d’erreur est représenté dans le type et peuvent donc être traitées en toute sécurité l’ensemble du programme.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

En règle générale, si vous pouvez modéliser les différentes façons que quelque chose peut **échouer** dans votre domaine, puis gestion de code d’erreur n’est plus traité en tant que quelque chose que vous devez traiter en plus des flux de programme régulière. Il est simplement une partie du flux de programme normal et pas considéré comme **exceptionnelles**. Il existe deux grands avantages à cela :

1. Il est plus facile à maintenir votre domaine que les modifications apportées au fil du temps.
2. Cas d’erreur sont plus faciles à test unitaire.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Utilisez les exceptions lorsque les erreurs ne peut pas être représentées avec des types

Pas toutes les erreurs peuvent être représentés dans un domaine qui pose problème. Ces types d’erreurs sont *exceptionnelles* par nature, par conséquent, la possibilité de déclencher et intercepter des exceptions dans F#.

Tout d’abord, il est recommandé de lire le [instructions de conception d’Exception](../../standard/design-guidelines/exceptions.md). Ceux-ci sont également applicables aux F#.

Les principales constructions disponibles dans F# pour les besoins de déclenchement d’exceptions doivent être considérés comme dans l’ordre de préférence suivant :

| Fonction | Syntaxe | Objectif |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Déclenche un `System.ArgumentNullException` portant le nom de l’argument spécifié. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Déclenche un `System.ArgumentException` avec un nom d’argument spécifié et le message. |
| `invalidOp` | `invalidOp "message"` | Déclenche un `System.InvalidOperationException` avec le message spécifié. |
|`raise`| `raise (ExceptionType("message"))` | Mécanisme à usage général pour lever des exceptions. |
| `failwith` | `failwith "message"` | Déclenche un `System.Exception` avec le message spécifié. |
| `failwithf` | `failwithf "format string" argForFormatString` | Déclenche un `System.Exception` avec un message déterminé par la chaîne de format et de ses entrées. |

Utilisez `nullArg`, `invalidArg` et `invalidOp` comme mécanisme pour lever `ArgumentNullException`, `ArgumentException` et `InvalidOperationException` quand cela est approprié.

Le `failwith` et `failwithf` fonctions doivent généralement être évitées, car elles déclenchent la base `Exception` type, pas une exception spécifique. En tant que par le [instructions de conception d’Exception](../../standard/design-guidelines/exceptions.md), vous souhaitez déclencher des exceptions plus spécifiques lorsque vous pouvez.

### <a name="using-exception-handling-syntax"></a>À l’aide de la syntaxe de gestion des exceptions

F#prend en charge les modèles d’exception via la `try...with` syntaxe :

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Réconciliation des fonctionnalités à effectuer en cas d’une exception avec les critères spéciaux peut être un peu délicate si vous souhaitez conserver le code propre. Une d’elles consiste à gérer cette situation consiste à utiliser [modèles actifs](../language-reference/active-patterns.md) comme un moyen de la fonctionnalité de groupe qui entoure un cas d’erreur avec une exception lui-même. Vous pouvez par exemple, qui utilise une API qui, lorsqu’elle lève une exception, englobe des informations précieuses dans les métadonnées d’exception. Désencapsulage d’une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et en retournant que la valeur peut être utile dans certaines situations.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>N’utilisez pas monadic gestion des erreurs pour remplacer des exceptions

Exceptions sont considérées comme un peu interdits dans la programmation fonctionnelle. En effet, les exceptions violent pureté, qu’il s’agisse à prendre en compte non-tout à fait fonctionnelle. Toutefois, il ignore la réalité du où le code doit s’exécuter et ce runtime erreurs peuvent se produire. En règle générale, écrire du code sur l’hypothèse que la plupart des éléments sont pure ni total, afin de réduire les mauvaises surprises.

Il est important de considérer les principaux atouts/aspects suivants d’Exceptions en ce qui concerne leur pertinence et la pertinence dans le runtime .NET et l’écosystème d’interlangage dans son ensemble :

1. Elles contiennent des informations de diagnostic détaillées, ce qui est très utiles lors du débogage d’un problème.
2. Ils sont bien compris par le runtime et d’autres langages .NET.
3. Elles permettent une réduction significative réutilisable par rapport au code qui est hors de sa méthode pour *éviter* exceptions en implémentant un sous-ensemble de leur sémantique sur une base ad hoc.

Cet troisième point est essentiel. Pour les opérations complexes non triviale, ne parvient pas à utiliser des exceptions peut entraîner dans le traitement des structures comme suit :

```fsharp
Result<Result<MyType, string>, string list>
```

Qui peut facilement conduire à un code fragile comme critères spéciaux sur les erreurs « stringly typé » :

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

En outre, il peut être tentant d’AVALER toute exception dans la volonté de disposer d’une fonction « simple » qui retourne un type « mieux » :

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Malheureusement, `tryReadAllText` peut lever de nombreuses exceptions selon la multitude de choses peuvent se produire sur un système de fichiers, et ce code annule immédiatement toutes les informations concernant ce qui peut réellement être fonctionner dans votre environnement. Si vous remplacez ce code avec un type de résultat, vous êtes à l’analyse des messages d’erreur « stringly typé » :

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

Et en plaçant l’objet exception lui-même dans le `Error` constructeur simplement vous oblige à gérer correctement le type d’exception sur le site d’appel, plutôt que dans la fonction. Cette opération efficacement crée des exceptions vérifiées, qui sont notoirement unfun à gérer en tant qu’appelant d’une API.

Une bonne alternative aux exemples ci-dessus consiste à intercepter *spécifique* exceptions et retournent une valeur significative dans le contexte de cette exception. Si vous modifiez le `tryReadAllText` fonctionnent comme suit, `None` a plus de sens :

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Au lieu de fonctionner comme un fourre-tout, cette fonction désormais correctement gérera le cas lorsqu’un fichier est introuvable et affecter ce sens à un retour. Cette valeur de retour peut mapper à ce cas d’erreur lors de pas en ignorant toutes les informations contextuelles ou forcer les appelants pour y faire face à un cas qui ne peuvent pas être pertinent à ce stade dans le code.

Types tels que `Result<'Success, 'Error>` conviennent pour les opérations de base où ils ne sont pas imbriqués, et F# types facultatifs sont parfaits pour représentant lorsque quelque chose peut retourner *quelque chose* ou *rien*. Ils ne sont pas un substitut pour les exceptions, cependant et ne doivent pas être utilisés dans une tentative pour remplacer des exceptions. Au lieu de cela, elles doivent être appliquées judicieusement à des aspects spécifiques d’adresse de stratégie de gestion des erreurs et des exceptions de manière ciblée.

## <a name="partial-application-and-point-free-programming"></a>Application partielle et libre de point de programmation

F#prend en charge d’application partielle et par conséquent, les différentes manières de programme dans un style libre de point. Ceci peut être avantageux de réutilisation du code au sein d’un module ou de l’implémentation de quelque chose, mais il n’est généralement pas quelque chose pour exposer publiquement. En général, libre de point de programmation n’est pas une raison elle-même et peut ajouter un frein COGNITIF pour les personnes qui ne sont pas plonge dans le style.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>N’utilisez pas application partielle et des curryfication dans les API publiques

Avec peu d’exception, l’utilisation d’une application partielle dans les API publiques permettre prêter à confuse pour les consommateurs. En règle générale, `let`-liée de valeurs dans F# code sont **valeurs**, et non **des valeurs de fonction**. Combinaison de valeurs et les valeurs de fonction peut entraîner l’enregistrement d’un petit nombre de lignes de code en échange d’un peu de surcharge cognitive, en particulier si combinées avec des opérateurs tels que `>>` pour composer des fonctions.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Prendre en compte les implications en matière d’outils pour la programmation exempt de point

Fonctions curryfiées étiquette pas leurs arguments. Cela a des implications des outils. Prenez en compte les deux fonctions suivantes :

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Les deux sont des fonctions valides, mais `funcWithApplication` est une fonction curryfiée. Lorsque vous pointez sur leurs types dans un éditeur, vous voir ceci :

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Sur le site d’appel, info-bulles dans les outils tels que Visual Studio ne vous donnera des informations significatives quant à ce que le `string` et `int` représentent les types d’entrée.

Si vous rencontrez le code sans point comme `funcWithApplication` qui est consommable publiquement, il est recommandé d’effectuer une expansion de η complète afin que les outils peuvent sélectionner en noms significatifs pour les arguments.

En outre, le débogage de code sans point peut être difficile, voire impossible. Outils de débogage s’appuient sur les valeurs liées aux noms (par exemple, `let` liaisons) afin que vous puissiez inspecter au milieu des valeurs intermédiaires de l’exécution. Lorsque votre code n’a aucune valeur à inspecter, vous n’avez rien à déboguer. À l’avenir, les outils de débogage peut évoluer pour synthétiser ces valeurs en fonction des chemins d’accès précédemment exécutées, mais il n’est pas une bonne idée pour couvrir vos meilleurs résultats sur *potentiels* fonctionnalités de débogage.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considérez une application partielle comme une technique pour réduire réutilisable interne

Contrairement au point précédent, application partielle est un outil merveilleux pour réduire réutilisable à l’intérieur d’une application ou les mécanismes internes plus approfondies d’une API. Il peut être utile pour l’implémentation des API plus complexes, où réutilisable est souvent un vrai calvaire s’occuper de tests unitaires. Par exemple, le code suivant montre comment vous pouvez réaliser les infrastructures factices plus vous donnent sans prendre une dépendance externe sur une telle infrastructure et devoir apprendre un connexes ad hoc des API.

Par exemple, considérez la topographie de solution suivants :

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` peut exposer du code tel que :

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Tests unitaires `Transactions.doTransaction` dans `ImplementationLogic.Tests.fsproj` est facile :

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

Application partiellement `doTransaction` avec un contexte de simulation objet vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir à construire un contexte factice chaque fois :

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Cette technique ne doit pas être appliquée universellement à votre base de code entière, mais il est un bon moyen de réduire la réutilisation pour internals compliquée et ces éléments internes de tests unitaires.

## <a name="access-control"></a>Contrôle d'accès

F#propose plusieurs options pour [contrôle d’accès](../language-reference/access-control.md), hérité de ce qui est disponible dans le runtime .NET. Ils ne sont pas simplement utilisables pour les types : vous pouvez les utiliser pour les fonctions, trop.

* Préférez non -`public` types et membres jusqu'à ce que vous avez besoin pour être utilisable publiquement. Cela réduit également les deux consommateurs à.
* Vous efforcer de garder toutes les fonctionnalités d’assistance `private`.
* Envisagez d’utiliser `[<AutoOpen>]` sur un module privé de fonctions d’assistance si elles sont nombreuses.

## <a name="type-inference-and-generics"></a>Inférence de type et génériques

Inférence de type peut vous faire gagner de la saisie d’un grand nombre de réutilisable. Et la généralisation automatique dans le F# compilateur peut vous aider à écrire du code plus générique avec pratiquement aucun effort supplémentaire de votre part. Toutefois, ces fonctionnalités ne sont pas universellement bonnes.

* Envisagez d’étiqueter les noms des arguments avec des types explicites dans les API publiques et ne vous basez pas sur l’inférence de type pour cela.

    La raison à cela est que **vous** doit se trouver dans le contrôle de la forme de votre API, pas le compilateur. Bien que le compilateur peut effectuer un travail à l’inférence de types pour vous, il est possible d’avoir la forme de la modification de l’API si les données internes sur qu'il s’appuie ont été modifiés de types. Il peut s’agir de ce que vous voulez, mais cela entraînerait certainement une modification d’API ayant des consommateurs en aval puis à gérer. Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, vous pouvez contrôler ces modifications avec rupture. En termes de conception pilotée par domaine, cela peut être représenté comme une couche de lutte contre la corruption.

* Donnez un nom explicite pour vos arguments génériques.

    Sauf si vous écrivez du code réellement générique qui n’est pas spécifique à un domaine particulier, un nom significatif peut aider d’autres programmeurs compréhension du domaine, qu'ils travaillent. Par exemple, un paramètre de type nommé `'Document` dans le contexte de l’interaction avec un document de base de données plus clairement que les types de document générique peuvent être acceptés par la fonction ou le membre que vous utilisez.

* Songez à nommer les paramètres de type générique avec la casse Pascal.

    Il s’agit du moyen général de faire des choses dans .NET, il est recommandé d’utiliser la casse Pascal plutôt que de snake_case ou de la casse mixte.

Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes qui débutent avec F# ou un grand code base. Il est nécessaire à l’aide de composants qui sont génériques. En outre, si automatiquement généralisées fonctions ne sont pas utilisées avec différents types d’entrée (permettent uniquement si elles sont conçues pour être utilisé en tant que tel), alors il n’existe aucun avantage réel d’y être un générique à ce stade dans le temps. Toujours prendre en compte si le code que vous écrivez est réellement avantage d’être générique.

## <a name="performance"></a>Performances

F#les valeurs sont immuables par défaut, ce qui vous permet d’éviter certaines catégories de bogues (en particulier les impliquant d’accès concurrentiel et parallélisme). Toutefois, dans certains cas, afin d’obtenir une efficacité optimale (ou même raisonnable) de la durée d’exécution ou des allocations de mémoire, une étendue de travail peut-être mieux être implémentée à l’aide de mutation in situ d’état. Cela est possible dans une base opt-in avec F# avec la `mutable` mot clé.

Toutefois, utiliser des `mutable` dans F# peuvent avoir l’impression ne correspond pas à pureté fonctionnelle. Ceci fonctionne bien, si vous ajustez les attentes à partir de la pureté [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency). Transparence référentielle - pas pureté - est l’objectif final lors de l’écriture F# fonctions. Cela vous permet d’écrire une interface fonctionnelle par rapport à une implémentation basée sur une mutation pour le code critique de performances.

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Encapsuler le code mutable dans les interfaces immuables

Transparence référentielle en tant qu’objectif, il est essentiel d’écrire du code qui n’expose pas l’underbelly mutable de fonctions critiques pour les performances. Par exemple, le code suivant implémente la `Array.contains` fonctionner dans le F# bibliothèque principale :

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

Appeler cette fonction plusieurs fois ne modifie pas le tableau sous-jacent, et il vous oblige à conserver un état mutable dans sa consommation. Il est assortie transparent, même si presque à chaque ligne de code qu’il contient utilise mutation.

### <a name="consider-encapsulating-mutable-data-in-classes"></a>Envisagez d’encapsuler des données mutables dans les classes

L’exemple précédent utilisait une seule fonction pour encapsuler des opérations à l’aide de données mutables. Cela n’est pas toujours suffisant pour les jeux de données plus complexes. Tenez compte des ensembles de fonctions suivants :

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

Ce code est performante, mais elle expose la structure de données basées sur une mutation que les appelants sont responsables de la maintenance. Cela peut être encapsulée à l’intérieur d’une classe sans membres sous-jacentes qui peuvent changer :

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table` encapsule la structure de données basées sur une mutation sous-jacente, ce qui n’est ne pas forcé aux appelants de maintenir la structure de données sous-jacente. Les classes sont un moyen efficace d’encapsuler des données et les routines qui ne sont mutation sans exposer les détails aux appelants.

### <a name="prefer-let-mutable-to-reference-cells"></a>Préférez `let mutable` aux cellules de référence

Cellules de référence sont un moyen pour représenter la référence à une valeur plutôt que la valeur elle-même. Même si elles peuvent servir pour le code critique pour les performances, ils sont généralement pas recommandés. Prenons l'exemple suivant :

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

L’utilisation d’une cellule de référence est maintenant « pollue « tout le code suivant à la déréférencer et re-référencer les données sous-jacentes. Envisagez plutôt de `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Outre le point unique de mutation au milieu de l’expression lambda, tout autre code qui touche `acc` pouvez le faire d’une manière qui est similaire à l’utilisation d’un élément normal `let`-immuable valeur limite. Cela rend plus facile à modifier au fil du temps.

## <a name="object-programming"></a>Programmation de l’objet

F#a une prise en charge complète pour les objets et concepts (OO) orientée objet. Bien que de nombreux concepts OO sont puissants et utiles, certaines d'entre elles sont idéales à utiliser. Les listes suivantes proposent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.

**Envisagez d’utiliser ces fonctionnalités dans de nombreuses situations :**

* Notation par points (`x.Length`)
* Membres d’instance
* Constructeurs implicites
* Membres static
* Notation d’indexeur (`arr.[x]`)
* Arguments nommés et facultatifs
* Interfaces et implémentations d’interface

**N’atteignent pas tout d’abord pour ces fonctionnalités, mais judicieusement appliquent les lorsqu’ils sont pratiques résoudre un problème :**

* Surcharge de méthode
* Données mutables encapsulées
* Opérateurs sur les types
* Propriétés automatiques
* Implémentation `IDisposable` et `IEnumerable`
* Extensions de type
* Événements
* Structs
* Délégués
* Enums

**Généralement éviter ces fonctionnalités, sauf si vous devez les utiliser :**

* Hiérarchies de type basé sur l’héritage et l’héritage d’implémentation
* Les valeurs NULL et `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Préférer composition de l’héritage

[Composition au fil de l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome de longue date aussi simple que ça F# code peut respecter. Le principe fondamental est que vous ne devez pas exposer une classe de base et forcer les appelants d’hériter de cette classe de base pour obtenir les fonctionnalités.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Utiliser des expressions d’objet pour implémenter les interfaces si vous n’avez pas besoin d’une classe

[Expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, liant l’interface implémentée à une valeur sans avoir à le faire à l’intérieur d’une classe. C’est pratique, surtout si vous _uniquement_ devez implémenter l’interface et n’avez pas besoin d’une classe complète.

Par exemple, voici le code qui est exécuté dans [Ionide](http://ionide.io/) pour fournir une action de correction de code si vous avez ajouté un symbole que vous n’avez pas un `open` instruction pour :

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

Car il n’est pas nécessaire pour une classe lors de l’interaction avec l’API de Code Visual Studio, les Expressions d’objet sont un outil idéal pour cela. Ils sont également utiles pour tests unitaires, lorsque vous souhaitez remplacer une interface avec des routines de test de manière ad hoc.

## <a name="type-abbreviations"></a>Abréviations de types

[Abréviations de types](../language-reference/type-abbreviations.md) sont un moyen pratique d’attribuer une étiquette à un autre type, par exemple une signature de fonction ou un type plus complexe. Par exemple, l’alias suivant attribue une étiquette pour ce qui est nécessaire pour définir un calcul avec [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une bibliothèque d’apprentissage approfondi :

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Le `Computation` nom est un moyen pratique pour désigner n’importe quelle fonction qui correspond à la signature sont les alias. À l’aide des abréviations de types, comme cela est pratique et autorise le code plus concise.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Évitez d’utiliser des abréviations de Type pour représenter votre domaine

Bien que les abréviations de Type sont pratiques pour donner un nom pour les signatures de fonction, ils peuvent prêter à confus lors de l’abréviation d’autres types. Prenez en compte cette abréviation :

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Cela peut prêter à confusion de plusieurs façons :

* `BufferSize` n’est pas une abstraction ; C’est juste un autre nom d’un entier.
* Si `BufferSize` est exposé dans une API publique, il peut facilement être interprété à tort comme signifiant plus que `int`. En règle générale, les types de domaine d’avoir plusieurs attributs leur et ne sont pas des types primitifs comme `int`. Cette abréviation enfreint cette hypothèse.
* La casse de `BufferSize` (la casse Pascal) implique que ce type conserve plus de données.
* Cet alias n’offre pas de davantage de clarté par rapport à fournir un argument nommé à une fonction.
* L’abréviation se manifeste pas dans le IL compilé ; Il s’agit simplement d’un entier, et cet alias est une construction de compilation.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

En résumé, l’inconvénient avec les abréviations de Type est qu’ils sont **pas** abstractions sur les types qu’ils sont abréviation. Dans l’exemple précédent, `BufferSize` est simplement un `int` en coulisses, avec des données supplémentaires, ni aucun avantage à partir du système de type en dehors de ce que `int` possède déjà.
