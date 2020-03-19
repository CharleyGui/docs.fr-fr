---
title: Conventions de codage F#
description: Apprenez les lignes directrices générales et les idiomes lors de la rédaction du code F.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400308"
---
# <a name="f-coding-conventions"></a>Conventions de codage F#

Les conventions suivantes sont formulées à partir de l’expérience de travail avec de grandes bases de code F. Les [cinq principes d’un bon code F sont](index.md#five-principles-of-good-f-code) à la base de chaque recommandation. Ils sont liés aux lignes directrices de [conception des composants F,](component-design-guidelines.md)mais s’appliquent à tout code F, et pas seulement aux composants tels que les bibliothèques.

## <a name="organizing-code"></a>Code d’organisation

FMD dispose de deux façons principales d’organiser le code : les modules et les espaces de noms. Ceux-ci sont similaires, mais ont les différences suivantes:

* Les espaces de noms sont compilés sous forme d’espaces nominaux .NET. Les modules sont compilés sous forme de classes statiques.
* Les espaces de noms sont toujours de haut niveau. Les modules peuvent être de haut niveau et imbriqués dans d’autres modules.
* Les espaces de noms peuvent s’étendre sur plusieurs fichiers. Les modules ne peuvent pas.
* Modules peuvent être `[<RequireQualifiedAccess>]` décorés avec et `[<AutoOpen>]`.

Les lignes directrices suivantes vous aideront à les utiliser pour organiser votre code.

### <a name="prefer-namespaces-at-the-top-level"></a>Préférez les espaces de nom au plus haut niveau

Pour tout code consommable publiquement, les espaces nominatifs sont préférentiels pour les modules au plus haut niveau. Parce qu’ils sont compilés comme des espaces de nom .NET, ils sont consommables à partir de C ' sans aucun problème.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

L’utilisation d’un module de haut niveau peut ne pas apparaître différente lorsqu’elle est `MyClass` appelée `MyCode` uniquement à partir de F, mais pour les consommateurs de C, les appelants peuvent être surpris d’avoir à se qualifier avec le module.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Appliquer soigneusement`[<AutoOpen>]`

La `[<AutoOpen>]` construction peut polluer la portée de ce qui est disponible pour les appelants, et la réponse à l’endroit d’où quelque chose vient est «magique». Ce n’est pas une bonne chose. Une exception à cette règle est la bibliothèque de base de F 'elle-même (bien que ce fait soit également un peu controversé).

Cependant, il est pratique si vous avez la fonctionnalité d’aide pour une API publique que vous souhaitez organiser séparément de cette API publique.

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

Cela vous permet de séparer proprement les détails de mise en œuvre de l’API publique d’une fonction sans avoir à qualifier pleinement une aide chaque fois que vous l’appelez.

En outre, exposer les méthodes d’extension et les constructeurs `[<AutoOpen>]`d’expression au niveau de l’espace de nom peut être soigneusement exprimé avec .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Utiliser `[<RequireQualifiedAccess>]` chaque fois que les noms peuvent entrer en conflit ou vous sentez qu’il aide à la lisibilité

L’ajout de l’attribut `[<RequireQualifiedAccess>]` à un module indique que le module peut ne pas être ouvert et que les références aux éléments du module nécessitent un accès explicite et qualifié. Par exemple, `Microsoft.FSharp.Collections.List` le module a cet attribut.

Ceci est utile lorsque les fonctions et les valeurs du module ont des noms susceptibles d’entrer en conflit avec les noms d’autres modules. Exiger un accès qualifié peut grandement accroître la maintenance à long terme et l’évocabilité d’une bibliothèque.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Trier `open` les déclarations topologiquement

Dans l’ordre des déclarations, l’ordre des déclarations est important, y compris avec `open` les déclarations. Cela est différent de C, `using` `using static` où l’effet de et est indépendant de la commande de ces déclarations dans un fichier.

Dans le F, les éléments ouverts dans une portée peuvent faire l’ombre à d’autres personnes déjà présentes. Cela signifie que `open` la réorganisation des déclarations pourrait modifier le sens du code. En conséquence, tout tri arbitraire `open` de toutes les déclarations (par exemple, alphanumériquement) n’est pas recommandé, de peur que vous ne générez un comportement différent que vous pourriez vous attendre.

Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting); c’est-à-dire, commander vos `open` instructions dans l’ordre dans lequel les _couches_ de votre système sont définies. Faire le tri alphanumérique dans différentes couches topologiques peut également être considéré.

