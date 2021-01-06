---
title: Conventions de codage F#
description: 'Découvrez des instructions générales et des idiomes lors de l’écriture de code F #.'
ms.date: 01/5/2021
ms.openlocfilehash: e69ceb2f3c37404ca8d8ed972f985340e62ecb59
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938687"
---
# <a name="f-coding-conventions"></a>Conventions de codage F#

Les conventions suivantes sont formulées à partir de l’expérience de l’utilisation de bases de code F # volumineuses. Les [cinq principes du bon code F #](index.md#five-principles-of-good-f-code) constituent la base de chaque recommandation. Ils sont liés aux [règles de conception des composants f #](component-design-guidelines.md), mais s’appliquent à tout code f #, et pas seulement aux composants tels que les bibliothèques.

## <a name="organizing-code"></a>Organisation du code

F # présente deux méthodes principales pour organiser le code : les modules et les espaces de noms. Celles-ci sont similaires, mais elles présentent les différences suivantes :

* Les espaces de noms sont compilés en tant qu’espaces de noms .NET. Les modules sont compilés en tant que classes statiques.
* Les espaces de noms sont toujours de niveau supérieur. Les modules peuvent être de niveau supérieur et imbriqués dans d’autres modules.
* Les espaces de noms peuvent s’étendre sur plusieurs fichiers. Les modules ne peuvent pas.
* Les modules peuvent être décorés avec `[<RequireQualifiedAccess>]` et `[<AutoOpen>]` .

Les instructions suivantes vous aideront à les utiliser pour organiser votre code.

### <a name="prefer-namespaces-at-the-top-level"></a>Préférer les espaces de noms au niveau supérieur

Pour tout code consommateur public, les espaces de noms sont préférentiels aux modules au niveau supérieur. Étant donné qu’ils sont compilés en tant qu’espaces de noms .NET, ils peuvent être consommés à partir de C# sans aucun problème.

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

L’utilisation d’un module de niveau supérieur peut ne pas apparaître différente quand elle est appelée uniquement à partir de F #, mais pour les consommateurs C#, les appelants peuvent être surpris par le fait d’avoir à qualifier `MyClass` le `MyCode` module.

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>Appliquer avec prudence `[<AutoOpen>]`

La `[<AutoOpen>]` construction peut polluer l’étendue de ce qui est disponible pour les appelants, et la réponse à l’origine d’un élément provient de « Magic ». Ce n’est pas une bonne chose. La bibliothèque principale F # est une exception à cette règle (bien que ce fait soit également un peu controversé).

Toutefois, cela est pratique si vous disposez d’une fonctionnalité d’assistance pour une API publique que vous souhaitez organiser séparément de cette API publique.

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

Cela vous permet de séparer correctement les détails de l’implémentation de l’API publique d’une fonction sans avoir à qualifier complètement une application d’assistance chaque fois que vous l’appelez.

En outre, l’exposition des méthodes d’extension et des générateurs d’expressions au niveau de l’espace de noms peut être clairement exprimée avec `[<AutoOpen>]` .

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>Utilisez `[<RequireQualifiedAccess>]` quand les noms peuvent entrer en conflit ou que vous estimez qu’ils facilitent la lisibilité

L’ajout `[<RequireQualifiedAccess>]` de l’attribut à un module indique que le module ne peut pas être ouvert et que les références aux éléments du module requièrent un accès qualifié explicite. Par exemple, le `Microsoft.FSharp.Collections.List` module a cet attribut.

Cela est utile lorsque les fonctions et valeurs du module ont des noms qui sont susceptibles d’entrer en conflit avec des noms dans d’autres modules. La nécessité d’un accès qualifié peut augmenter la maintenabilité à long terme et la évolutivité d’une bibliothèque.

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>Trier les `open` instructions topologiquement

En F #, l’ordre des déclarations est important, y compris avec les `open` instructions. Cela est différent de C#, où l’effet de `using` et `using static` est indépendant de l’ordre des instructions dans un fichier.

En F #, les éléments ouverts dans une portée peuvent masquer d’autres personnes déjà présentes. Cela signifie que `open` les instructions de réorganisation peuvent modifier la signification du code. Par conséquent, tout tri arbitraire de toutes les `open` instructions (par exemple, dans l’ordre alphanumérique) n’est pas recommandé, mais vous ne pouvez pas générer un comportement différent.

Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting). autrement dit, classez vos `open` instructions dans l’ordre dans lequel les _couches_ de votre système sont définies. Le tri alphanumérique au sein de différentes couches topologiques peut également être envisagé.