À titre d’exemple, voici le tri topologique pour le fichier API public du service de compilateur F :

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

Notez qu’une rupture de ligne sépare les couches topologiques, chaque couche étant triée alphanumériquement par la suite. Cela organise proprement le code sans ombrer accidentellement les valeurs.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Utiliser les classes pour contenir les valeurs qui ont des effets secondaires

Il y a plusieurs fois où l’initialisation d’une valeur peut avoir des effets secondaires, comme l’instantanéisation d’un contexte à une base de données ou à une autre ressource à distance. Il est tentant d’initialiser de telles choses dans un module et de l’utiliser dans les fonctions suivantes :

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

C’est souvent une mauvaise idée pour quelques raisons :

Tout d’abord, la configuration `dep1` de `dep2`l’application est poussée dans la base de code avec et . Ceci est difficile à maintenir dans de plus grandes bases de code.

Deuxièmement, les données parasmineuses statiques ne doivent pas inclure de valeurs qui ne sont pas sans danger si votre composant utilisera lui-même plusieurs threads. Cela est clairement `dep3`violé par .

Enfin, l’initialisation du module se transforme en un constructeur statique pour l’ensemble de l’unité de compilation. Si une erreur se produit dans l’initialisation de valeur `TypeInitializationException` lisible dans ce module, elle se manifeste comme une qui est ensuite mise en cache pour toute la durée de vie de l’application. Cela peut être difficile à diagnostiquer. Il ya généralement une exception interne que vous pouvez essayer de raisonner, mais s’il n’y en a pas, alors il n’y a pas de dire quelle est la cause profonde.

Au lieu de cela, il suffit d’utiliser une classe simple pour tenir des dépendances:

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Cela permet ce qui suit :

1. Pousser tout état dépendant en dehors de l’API lui-même.
2. La configuration peut maintenant se faire en dehors de l’API.
3. Les erreurs dans l’initialisation des valeurs `TypeInitializationException`dépendantes ne sont pas susceptibles de se manifester comme un .
4. L’API est maintenant plus facile à tester.

## <a name="error-management"></a>Gestion des erreurs

La gestion des erreurs dans les grands systèmes est une entreprise complexe et nuancée, et il n’y a pas de balles d’argent pour s’assurer que vos systèmes sont tolérants aux défauts et se comportent bien. Les lignes directrices suivantes devraient offrir des conseils sur la navigation dans cet espace difficile.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Représentez les cas d’erreur et l’état illégal dans des types intrinsèques à votre domaine

Avec [Discriminated Unions](../language-reference/discriminated-unions.md), Fmd vous donne la possibilité de représenter l’état défectueux du programme dans votre système de type. Par exemple :

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Dans ce cas, il existe trois façons connues que le retrait d’argent d’un compte bancaire peut échouer. Chaque cas d’erreur est représenté dans le type, et peut donc être traité en toute sécurité tout au long du programme.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

En général, si vous pouvez modéliser les différentes façons dont quelque chose peut **échouer** dans votre domaine, alors le code de traitement des erreurs n’est plus traité comme quelque chose que vous devez traiter en plus du flux régulier du programme. Il s’agit simplement d’une partie du flux de programme normal, et non considéré comme **exceptionnel**. Il y a deux avantages principaux à ceci :

1. Il est plus facile à maintenir que votre domaine change au fil du temps.
2. Les cas d’erreur sont plus faciles à tester.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Utiliser des exceptions lorsque les erreurs ne peuvent pas être représentées avec des types

Toutes les erreurs ne peuvent pas être représentées dans un domaine problématique. Ces types de défauts sont de nature *exceptionnelle,* d’où la capacité d’augmenter et d’attraper des exceptions dans le F.