À titre d’exemple, voici le tri topologique du fichier d’API publique du service du compilateur F # :

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open FSharp.Compiler
open FSharp.Compiler.AbstractIL
open FSharp.Compiler.AbstractIL.Diagnostics
open FSharp.Compiler.AbstractIL.IL
open FSharp.Compiler.AbstractIL.ILBinaryReader
open FSharp.Compiler.AbstractIL.Internal
open FSharp.Compiler.AbstractIL.Internal.Library

open FSharp.Compiler.AccessibilityLogic
open FSharp.Compiler.Ast
open FSharp.Compiler.CompileOps
open FSharp.Compiler.CompileOptions
open FSharp.Compiler.Driver

open Internal.Utilities
open Internal.Utilities.Collections
```

Notez qu’un saut de ligne sépare les couches topologiques, chaque couche étant triée par ordre alphabétique par la suite. Cette classe organise correctement le code sans occulter accidentellement des valeurs.

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>Utiliser des classes pour contenir des valeurs qui ont des effets secondaires

Il existe de nombreuses fois que l’initialisation d’une valeur peut avoir des effets secondaires, par exemple l’instanciation d’un contexte à une base de données ou à une autre ressource distante. Il est tentant d’initialiser ces éléments dans un module et de les utiliser dans les fonctions suivantes :

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/<name>/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

C’est souvent une mauvaise idée pour plusieurs raisons :

Tout d’abord, la configuration de l’application est envoyée au code base avec `dep1` et `dep2` . Cela est difficile à maintenir dans les codes base plus volumineux.

Deuxièmement, les données initialisées statiquement ne doivent pas inclure de valeurs qui ne sont pas thread-safe si votre composant utilise lui-même plusieurs threads. Cela est clairement violé par `dep3` .

Enfin, l’initialisation de module se compile en un constructeur statique pour l’ensemble de l’unité de compilation. Si une erreur se produit dans l’initialisation de la valeur liée à Let dans ce module, elle est manifeste en tant `TypeInitializationException` que qui est ensuite mis en cache pour toute la durée de vie de l’application. Cela peut être difficile à diagnostiquer. Il y a généralement une exception interne que vous pouvez essayer de créer, mais si ce n’est pas le cas, il n’y a pas d’objet indiquant la cause racine.

Au lieu de cela, il vous suffit d’utiliser une classe simple pour stocker les dépendances :

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

Cela permet d’activer les éléments suivants :

1. Envoi d’un État dépendant en dehors de l’API elle-même.
2. La configuration peut maintenant être effectuée en dehors de l’API.
3. Les erreurs dans l’initialisation des valeurs dépendantes ne sont pas susceptibles de se manifester en tant que `TypeInitializationException` .
4. L’API est désormais plus facile à tester.

## <a name="error-management"></a>Gestion des erreurs

La gestion des erreurs dans les systèmes de grande taille est un effort complexe et en nuances de temps, et il n’y a pas de puce Silver pour s’assurer que vos systèmes sont tolérants aux pannes et se comportent correctement. Les instructions suivantes doivent vous aider à naviguer dans cet espace difficile.

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>Représenter des cas d’erreur et un État non conforme dans des types intrinsèques à votre domaine

Avec les [unions discriminées](../language-reference/discriminated-unions.md), F # vous donne la possibilité de représenter un état de programme défectueux dans votre système de type. Par exemple :

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

Dans ce cas, il existe trois façons connues de retirer de l’argent d’un compte bancaire. Chaque cas d’erreur est représenté dans le type et peut donc être traité en toute sécurité dans tout le programme.

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn $"Successfully withdrew %f{am}"
    | InsufficientFunds balance -> printfn $"Failed: balance is %f{balance}"
    | CardExpired expiredDate -> printfn $"Failed: card expired on {expiredDate}"
    | UndisclosedFailure -> printfn "Failed: unknown"
```

En général, si vous pouvez modéliser les différentes façons dont un événement peut **échouer** dans votre domaine, le code de gestion des erreurs n’est plus traité comme un problème que vous devez traiter en plus du déroulement normal du programme. Il s’agit simplement d’une partie du déroulement normal du programme et n’est pas considéré comme **exceptionnel**. Cela présente deux avantages principaux :

1. Il est plus facile à gérer lorsque votre domaine évolue dans le temps.
2. Les cas d’erreur sont plus faciles à tester par unité.

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>Utiliser des exceptions lorsque des erreurs ne peuvent pas être représentées avec des types

Toutes les erreurs ne peuvent pas être représentées dans un domaine posant problème. Ces types d’erreurs sont de nature *exceptionnelle* , par conséquent la possibilité de déclencher et d’intercepter des exceptions en F #.

Tout d’abord, il est recommandé de lire les [règles de conception des exceptions](../../standard/design-guidelines/exceptions.md). Elles s’appliquent également à F #.

Les constructions principales disponibles en F # à des fins de déclenchement d’exceptions doivent être prises en compte dans l’ordre de préférence suivant :

| Fonction | Syntaxe | Objectif |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | Déclenche un `System.ArgumentNullException` avec le nom d’argument spécifié. |
| `invalidArg` | `invalidArg "argumentName" "message"` | Déclenche un `System.ArgumentException` avec un nom d’argument et un message spécifiés. |
| `invalidOp` | `invalidOp "message"` | Déclenche un `System.InvalidOperationException` avec le message spécifié. |
|`raise`| `raise (ExceptionType("message"))` | Mécanisme à usage général pour lever des exceptions. |
| `failwith` | `failwith "message"` | Déclenche un `System.Exception` avec le message spécifié. |
| `failwithf` | `failwithf "format string" argForFormatString` | Déclenche un `System.Exception` avec un message déterminé par la chaîne de format et ses entrées. |

Utilisez `nullArg` , `invalidArg` et `invalidOp` comme mécanisme de levée `ArgumentNullException` et, `ArgumentException` le `InvalidOperationException` cas échéant.

Les `failwith` `failwithf` fonctions et doivent généralement être évitées, car elles lèvent le type de base `Exception` , et non une exception spécifique. Conformément aux [règles de conception d’exception](../../standard/design-guidelines/exceptions.md), vous souhaitez déclencher des exceptions plus spécifiques lorsque vous le pouvez.

### <a name="use-exception-handling-syntax"></a>Utiliser la syntaxe de gestion des exceptions

F # prend en charge les modèles d’exception via la `try...with` syntaxe suivante :

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

Le rapprochement des fonctionnalités à effectuer en cas d’exception avec les critères spéciaux peut être un peu délicat si vous souhaitez que le code reste propre. Pour ce faire, il est possible d’utiliser des [modèles actifs](../language-reference/active-patterns.md) comme moyen de regrouper les fonctionnalités entourant un cas d’erreur avec une exception. Par exemple, vous pouvez consommer une API qui, lorsqu’elle lève une exception, englobe des informations précieuses dans les métadonnées d’exception. La désencapsulation d’une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et le retour de cette valeur peut être utile dans certaines situations.

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>N’utilisez pas la gestion des erreurs monadic pour remplacer les exceptions

Les exceptions sont souvent considérées comme des Taboo dans la programmation fonctionnelle. En effet, les exceptions enfreignent la pureté, donc il est préférable de les considérer comme non très fonctionnelles. Toutefois, cela ignore la réalité de l’emplacement où le code doit s’exécuter et les erreurs d’exécution peuvent se produire. En général, écrivez du code sur l’hypothèse que la plupart des choses ne sont ni pures ni totales, afin de minimiser les surprises.

Il est important de prendre en compte les points forts/aspects d’exception suivants en ce qui concerne leur pertinence et leur adéquation dans le Runtime .NET et l’écosystème interlangage dans son ensemble :

1. Elles contiennent des informations de diagnostic détaillées, ce qui est très utile lors du débogage d’un problème.
2. Elles sont bien comprises par le runtime et d’autres langages .NET.
3. Ils peuvent réduire les réemplois importants par rapport au code qui *ne permet pas d’éviter* les exceptions en implémentant un sous-ensemble de leur sémantique sur une base ad hoc.

Ce troisième point est essentiel. Pour les opérations complexes non triviales, l’échec de l’utilisation d’exceptions peut entraîner une gestion des structures comme suit :