Tout d’abord, il est recommandé que vous lisiez les [lignes directrices de conception d’exception](../../standard/design-guidelines/exceptions.md). Celles-ci s’appliquent également à la F.

Les principales constructions disponibles en FMD aux fins de l’augmentation des exceptions devraient être prises en considération dans l’ordre de préférence suivant :

| Fonction | Syntaxe | Objectif |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Soulève `System.ArgumentNullException` un avec le nom d’argument spécifié. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Soulève `System.ArgumentException` un avec un nom d’argument spécifié et un message. |
| `invalidOp` | `invalidOp "message"` | Soulève `System.InvalidOperationException` un avec le message spécifié. |
|`raise`| `raise (ExceptionType("message"))` | Mécanisme à usage général pour jeter des exceptions. |
| `failwith` | `failwith "message"` | Soulève `System.Exception` un avec le message spécifié. |
| `failwithf` | `failwithf "format string" argForFormatString` | Relance `System.Exception` un message déterminé par la chaîne de format et ses entrées. |

`nullArg`Utilisez, `invalidArg` `invalidOp` et comme mécanisme `ArgumentNullException` `ArgumentException` à `InvalidOperationException` jeter, et le cas échéant.

Les `failwith` `failwithf` fonctions et les fonctions doivent `Exception` généralement être évitées parce qu’elles soulèvent le type de base, et non une exception spécifique. Conformément aux lignes directrices sur la [conception des exceptions,](../../standard/design-guidelines/exceptions.md)vous souhaitez soulever des exceptions plus précises lorsque vous le pouvez.

### <a name="using-exception-handling-syntax"></a>Utilisation de la syntaxe de manipulation d’exceptions

FMD prend en `try...with` charge les modèles d’exception via la syntaxe :

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Concilier fonctionnalité à effectuer face à une exception avec l’appariement des motifs peut être un peu difficile si vous souhaitez garder le code propre. Une telle façon de gérer cela est d’utiliser [des modèles actifs](../language-reference/active-patterns.md) comme un moyen de regrouper les fonctionnalités entourant un cas d’erreur à une exception elle-même. Par exemple, vous pouvez consommer une API qui, lorsqu’elle fait une exception, contient des informations précieuses dans les métadonnées d’exception. Déballer une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et le retour de cette valeur peut être utile dans certaines situations.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>N’utilisez pas la manipulation d’erreur monadic pour remplacer les exceptions

Les exceptions sont considérées comme quelque peu taboues dans la programmation fonctionnelle. En effet, les exceptions violent la pureté, il est donc sûr de les considérer pas tout à fait fonctionnel. Cependant, cela ignore la réalité de l’endroit où le code doit s’exécuter, et que des erreurs de temps d’exécution peuvent se produire. En général, écrire du code sur l’hypothèse que la plupart des choses ne sont ni pures ni totales, pour minimiser les mauvaises surprises.

Il est important de tenir compte des forces/aspects fondamentaux suivants des exceptions en ce qui concerne leur pertinence et leur pertinence dans l’écosystème .NET runtime et cross-language dans son ensemble :

1. Ils contiennent des informations diagnostiques détaillées, ce qui est très utile lors de la débogage d’un problème.
2. Ils sont bien compris par le runtime et d’autres langues .NET.
3. Ils peuvent réduire la plaque chauffante importante par rapport au code qui fait des ravages pour *éviter* les exceptions en mettant en œuvre un sous-ensemble de leur sémantique sur une base ad hoc.

Ce troisième point est essentiel. Pour les opérations non complexes non complexes, le défaut d’utiliser des exceptions peut entraîner des relations avec des structures comme celle-ci :

```fsharp
Result<Result<MyType, string>, string list>
```

Ce qui peut facilement conduire à un code fragile comme l’appariement des motifs sur les erreurs de « stringly-typed » :

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

En outre, il peut être tentant d’avaler n’importe quelle exception dans le désir d’une fonction "simple" qui renvoie un type "plus agréable":

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Malheureusement, `tryReadAllText` peut jeter de nombreuses exceptions basées sur la myriade de choses qui peuvent se produire sur un système de fichiers, et ce code écarte toute information sur ce qui pourrait réellement aller mal dans votre environnement. Si vous remplacez ce code par un type de résultat, alors vous revenez à l’analyse de messages d’erreur « tapé » :

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

Et placer l’objet `Error` d’exception lui-même dans le constructeur vous oblige juste à traiter correctement avec le type d’exception au site d’appel plutôt que dans la fonction. Cela crée efficacement des exceptions vérifiées, qui sont notoirement non parfumés à traiter comme un appelant d’une API.

Une bonne alternative aux exemples ci-dessus est d’attraper des exceptions *précises* et de retourner une valeur significative dans le contexte de cette exception. Si vous `tryReadAllText` modifiez la `None` fonction comme suit, a plus de sens:

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Au lieu de fonctionner comme un fourre-tout, cette fonction va maintenant gérer correctement le cas quand un fichier n’a pas été trouvé et attribuer ce sens à une déclaration. Cette valeur de retour peut être cartographe dans ce cas d’erreur, tout en ne rejetant aucune information contextuelle ou en forçant les appelants à traiter une affaire qui peut ne pas être pertinente à ce moment-là dans le code.

Les types `Result<'Success, 'Error>` tels que sont appropriés pour les opérations de base où ils ne sont pas imbriqués, et les types optionnels F sont parfaits pour représenter quand quelque chose pourrait soit retourner *quelque chose* ou *rien*. Ils ne remplacent toutefois pas les exceptions et ne devraient pas être utilisés pour tenter de remplacer les exceptions. Ils devraient plutôt être appliqués judicieusement pour aborder des aspects précis de la politique d’exception et de gestion des erreurs de façon ciblée.

## <a name="partial-application-and-point-free-programming"></a>Application partielle et programmation sans point

FMD prend en charge l’application partielle, et donc, de diverses façons de programmer dans un style sans point. Cela peut être bénéfique pour la réutilisation du code dans un module ou la mise en œuvre de quelque chose, mais ce n’est pas quelque chose à exposer publiquement. En général, la programmation sans point n’est pas une vertu en soi, et peut ajouter une barrière cognitive importante pour les personnes qui ne sont pas immergés dans le style.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>N’utilisez pas l’application partielle et le curry dans les API publiques

À peu près d’exception, l’utilisation d’une application partielle dans les API publiques peut prêter à confusion pour les consommateurs. Habituellement, `let`les valeurs liées dans le code F sont des **valeurs,** pas **des valeurs de fonction**. Mélanger les valeurs et les valeurs de fonction peut permettre d’économiser un petit nombre de lignes `>>` de code en échange d’un certain nombre de frais généraux cognitifs, surtout s’ils sont combinés avec des opérateurs tels que pour composer des fonctions.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Tenir compte des implications en ce qui a eu pour la programmation sans point

Les fonctions au curry n’étiquetent pas leurs arguments. Cela a des implications d’outillage. Considérez les deux fonctions suivantes :

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Les deux sont des `funcWithApplication` fonctions valides, mais est une fonction au curry. Lorsque vous survolez leurs types dans un éditeur, vous voyez ceci:

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Sur le site d’appel, les outils dans l’outillage tels que `string` `int` Visual Studio ne vous donneront pas d’informations significatives sur ce que les types et les types d’entrée représentent réellement.

Si vous rencontrez un `funcWithApplication` code sans point comme celui-ci est publiquement consommable, il est recommandé de faire une extension complète afin que l’outillage peut ramasser sur des noms significatifs pour les arguments.

En outre, débogage de code sans point peut être difficile, voire impossible. Les outils de débogage s’appuient `let` sur des valeurs liées aux noms (par exemple, les fixations) afin que vous puissiez inspecter les valeurs intermédiaires à mi-parcours de l’exécution. Lorsque votre code n’a pas de valeurs à inspecter, il n’y a rien à déboiffer. À l’avenir, des outils de débogage peuvent évoluer pour synthétiser ces valeurs en fonction de chemins précédemment exécutés, mais ce n’est pas une bonne idée de couvrir vos paris sur les fonctionnalités *potentielles* de débogage.

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Considérez l’application partielle comme une technique pour réduire la plaque chauffante interne