```fsharp
Result<Result<MyType, string>, string list>
```

Ce qui peut facilement entraîner un code fragile comme la mise en correspondance de modèle sur les erreurs de type « chaîne » :

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

En outre, il peut être tentant d’absorber une exception dans le désir d’une fonction « simple » qui retourne un type « plus attrayant » :

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

Malheureusement, `tryReadAllText` peut lever de nombreuses exceptions en fonction de la myriade de choses qui peuvent se produire sur un système de fichiers, et ce code rejette toutes les informations sur ce qui peut en fait être erroné dans votre environnement. Si vous remplacez ce code par un type de résultat, vous revenez à l’analyse du message d’erreur « typé en chaîne » :

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

Et le placement de l’objet exception lui-même dans le `Error` constructeur vous oblige simplement à gérer correctement le type d’exception sur le site d’appel plutôt que dans la fonction. Cela permet de créer efficacement des exceptions vérifiées, qui sont notoirement unfun pour traiter en tant qu’appelant d’une API.

Une bonne alternative aux exemples ci-dessus consiste à intercepter *des exceptions spécifiques* et à retourner une valeur significative dans le contexte de cette exception. Si vous modifiez la `tryReadAllText` fonction comme suit, `None` a plus de sens :

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

Au lieu de fonctionner comme un catch, cette fonction gère désormais correctement le cas lorsqu’un fichier est introuvable et assigne cette signification à un retour. Cette valeur de retour peut être mappée à ce cas d’erreur, sans ignorer d’informations contextuelles ou obliger les appelants à traiter un cas qui peut ne pas être pertinent à ce stade du code.

Les types tels que `Result<'Success, 'Error>` sont appropriés pour les opérations de base où ils ne sont pas imbriqués, et les types facultatifs F # sont *parfaits* pour représenter les cas où un élément peut retourner *une valeur* ou rien. Toutefois, ils ne remplacent pas les exceptions et ne doivent pas être utilisés dans une tentative de remplacement des exceptions. Au lieu de cela, elles doivent être appliquées judicieusement pour répondre à des aspects spécifiques de la stratégie de gestion des exceptions et des erreurs de manière ciblée.

## <a name="partial-application-and-point-free-programming"></a>Programmation partielle d’application et de point-Free

F # prend en charge l’application partielle et, par conséquent, les différentes façons de programmer dans un style point-to-free. Cela peut être bénéfique pour la réutilisation de code dans un module ou pour l’implémentation d’un événement, mais il ne s’agit pas d’un point à exposer publiquement. En général, la programmation sans point n’est pas un fait en soi et peut ajouter une barrière cognitive importante pour les personnes qui ne sont pas immergées dans le style.

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>N’utilisez pas d’application partielle et de curryfication dans les API publiques

Avec peu d’exceptions, l’utilisation d’une application partielle dans des API publiques peut prêter à confusion pour les consommateurs. En général, `let` les valeurs liées au code F # sont des **valeurs**, et non des valeurs de **fonction**. La combinaison de valeurs et de valeurs de fonction peut entraîner l’enregistrement d’un petit nombre de lignes de code dans Exchange pour une surcharge cognitive, en particulier si elle est associée à des opérateurs tels que `>>` pour composer des fonctions.

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>Tenez compte des implications des outils pour la programmation sans point

Les fonctions curryfiée n’étiquettent pas leurs arguments. Cela a des implications en matière d’outils. Considérez les deux fonctions suivantes :