Contrairement au point précédent, l’application partielle est un outil merveilleux pour réduire la plaque chauffante à l’intérieur d’une application ou les internes plus profonds d’une API. Il peut être utile pour tester unitaire la mise en œuvre d’API plus compliquées, où la plaque chauffante est souvent une douleur à traiter. Par exemple, le code suivant montre comment vous pouvez accomplir ce que la plupart des cadres moqueurs vous donnent sans prendre une dépendance externe à un tel cadre et d’avoir à apprendre une API sur mesure connexes.

Par exemple, considérez la topographie de solution suivante :

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`pourrait exposer le code tel que :

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Les `Transactions.doTransaction` tests `ImplementationLogic.Tests.fsproj` unitaires sont faciles :

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

L’application `doTransaction` partielle avec un objet contextuelle vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir besoin de construire un contexte simulé à chaque fois :

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

Cette technique ne doit pas être universellement appliquée à votre base de code entière, mais c’est un bon moyen de réduire la plaque chauffante pour les internes compliqués et les tests unitaires de ces internes.

## <a name="access-control"></a>Contrôle d’accès

F a plusieurs options pour [le contrôle d’accès](../language-reference/access-control.md), hérité de ce qui est disponible dans le temps d’exécution .NET. Ceux-ci ne sont pas seulement utilisables pour les types - vous pouvez les utiliser pour des fonctions, aussi.

* Préférez les`public` non-types et les membres jusqu’à ce que vous en ayez besoin pour être consommables publiquement. Cela minimise également ce que les consommateurs couple à.
* Efforcez-vous de conserver `private`toutes les fonctionnalités d’aide .
* Considérez l’utilisation d’un `[<AutoOpen>]` module privé de fonctions d’aide si elles deviennent nombreuses.

## <a name="type-inference-and-generics"></a>Inférence de type et génériques

L’inférence de type peut vous éviter de taper beaucoup de plaques chauffantes. Et la généralisation automatique dans le compilateur de F peut vous aider à écrire plus de code générique sans aucun effort supplémentaire de votre part. Cependant, ces caractéristiques ne sont pas universellement bonnes.

* Envisagez d’étiqueter les noms d’arguments avec des types explicites dans les API publiques et ne vous fiez pas à l’inférence de type pour cela.

    La raison en est que **vous** devriez être en contrôle de la forme de votre API, pas le compilateur. Bien que le compilateur peut faire un excellent travail à déduire les types pour vous, il est possible d’avoir la forme de votre changement API si les internes qu’il s’appuie sur ont changé les types. C’est peut-être ce que vous voulez, mais il en résultera presque certainement un changement d’API qui brisera que les consommateurs en aval devront alors faire face. Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, alors vous pouvez contrôler ces changements de rupture. En termes de DDD, cela peut être considéré comme une couche anti-corruption.

* Envisagez de donner un nom significatif à vos arguments génériques.

    Sauf si vous écrivez un code vraiment générique qui n’est pas spécifique à un domaine particulier, un nom significatif peut aider d’autres programmeurs à comprendre le domaine dans lequel ils travaillent. Par exemple, un `'Document` paramètre type nommé dans le contexte de l’interaction avec une base de données de documents indique plus clairement que les types de documents génériques peuvent être acceptés par la fonction ou le membre avec lequel vous travaillez.

* Envisagez de nommer des paramètres de type générique avec PascalCase.

    C’est la façon générale de faire les choses en .NET, il est donc recommandé que vous utilisez PascalCase plutôt que snake_case ou camelCase.

Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes qui sont nouvelles à F ou une grande base de code. Il y a des frais généraux cognitifs dans l’utilisation des composants qui sont génériques. En outre, si les fonctions automatiquement généralisées ne sont pas utilisées avec différents types d’entrées (et encore moins si elles sont destinées à être utilisées en tant que telles), alors il n’y a aucun avantage réel pour eux d’être générique à ce moment-là. Considérez toujours si le code que vous écrivez bénéficiera réellement d’être générique.