```fsharp
let func name age =
    printfn $"My name is {name} and I am %d{age} years old!"

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

Les deux sont des fonctions valides, mais `funcWithApplication` est une fonction curryfiée. Lorsque vous pointez sur leurs types dans un éditeur, vous voyez ceci :

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

Sur le site d’appel, les info-bulles dans les outils, tels que Visual Studio, vous donnent la signature de type, mais étant donné qu’aucun nom n’est défini, les noms ne sont pas affichés. Les noms sont essentiels pour une bonne conception d’API, car ils aident les appelants à mieux comprendre la signification de l’API. L’utilisation de code sans point dans l’API publique peut compliquer la compréhension des appelants.

Si vous rencontrez du code de point-Free comme `funcWithApplication` qui est utilisable publiquement, il est recommandé d’effectuer une expansion η complète afin que les outils puissent récupérer des noms significatifs pour les arguments.

En outre, le débogage du code de point-Free peut être difficile, voire impossible. Les outils de débogage s’appuient sur des valeurs liées à des noms (par exemple, des `let` liaisons) afin que vous puissiez inspecter les valeurs intermédiaires au milieu de l’exécution. Lorsque votre code n’a pas de valeurs à inspecter, il n’y a rien à déboguer. À l’avenir, les outils de débogage peuvent évoluer pour synthétiser ces valeurs en fonction des chemins d’accès exécutés précédemment, mais il n’est pas judicieux de couvrir vos résultats sur les fonctionnalités de débogage *potentielles* .

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>Envisagez l’application partielle comme une technique pour réduire la réutilisabilité interne

Contrairement au point précédent, l’application partielle est un outil formidable pour réduire la réutilisabilité dans une application ou les éléments internes plus approfondis d’une API. Il peut être utile pour les tests unitaires de l’implémentation d’API plus compliquées, où les réutilisations sont souvent difficiles à gérer. Par exemple, le code suivant montre comment vous pouvez accomplir ce que la plupart des frameworks factices vous procurent sans prendre de dépendance externe sur une telle infrastructure et avoir à apprendre une API de rôle associé.

Par exemple, considérez la topographie de solution suivante :

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
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

Le test unitaire `Transactions.doTransaction` dans `ImplementationLogic.Tests.fsproj` est simple :

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

L’application partielle `doTransaction` à un objet de contexte factice vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir à construire un contexte simulé à chaque fois :

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

Cette technique ne doit pas être appliquée universellement à votre code base, mais il s’agit d’un bon moyen de réduire la réutilisabilité pour les éléments internes complexes et les tests unitaires.

## <a name="access-control"></a>Contrôle d’accès

F # dispose de plusieurs options pour le [contrôle d’accès](../language-reference/access-control.md), héritées de ce qui est disponible dans le Runtime .net. Celles-ci ne sont pas uniquement utilisables pour les types. vous pouvez également les utiliser pour les fonctions.

* Préférez les non- `public` types et les membres jusqu’à ce que vous ayez besoin qu’ils soient consommables publiquement. Cela réduit également ce que les consommateurs couplent à.
* Efforcez-vous de conserver toutes les fonctionnalités d’assistance `private` .
* Envisagez l’utilisation de `[<AutoOpen>]` sur un module privé de fonctions d’assistance si elles deviennent nombreuses.

## <a name="type-inference-and-generics"></a>Inférence de type et génériques

L’inférence de type peut vous éviter de saisir un grand nombre de réutilisables. Et la généralisation automatique dans le compilateur F # peuvent vous aider à écrire du code plus générique sans pratiquement aucun effort supplémentaire de votre part. Toutefois, ces fonctionnalités ne sont pas universellement bonnes.

* Envisagez d’étiqueter les noms d’arguments avec des types explicites dans les API publiques et de ne pas compter sur l’inférence de type pour ce.

    Cela est dû au fait que **vous** devez contrôler la forme de votre API, et non le compilateur. Bien que le compilateur puisse faire un travail précis au niveau de l’inférence des types pour vous, il est possible de modifier la forme de votre API si les éléments internes sur lesquels elle repose ont des types modifiés. C’est peut-être ce que vous souhaitez, mais il résultera certainement d’une modification de l’API avec rupture que les consommateurs en aval devront ensuite traiter. Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, vous pouvez contrôler ces modifications avec rupture. En termes de DDD, cela peut être considéré comme une couche de lutte contre la corruption.

* Envisagez de donner un nom explicite à vos arguments génériques.

    À moins que vous n’écriviez du code véritablement générique qui n’est pas spécifique à un domaine particulier, un nom explicite peut aider d’autres programmeurs à comprendre le domaine dans lequel ils travaillent. Par exemple, un paramètre de type nommé `'Document` dans le contexte de l’interaction avec une base de données de documents rend plus clair que les types de documents génériques peuvent être acceptés par la fonction ou le membre que vous utilisez.

* Envisagez de nommer des paramètres de type générique avec casse Pascal.

    C’est le moyen général de faire des choses dans .NET. il est donc recommandé d’utiliser casse Pascal au lieu de snake_case ou la casse mixte.

Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes qui découvrent F # ou un code base volumineux. L’utilisation de composants génériques implique une surcharge cognitive. En outre, si des fonctions automatiquement généralisées ne sont pas utilisées avec des types d’entrée différents (qui peuvent être utilisés en tant que tels), il n’y a pas d’avantages réels pour eux, à ce moment précis. Envisagez toujours d’être générique pour le code que vous écrivez.

## <a name="performance"></a>Performances

### <a name="consider-structs-for-small-types-with-high-allocation-rates"></a>Envisagez les structs pour les petits types avec des taux d’allocation élevés

L’utilisation de structs (également appelés types valeur) peut souvent aboutir à des performances supérieures pour du code, car il évite généralement d’allouer des objets. Toutefois, les structs ne sont pas toujours un bouton « Go plus rapide » : si la taille des données d’un struct dépasse 16 octets, la copie des données peut souvent entraîner une réduction du temps processeur par rapport à l’utilisation d’un type référence.

Pour déterminer si vous devez utiliser un struct, tenez compte des conditions suivantes :

- Si la taille de vos données est inférieure ou égal à 16 octets.
- Si de nombreuses instances de ces types sont susceptibles de résider en mémoire dans un programme en cours d’exécution.

Si la première condition s’applique, vous devez généralement utiliser un struct. Si les deux s’appliquent, vous devez presque toujours utiliser un struct. Il peut y avoir des cas où les conditions précédentes s’appliquent, mais l’utilisation d’un struct n’est pas mieux ou pire que l’utilisation d’un type référence, mais elles sont susceptibles d’être rares. Toutefois, il est important de toujours mesurer le moment où les modifications sont apportées, et non pas en fonction de l’hypothèse ou de l’intuition.

#### <a name="consider-struct-tuples-when-grouping-small-value-types-with-high-allocation-rates"></a>Envisagez les tuples de struct lors du regroupement de petits types de valeur avec des taux d’allocation élevés

Considérez les deux fonctions suivantes :

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

Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que la `runWithStructTuple` fonction qui utilise des tuples de struct s’exécute 40% plus rapidement et n’alloue pas de mémoire.

Toutefois, ces résultats ne seront pas toujours le cas dans votre propre code. Si vous marquez une fonction en tant que `inline` , le code qui utilise des tuples de référence peut obtenir des optimisations supplémentaires, ou le code qui allouerait peut simplement être optimisé. Vous devez toujours mesurer les résultats chaque fois que les performances le concernent et ne jamais travailler en fonction de l’hypothèse ou de l’intuition.

#### <a name="consider-struct-records-when-the-type-is-small-and-has-high-allocation-rates"></a>Envisagez les enregistrements de struct lorsque le type est petit et a des taux d’allocation élevés