## <a name="performance"></a>Performances

### <a name="prefer-structs-for-small-data-types"></a>Préférez les structs pour les petits types de données

L’utilisation de structs (également appelées types de valeurs) peut souvent entraîner des performances plus élevées pour certains codes, car il évite généralement d’attribuer des objets. Cependant, les structs ne sont pas toujours un bouton « aller plus vite » : si la taille des données dans une struct dépasse 16 octets, la copie des données peut souvent entraîner plus de temps de processeur que d’utiliser un type de référence.

Pour déterminer si vous devez utiliser une struct, considérez les conditions suivantes :

- Si la taille de vos données est de 16 octets ou plus petit.
- Si vous êtes susceptible d’avoir beaucoup de ces types de données résident dans la mémoire dans un programme en cours d’exécution.

Si la première condition s’applique, vous devriez généralement utiliser une struct. Si les deux s’appliquent, vous devriez presque toujours utiliser une struct. Il peut y avoir certains cas où les conditions précédentes s’appliquent, mais l’utilisation d’une struct n’est pas meilleure ou pire que l’utilisation d’un type de référence, mais ils sont susceptibles d’être rares. Il est important de toujours mesurer lors de faire des changements comme celui-ci, cependant, et ne pas fonctionner sur l’hypothèse ou l’intuition.

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>Préférez les tuples struct lors du regroupement de petits types de valeur

Considérez les deux fonctions suivantes :

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

Lorsque vous comparez ces fonctions avec un outil de benchmarking statistique `runWithStructTuple` comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que la fonction qui utilise des tuples struct est 40% plus rapide et n’alloue aucune mémoire.

Cependant, ces résultats ne seront pas toujours le cas dans votre propre code. Si vous marquez `inline`une fonction comme , le code qui utilise des tuples de référence peut obtenir quelques optimisations supplémentaires, ou le code qui allouerait pourrait tout simplement être optimisé. Vous devez toujours mesurer les résultats chaque fois que les performances sont concernées, et ne jamais fonctionner sur la base de l’hypothèse ou l’intuition.

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>Préférez les enregistrements de struct lorsque le type de données est faible

La règle de base décrite précédemment détient également pour [les types de disques F .](../language-reference/records.md) Considérez les types et fonctions de données suivants qui les traitent :

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

Ceci est similaire au code de tuple précédent, mais cette fois l’exemple utilise des enregistrements et une fonction intérieure inlinisée.

Lorsque vous comparez ces fonctions avec un outil de benchmarking `processStructPoint` statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que fonctionne près de 60% plus rapidement et n’alloue rien sur le tas géré.

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>Préférez les syndicats discriminés structurés lorsque le type de données est faible

Les observations précédentes sur la performance avec des tuples et des dossiers structurants sont également valables pour [les syndicats discriminés](../language-reference/discriminated-unions.md). Examinons le code ci-dessous.

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

Il est courant de définir des unions discriminées à un seul cas comme celle-ci pour la modélisation de domaine. Lorsque vous comparez ces fonctions avec un outil de benchmarking `structReverseName` statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous trouverez que fonctionne environ 25% plus vite que `reverseName` pour les petites chaînes. Pour les grosses cordes, les deux exécutent à peu près la même chose. Donc, dans ce cas, il est toujours préférable d’utiliser une struct. Comme mentionné précédemment, mesurez toujours et ne fonctionnent pas sur des hypothèses ou des intuitions.

Bien que l’exemple précédent ait montré qu’une union discriminée structed a donné de meilleurs résultats, il est courant d’avoir de plus grands unions discriminées lors de la modélisation d’un domaine. Les types de données plus grands comme celui-ci peuvent ne pas fonctionner aussi bien s’ils sont structs en fonction des opérations sur eux, puisque plus de copie pourrait être impliquée.