La règle de curseur de défilement décrite précédemment contient également des [types d’enregistrement F #](../language-reference/records.md). Tenez compte des types de données et des fonctions suivants qui les traitent :

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

Cela est similaire au code de tuple précédent, mais cette fois-ci, l’exemple utilise des enregistrements et une fonction interne Inline.

Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que `processStructPoint` s’exécute presque 60% plus rapidement et n’alloue rien sur le tas managé.

#### <a name="consider-struct-discriminated-unions-when-the-data-type-is-small-with-high-allocation-rates"></a>Envisagez les unions discriminées struct lorsque le type de données est petit avec des taux d’allocation élevés

Les observations précédentes sur les performances avec les tuples de struct et les enregistrements contiennent également des [unions discriminées F #](../language-reference/discriminated-unions.md). Considérez le code suivant :

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

Il est courant de définir des unions discriminées à cas unique comme celles-ci pour la modélisation de domaine. Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que `structReverseName` s’exécute environ 25% plus rapide que `reverseName` pour les petites chaînes. Pour les chaînes volumineuses, elles sont toutes deux identiques. Ainsi, dans ce cas, il est toujours préférable d’utiliser un struct. Comme mentionné précédemment, il est toujours possible de mesurer et de ne pas utiliser les hypothèses ou l’intuition.

Bien que l’exemple précédent indiquait qu’une union discriminée de struct produisait de meilleures performances, il est courant d’avoir des unions discriminées plus importantes lors de la modélisation d’un domaine. Les types de données plus importants, tels que, peuvent ne pas s’exécuter également s’ils sont des structs en fonction des opérations qui leur sont associées, car une copie supplémentaire peut être impliquée.

### <a name="functional-programming-and-mutation"></a>Programmation et mutation fonctionnelles

Les valeurs F # sont immuables par défaut, ce qui vous permet d’éviter certaines classes de bogues (en particulier celles qui impliquent la concurrence et le parallélisme). Toutefois, dans certains cas, pour obtenir une efficacité optimale (voire raisonnable) du temps d’exécution ou des allocations de mémoire, il est préférable d’implémenter une étendue de travail à l’aide d’une mutation sur place de l’État. Cela est possible dans une base d’abonnement avec F # avec le `mutable` mot clé.

L’utilisation de `mutable` en F # peut avoir des chances d’avoir une pureté fonctionnelle. Cela est compréhensible, mais la pureté fonctionnelle partout peut être à la même des objectifs de performances. Un compromis consiste à encapsuler la mutation de manière à ce que les appelants n’aient pas à se soucier de ce qui se passe lorsqu’ils appellent une fonction. Cela vous permet d’écrire une interface fonctionnelle sur une implémentation basée sur une mutation pour le code critique pour les performances.

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>Encapsuler le code mutable dans des interfaces immuables

Avec la transparence référentielle comme objectif, il est essentiel d’écrire du code qui n’expose pas le Underbelly mutable des fonctions critiques pour les performances. Par exemple, le code suivant implémente la `Array.contains` fonction dans la bibliothèque principale F # :

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

L’appel de cette fonction plusieurs fois ne change pas le tableau sous-jacent, pas plus qu’il ne nécessite que vous mainteniez un État mutable dans l’utilisation de celui-ci. Elle est transparente de manière référentielle, même si presque chaque ligne de code qu’elle contient utilise la mutation.

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>Envisagez d’encapsuler des données mutables dans des classes

L’exemple précédent utilisait une fonction unique pour encapsuler des opérations à l’aide de données mutables. Cela n’est pas toujours suffisant pour les ensembles de données plus complexes. Prenez en compte les ensembles de fonctions suivants :

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

Ce code est performant, mais il expose la structure de données basée sur la mutation que les appelants sont responsables de la gestion. Cela peut être encapsulé à l’intérieur d’une classe sans membres sous-jacents qui peuvent changer :

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

`Closure1Table` encapsule la structure de données basée sur la mutation sous-jacente, ce qui ne force pas les appelants à gérer la structure de données sous-jacente. Les classes sont un moyen puissant d’encapsuler des données et des routines basées sur une mutation sans exposer les détails aux appelants.

#### <a name="prefer-let-mutable-to-reference-cells"></a>Préférer les `let mutable` cellules de référence

Les cellules de référence sont un moyen de représenter la référence à une valeur plutôt que la valeur elle-même. Bien qu’elles puissent être utilisées pour le code critique pour les performances, elles ne sont pas recommandées. Prenons l’exemple suivant :

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

L’utilisation d’une cellule de référence « pollue » tout le code suivant avec un déréférencement et une nouvelle référence aux données sous-jacentes. Au lieu de cela, tenez compte des `let mutable` éléments suivants :

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Hormis le point de mutation unique au milieu de l’expression lambda, tout autre code qui touche `acc` peut le faire d’une manière qui ne diffère pas de l’utilisation d’une `let` valeur immuable à liaison normale. Cela facilitera la modification au fil du temps.

## <a name="object-programming"></a>Programmation d’objets

F # offre une prise en charge complète des objets et des concepts orientés objet. Bien que de nombreux concepts OO soient puissants et utiles, ils ne sont pas tous idéaux pour être utilisés. Les listes suivantes offrent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.

**Envisagez d’utiliser ces fonctionnalités dans de nombreux cas :**

* Notation par points ( `x.Length` )
* Membres d’instance
* Constructeurs implicites
* Membres static
* Notation de l’indexeur ( `arr.[x]` )
* Arguments nommés et facultatifs
* Interfaces et implémentations d’interface

**N’atteignez pas ces fonctionnalités en premier, mais appliquez-les judicieusement lorsqu’ils sont pratiques pour résoudre un problème :**

* Surcharge de méthode
* Données mutables encapsulées
* Opérateurs sur les types
* Propriétés automatiques
* Implémentation `IDisposable` et `IEnumerable`
* Extensions de type
* Événements
* Structures
* Délégués
* Énumérations

**Évitez généralement ces fonctionnalités, sauf si vous devez les utiliser :**

* Hiérarchies de types basées sur l’héritage et héritage d’implémentation
* Valeurs NULL et `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>Préférer la composition à l’héritage

La [composition sur l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome à long terme auquel un bon code F # peut adhérer. Le principe fondamental est que vous ne devez pas exposer une classe de base et forcer les appelants à hériter de cette classe de base pour obtenir des fonctionnalités.

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>Utiliser des expressions d’objet pour implémenter des interfaces si vous n’avez pas besoin d’une classe

Les [expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, en liant l’interface implémentée à une valeur sans avoir à le faire à l’intérieur d’une classe. Cela est pratique, surtout si vous avez _uniquement_ besoin d’implémenter l’interface et que vous n’avez pas besoin d’une classe complète.

Par exemple, voici le code qui est exécuté dans [Ionide](https://ionide.io/) pour fournir une action de correction de code si vous avez ajouté un symbole pour lequel vous n’avez pas d' `open` instruction :

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

Étant donné qu’il n’est pas nécessaire d’utiliser une classe lors de l’interaction avec l’API Visual Studio Code, les expressions d’objet constituent un outil idéal pour cela. Elles sont également utiles pour les tests unitaires, lorsque vous souhaitez insérer une interface avec des routines de test de manière ad hoc.

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>Considérer les abréviations de type pour raccourcir les signatures

Les [abréviations de type](../language-reference/type-abbreviations.md) sont un moyen pratique d’assigner une étiquette à un autre type, tel qu’une signature de fonction ou un type plus complexe. Par exemple, l’alias suivant affecte une étiquette à ce qui est nécessaire pour définir un calcul avec [CNTK](/cognitive-toolkit/), une bibliothèque d’apprentissage approfondi :

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

Le `Computation` nom est un moyen pratique de désigner une fonction qui correspond à la signature qu’elle utilise comme alias. L’utilisation d’abréviations de type comme celle-ci est pratique et permet d’obtenir un code plus concis.

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>Évitez d’utiliser des abréviations de type pour représenter votre domaine

Bien que les abréviations de type soient pratiques pour donner un nom aux signatures de fonction, elles peuvent prêter à confusion lors de l’abréviation d’autres types. Tenez compte de cette abréviation :

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

Cela peut prêter à confusion de plusieurs façons :

* `BufferSize` n’est pas une abstraction ; Il s’agit simplement d’un autre nom pour un entier.
* Si `BufferSize` est exposé dans une API publique, il peut facilement être interprété de manière erronée pour signifier plus que simplement `int` . En règle générale, les types de domaine ont plusieurs attributs et ne sont pas des types primitifs comme `int` . Cette abréviation ne respecte pas cette hypothèse.
* La casse de `BufferSize` (casse Pascal) implique que ce type contient plus de données.
* Cet alias n’offre pas de clarté accrue par rapport à la fourniture d’un argument nommé à une fonction.
* L’abréviation ne se manifeste pas dans le langage intermédiaire compilé. Il s’agit simplement d’un entier et cet alias est une construction au moment de la compilation.

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

En résumé, le piège avec les abréviations de type est qu’il ne s’agit **pas** d’abstractions sur les types qu’ils abrégént. Dans l’exemple précédent, `BufferSize` est juste un en `int` coulisses, sans données supplémentaires, ni aucun avantage du système de type en plus de ce qui existe `int` déjà.

Une autre approche de l’utilisation d’abréviations de type pour représenter un domaine consiste à utiliser des unions discriminées à cas unique. L’exemple précédent peut être modélisé comme suit :

```fsharp
type BufferSize = BufferSize of int
```

Si vous écrivez du code qui fonctionne en termes de `BufferSize` et de sa valeur sous-jacente, vous devez construire un entier au lieu de passer un entier arbitraire :

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

Cela réduit la probabilité de passer un entier arbitraire dans la fonction par erreur `send` , car l’appelant doit construire un `BufferSize` type pour encapsuler une valeur avant d’appeler la fonction.