### <a name="functional-programming-and-mutation"></a>Programmation fonctionnelle et mutation

Les valeurs F sont immuables par défaut, ce qui vous permet d’éviter certaines catégories de bogues (en particulier ceux impliquant la concurrence et le parallélisme). Cependant, dans certains cas, afin d’atteindre une efficacité optimale (voire raisonnable) du temps d’exécution ou des allocations de mémoire, une durée de travail peut être mieux mise en œuvre en utilisant la mutation sur place de l’état. Ceci est possible dans une base d’opt-in avec F avec le `mutable` mot clé.

L’utilisation de l’inF `mutable` peut se sentir en contradiction avec la pureté fonctionnelle. C’est compréhensible, mais la pureté fonctionnelle partout peut être en contradiction avec les objectifs de performance. Un compromis est d’encapsuler la mutation de telle sorte que les appelants n’ont pas besoin de se soucier de ce qui se passe quand ils appellent une fonction. Cela vous permet d’écrire une interface fonctionnelle sur une implémentation basée sur la mutation pour le code critique des performances.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Enveloppez le code mutable dans des interfaces immuables

Avec la transparence référentielle comme objectif, il est essentiel d’écrire du code qui n’expose pas le ventre mutable des fonctions critiques de performance. Par exemple, le code `Array.contains` suivant implémente la fonction dans la bibliothèque de base de FMD :

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

Appeler cette fonction plusieurs fois ne change pas le tableau sous-jacent, ni ne vous oblige à maintenir un état mutable en le consommant. Il est référentiellement transparent, même si presque toutes les lignes de code en son sein utilisent la mutation.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Envisagez d’encapsulant des données mutables dans les classes

L’exemple précédent utilisait une seule fonction pour encapsuler les opérations à l’aide de données mutables. Ce n’est pas toujours suffisant pour des ensembles de données plus complexes. Considérez les ensembles de fonctions suivants :

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

Ce code est performant, mais il expose la structure de données basée sur la mutation que les appelants sont responsables du maintien. Ceci peut être enveloppé à l’intérieur d’une classe sans membres sous-jacents qui peuvent changer :

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

`Closure1Table`encapsule la structure de données sous-jacente basée sur la mutation, ce qui ne force pas les appelants à maintenir la structure de données sous-jacente. Les cours sont un moyen puissant d’encapsuler les données et les routines qui sont basées sur les mutations sans exposer les détails aux appelants.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Préférez `let mutable` les cellules de référence

Les cellules de référence sont un moyen de représenter la référence à une valeur plutôt qu’à la valeur elle-même. Bien qu’ils puissent être utilisés pour le code critique des performances, ils ne sont pas recommandés. Prenons l’exemple suivant :

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

L’utilisation d’une cellule de référence « pollue » maintenant tout code subséquent en ayant à déreférencer et à recouper les données sous-jacentes. Au lieu `let mutable`de cela, considérez :

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Mis à part le seul point de mutation au milieu de `acc` l’expression lambda, tout autre code qui `let`touche peut le faire d’une manière qui n’est pas différente de l’utilisation d’une valeur immuable normale liée. Cela facilitera le changement avec le temps.

## <a name="object-programming"></a>Programmation d’objets

FMD bénéficie d’un support complet pour les objets et les concepts orientés objet (OO). Bien que de nombreux concepts OO sont puissants et utiles, pas tous d’entre eux sont idéaux à utiliser. Les listes suivantes offrent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.

**Envisagez d’utiliser ces fonctionnalités dans de nombreuses situations :**

* Notation par`x.Length`points ( )
* Membres d’instance
* Constructeurs implicites
* Membres static
* Notation de`arr.[x]`l’indexeur ( )
* Arguments nommés et facultatifs
* Interfaces et implémentations d’interfaces

**N’atteignez pas ces fonctionnalités d’abord, mais ne les appliquer judicieusement quand ils sont commodes pour résoudre un problème:**

* Surcharge de méthode
* Données mutables encapsulées
* Opérateurs sur les types
* Propriétés automobiles
* Mise `IDisposable` en œuvre et mise en œuvre`IEnumerable`
* Extensions de type
* Événements
* Structs
* Délégués
* Enums

**Évitez généralement ces fonctionnalités à moins que vous ne les utilisiez :**

* Hiérarchies de type fondées sur l’héritage et héritage de mise en œuvre
* Nuls et`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Préférez la composition à l’héritage

[La composition sur l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome de longue date auquel un bon code F peut adhérer. Le principe fondamental est que vous ne devriez pas exposer une classe de base et forcer les appelants à hériter de cette classe de base pour obtenir des fonctionnalités.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Utilisez des expressions d’objets pour implémenter des interfaces si vous n’avez pas besoin d’une classe

[Les expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, liant l’interface implémentée à une valeur sans avoir besoin de le faire à l’intérieur d’une classe. C’est pratique, surtout si vous _n’avez_ besoin que d’implémenter l’interface et n’avez pas besoin d’une classe complète.

Par exemple, voici le code qui est exécuté dans [Ionide](http://ionide.io/) pour fournir une action de correction `open` de code si vous avez ajouté un symbole que vous n’avez pas une déclaration pour :

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

Parce qu’il n’est pas nécessaire d’avoir une classe lors de l’interaction avec l’API Visual Studio Code, Les expressions d’objets sont un outil idéal pour cela. Ils sont également précieux pour les tests unitaires, lorsque vous voulez talon sur une interface avec des routines de test d’une manière ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Considérez les abréviations de type pour raccourcir les signatures

[Les abréviations de type](../language-reference/type-abbreviations.md) sont un moyen pratique d’attribuer une étiquette à un autre type, comme une signature de fonction ou un type plus complexe. Par exemple, l’alias suivant attribue une étiquette à ce qui est nécessaire pour définir un calcul avec [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une bibliothèque d’apprentissage profond :

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Le `Computation` nom est un moyen pratique de désigner toute fonction qui correspond à la signature qu’il est aliasing. L’utilisation d’abréviations de type comme celle-ci est pratique et permet un code plus succinct.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Évitez d’utiliser des abréviations de type pour représenter votre domaine

Bien que les abréviations de type soient pratiques pour donner un nom aux signatures de fonction, elles peuvent être confuses lors de l’abréviation d’autres types. Considérez cette abréviation :

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Cela peut être déroutant de multiples façons :

* `BufferSize`n’est pas une abstraction; c’est juste un autre nom pour un integer.
* Si `BufferSize` elle est exposée dans une API publique, elle peut `int`facilement être mal interprétée comme signifiant plus que simplement. Généralement, les types de domaine ont plusieurs attributs pour eux et ne sont pas des types primitifs comme `int`. Cette abréviation viole cette hypothèse.
* Le boîtier `BufferSize` de (PascalCase) implique que ce type contient plus de données.
* Ce pseudonyme n’offre pas une clarté accrue par rapport à la fourniture d’un argument nommé à une fonction.
* L’abréviation ne se manifestera pas dans l’IL compilé; c’est juste un intégrant et ce alias est une construction de compile-temps.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

En résumé, l’écueil avec les abréviations de type est qu’ils ne sont **pas** des abstractions sur les types qu’ils abrégé. Dans l’exemple `BufferSize` précédent, `int` est juste un sous les couvertures, sans données `int` supplémentaires, ni aucun avantage du système de type en dehors de ce qui a déjà.

Une autre approche de l’utilisation d’abréviations de type pour représenter un domaine consiste à utiliser des syndicats à cas unique et discriminés. L’échantillon précédent peut être modélisé comme suit :

```fsharp
type BufferSize = BufferSize of int
```

Si vous écrivez du `BufferSize` code qui fonctionne en termes de et sa valeur sous-jacente, vous devez en construire un plutôt que de passer dans n’importe quel intégrant arbitraire :

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Cela réduit la probabilité de passer par erreur un `send` integer arbitraire dans `BufferSize` la fonction, parce que l’appelant doit construire un type pour envelopper une valeur avant d’appeler la fonction.
