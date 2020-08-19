---
title: Indications de mise en forme du code F#
description: 'Découvrez les instructions de mise en forme du code F #.'
ms.date: 11/04/2019
ms.openlocfilehash: fe8da6070e1c92bb5205e9cb408b8ac75372b061
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558307"
---
# <a name="f-code-formatting-guidelines"></a>Indications de mise en forme du code F#

Cet article fournit des instructions sur la façon de mettre en forme votre code afin que votre code F # soit :

* Plus lisible
* Conformément aux conventions appliquées par les outils de mise en forme dans Visual Studio et d’autres éditeurs
* Similaire à un autre code en ligne

Ces instructions sont basées sur [un guide exhaustif des conventions de mise en forme F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-fumier Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Règles générales pour la mise en retrait

F # utilise des espaces blancs significatifs par défaut. Les instructions suivantes sont destinées à vous aider à jongler avec les défis que cela peut imposer.

### <a name="using-spaces"></a>Utilisation des espaces

Lorsque la mise en retrait est requise, vous devez utiliser des espaces, et non des tabulations. Au moins un espace est requis. Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait sont typiques.

**Nous vous recommandons quatre espaces par retrait.**

Ceci dit, la mise en retrait des programmes est une question subjective. Les variations sont OK, mais la première règle que vous devez suivre est la *cohérence de la mise en retrait*. Choisissez un style de mise en retrait généralement accepté et utilisez-le systématiquement tout au long de votre code base.

## <a name="formatting-white-space"></a>Mise en forme des espaces blancs

F # est sensible à l’espace blanc. Bien que la plupart des sémantiques de l’espace blanc soient couvertes par une mise en retrait appropriée, il y a d’autres éléments à prendre en compte.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Mise en forme des opérateurs dans les expressions arithmétiques

Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :

```fsharp
let subtractThenAdd x = x - 1 + 3
```

`-`Les opérateurs unaires doivent toujours être suivis immédiatement de la valeur qu’ils annulent :

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

L’ajout d’un espace blanc après l' `-` opérateur peut entraîner des confusions pour d’autres.

En résumé, il est important de toujours :

* Entourer les opérateurs binaires avec un espace blanc
* Ne jamais avoir d’espace blanc de fin après un opérateur unaire

L’indication de l’opérateur arithmétique binaire est particulièrement importante. L’échec de l’entourage d’un `-` opérateur binaire, lorsqu’il est associé à certains choix de mise en forme, peut entraîner son interprétation comme unaire `-` .

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Entourer une définition d’opérateur personnalisée avec un espace blanc

Utilisez toujours des espaces blancs pour entourer une définition d’opérateur :

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pour tout opérateur personnalisé qui commence par `*` et qui contient plusieurs caractères, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté du compilateur. Pour cette raison, nous vous recommandons d’entourer simplement les définitions de tous les opérateurs avec un seul espace blanc.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Placer les flèches de paramètre de fonction avec un espace blanc

Lors de la définition de la signature d’une fonction, utilisez un espace blanc autour du `->` symbole :

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Entourer les arguments de fonction avec un espace blanc

Lors de la définition d’une fonction, utilisez un espace blanc autour de chaque argument.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a>Placer des paramètres sur une nouvelle ligne pour les définitions longues

Si vous avez une définition de fonction très longue, placez les paramètres sur de nouvelles lignes et mettez-les en retrait pour qu’ils correspondent au niveau de mise en retrait du paramètre suivant.

```fsharp
module M =
    let LongFunctionWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        =
        // ... the body of the method follows
```

Cela s’applique également aux membres, constructeurs et paramètres à l’aide de tuples :

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method

type TC(aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

Si les paramètres sont currified ou s’il existe une annotation de type de retour explicite, il est préférable de placer le `=` caractère sur une nouvelle ligne :

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                            : AReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                =
        // ... the body of the method
```

Il s’agit d’un moyen d’éviter des lignes trop longues (dans le cas où le type de retour peut avoir un nom long) et d’avoir moins de dommages lors de l’ajout de paramètres.

### <a name="type-annotations"></a>Annotations de type

#### <a name="right-pad-function-argument-type-annotations"></a>Annotations de type d’argument de fonction de remplissage à droite

Quand vous définissez des arguments avec des annotations de type, utilisez un espace blanc après le `:` symbole :

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Entourer les annotations de type de retour avec des espaces blancs

Dans une fonction de liaison ou une annotation de type valeur (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le `:` symbole :

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Mise en forme des lignes vides

* Séparez les définitions de fonction et de classe de niveau supérieur par deux lignes vides.
* Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne vide.
* Des lignes vides supplémentaires peuvent être utilisées (avec modération) pour séparer les groupes de fonctions associées. Des lignes vides peuvent être omises entre une série de lignes associées (par exemple, un ensemble d’implémentations factices).
* Utilisez des lignes vides dans les fonctions, avec modération, pour indiquer les sections logiques.

## <a name="formatting-comments"></a>Mise en forme des commentaires

Préférez généralement plusieurs commentaires à deux barres obliques par rapport aux commentaires de bloc de type ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Les commentaires insérés doivent mettre en majuscule la première lettre.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Conventions d'attribution d'un nom

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Utilisez la casse mixte pour les valeurs et les fonctions liées à la classe, à l’expression et liées aux modèles

Il est courant et accepté le style F # pour utiliser la casse mixte pour tous les noms liés en tant que variables locales ou dans les définitions de fonctions et les correspondances de modèle.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Les fonctions liées localement dans les classes doivent également utiliser la casse mixte.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Utiliser la casse mixte pour les fonctions publiques liées aux modules

Quand une fonction liée à un module fait partie d’une API publique, elle doit utiliser la casse mixte :

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Utilisez la casse mixte pour les valeurs et les fonctions liées aux modules internes et privés

Utilisez la casse mixte pour les valeurs à liaison de module privées, y compris les éléments suivants :

* Fonctions ad hoc dans les scripts

* Valeurs constituant l’implémentation interne d’un module ou d’un type

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Utiliser la casse mixte pour les paramètres

Tous les paramètres doivent utiliser la casse mixte conformément aux conventions d’affectation de noms .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Utiliser casse Pascal pour les modules

Tous les modules (de niveau supérieur, interne, privé, imbriqué) doivent utiliser casse Pascal.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Utiliser casse Pascal pour les déclarations de type, les membres et les étiquettes

Les classes, les interfaces, les structures, les énumérations, les délégués, les enregistrements et les unions discriminées doivent toutes être nommées avec casse Pascal. Les membres dans les types et les étiquettes pour les enregistrements et les unions discriminées doivent également utiliser casse Pascal.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Utiliser casse Pascal pour les constructions intrinsèques à .NET

Les espaces de noms, les exceptions, les événements et les projets/ `.dll` noms doivent également utiliser casse Pascal. Non seulement cela rend la consommation des autres langages .NET plus naturelle pour les consommateurs, mais elle est également cohérente avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.

### <a name="avoid-underscores-in-names"></a>Éviter les traits de soulignement dans les noms

Historiquement, certaines bibliothèques F # ont utilisé des traits de soulignement dans les noms. Toutefois, cela n’est plus largement accepté, en partie parce qu’il est en conflit avec les conventions de nommage .NET. Cela dit, certains programmeurs F # utilisent des traits de soulignement très largement, en partie pour des raisons historiques, et la tolérance et le respect sont importants. Toutefois, n’oubliez pas que le style est souvent utilisé par d’autres personnes qui ont le choix de l’utiliser ou non.

Une exception concerne l’interopérabilité avec les composants natifs, où les traits de soulignement sont courants.

### <a name="use-standard-f-operators"></a>Utiliser les opérateurs F # standard

Les opérateurs suivants sont définis dans la bibliothèque standard F # et doivent être utilisés au lieu de définir des équivalents. L’utilisation de ces opérateurs est recommandée, car elle tend à rendre le code plus lisible et idiomatique. Les développeurs disposant d’un arrière-plan dans OCaml ou d’autres langages de programmation fonctionnelle peuvent être habitués à différents idiomes. La liste suivante récapitule les opérateurs F # recommandés.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Utilisez la syntaxe de préfixe pour les génériques ( `Foo<T>` ) de préférence à la syntaxe postfix ( `T Foo` )

F # hérite à la fois du style postfix ML de l’attribution d’un nom aux types génériques (par exemple,), ainsi `int list` que du style .net du préfixe (par exemple, `list<int>` ). Préférer le style .NET, à l’exception de cinq types spécifiques :

1. Pour les listes F #, utilisez le formulaire de suffixe : `int list` plutôt que `list<int>` .
2. Pour les options F #, utilisez le formulaire de suffixe : `int option` plutôt que `option<int>` .
3. Pour les options de valeur F #, utilisez la forme postfixé : `int voption` plutôt que `voption<int>` .
4. Pour les tableaux F #, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>` .
5. Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>` .

Pour tous les autres types, utilisez le formulaire de préfixe.

## <a name="formatting-tuples"></a>Mise en forme des tuples

Une instanciation de tuple doit être placée entre parenthèses et les virgules de délimitation doivent être suivies d’un seul espace, par exemple : `(1, 2)` , `(x, y, z)` .

Il est généralement admis d’omettre les parenthèses dans les critères spéciaux des tuples :

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Il est également généralement admis à omettre les parenthèses si le tuple est la valeur de retour d’une fonction :

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

En résumé, préférez les instanciations de tuple entre parenthèses, mais lors de l’utilisation de tuples pour les critères spéciaux ou une valeur de retour, il est considéré comme correct pour éviter les parenthèses.

## <a name="formatting-discriminated-union-declarations"></a>Mise en forme des déclarations d’union discriminée

Mise en retrait `|` dans la définition de type par quatre espaces :

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Mise en forme des unions discriminées

Les unions discriminées instanciées qui sont fractionnées sur plusieurs lignes doivent fournir aux données contenues une nouvelle étendue avec mise en retrait :

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

La parenthèse fermante peut également se trouver sur une nouvelle ligne :

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Mise en forme des déclarations d’enregistrement

Mettre en retrait `{` dans la définition de type par quatre espaces et démarrer la liste de champs sur la même ligne :

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

Il est préférable de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne si vous déclarez des implémentations d’interface ou des membres sur l’enregistrement :

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Mise en forme des enregistrements

Les enregistrements courts peuvent être écrits en une seule ligne :

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Les enregistrements qui sont plus longs doivent utiliser de nouvelles lignes pour les étiquettes :

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Le fait de placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabulé sur une étendue et le jeton de fermeture sur une nouvelle ligne sont préférables si vous êtes :

* Déplacement d’enregistrements dans du code avec différentes étendues de mise en retrait
* Les rediriger dans une fonction

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

Les mêmes règles s’appliquent aux éléments de liste et de tableau.

## <a name="formatting-copy-and-update-record-expressions"></a>Mise en forme des expressions d’enregistrement de copie et de mise à jour

Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, donc des instructions similaires s’appliquent.

Les expressions courtes peuvent tenir sur une seule ligne :

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Les expressions plus longues doivent utiliser de nouvelles lignes :

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

Comme avec les conseils d’enregistrement, vous souhaiterez peut-être dédier des lignes distinctes pour les accolades et mettre en retrait une étendue à droite avec l’expression. Dans certains cas spéciaux, tels que l’encapsulation d’une valeur avec un facultatif sans parenthèses, vous devrez peut-être conserver une accolade sur une ligne :

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>Mise en forme des listes et des tableaux

Écrire `x :: l` avec des espaces autour de l' `::` opérateur ( `::` est un opérateur infixe, par conséquent entouré d’espaces).

La liste et les tableaux déclarés sur une seule ligne doivent avoir un espace après le crochet ouvrant et avant le crochet fermant :

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Utilisez toujours au moins un espace entre deux opérateurs similaires à des accolades. Par exemple, laissez un espace entre un `[` et un `{` .

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

La même règle s’applique pour les listes ou les tableaux de tuples.

Les listes et les tableaux répartis sur plusieurs lignes suivent une règle similaire, à l’instar des enregistrements :

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

Et comme avec les enregistrements, la déclaration de l’ouverture et des crochets fermants sur leur propre ligne permet de faciliter le déplacement du code et de rediriger les fonctions vers les fonctions.

Lors de la génération de tableaux et de listes par programmation, préférez `->` `do ... yield` quand une valeur est toujours générée :

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

Les versions antérieures du langage F # nécessitaient `yield` de spécifier dans des situations où les données peuvent être générées de manière conditionnelle, ou il peut y avoir des expressions consécutives à évaluer. Préférez omettre ces `yield` Mots clés sauf si vous devez compiler avec une version plus ancienne du langage F # :

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

Dans certains cas, `do...yield` peut contribuer à la lisibilité. Ces cas, bien que subjectives, doivent être pris en considération.

## <a name="formatting-if-expressions"></a>Mettre en forme si des expressions

La mise en retrait des conditions dépend de la taille des expressions qui les composent. Si `cond` `e1` et `e2` sont courts, il vous suffit de les écrire sur une seule ligne :

```fsharp
if cond then e1 else e2
```

Si l’un ou l’autre `cond` `e1` `e2` est plus long, mais pas sur plusieurs lignes :

```fsharp
if cond
then e1
else e2
```

Si l’une des expressions est multiligne :

```fsharp
if cond then
    e1
else
    e2
```

Plusieurs conditions avec `elif` et `else` sont mises en retrait à la même portée que `if` :

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Constructions de critères spéciaux

Utilisez une `|` clause for each d’une correspondance sans mise en retrait. Si l’expression est brève, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Si l’expression à droite de la flèche de critères spéciaux est trop grande, déplacez-la vers la ligne suivante, en mettant en retrait une étape de la `match` / `|` .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Les critères spéciaux des fonctions anonymes, à partir de `function` , ne doivent généralement pas être mis en retrait trop loin. Par exemple, la mise en retrait d’une étendue comme suit est correcte :

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Les critères spéciaux dans les fonctions définies par `let` ou `let rec` doivent être mis en retrait à quatre espaces après le démarrage de `let` , même si le `function` mot clé est utilisé :

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nous vous déconseillons d’aligner les flèches.

## <a name="formatting-trywith-expressions"></a>Mise en forme des expressions try/with

Les critères spéciaux sur le type d’exception doivent être mis en retrait au même niveau que `with` .

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Mise en forme de l’application de paramètre de fonction

En général, la plupart des paramètres de fonction sont exécutés sur la même ligne.

Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, mettez-les en retrait d’une seule étendue.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

Les mêmes instructions s’appliquent aux expressions lambda comme arguments de fonction. Si le corps d’une expression lambda, le corps peut avoir une autre ligne, mise en retrait d’une étendue

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

Toutefois, si le corps d’une expression lambda est plus d’une ligne, envisagez de le factoriser dans une fonction distincte plutôt que d’avoir une construction multiligne appliquée comme argument unique à une fonction.

### <a name="formatting-infix-operators"></a>Mise en forme des opérateurs infixes

Séparez les opérateurs par des espaces. Les opérateurs et sont des exceptions évidentes à cette règle `!` `.` .

Les expressions infixes sont correctes pour la programmation sur la même colonne :

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Mise en forme des opérateurs de pipeline

`|>`Les opérateurs de pipeline doivent se trouver sous les expressions sur lesquelles ils opèrent.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Mise en forme des modules

Le code d’un module local doit être mis en retrait par rapport au module, mais le code d’un module de niveau supérieur ne doit pas être mis en retrait. Les éléments d’espace de noms n’ont pas besoin d’être mis en retrait.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Mise en forme des expressions et des interfaces d’objet

Les interfaces et les expressions d’objet doivent être alignées de la même façon avec `member` une mise en retrait après quatre espaces.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Mise en forme des espaces blancs dans les expressions

Évitez les espaces superflus dans les expressions F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Les arguments nommés ne doivent pas non plus avoir d’espace autour de `=` :

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Attributs de mise en forme

Les [attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>Mise en forme des attributs sur les paramètres

Les attributs peuvent également être placés sur des paramètres. Dans ce cas, placez ensuite sur la même ligne que le paramètre et avant le nom :

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Mise en forme de plusieurs attributs

Quand plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de façon à ce qu’il y ait un attribut par ligne :

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Lorsqu’ils sont appliqués à un paramètre, ils doivent se trouver sur la même ligne et être séparés par un `;` séparateur.

## <a name="formatting-literals"></a>Mise en forme des littéraux

Les [littéraux F #](../language-reference/literals.md) utilisant l' `Literal` attribut doivent placer l’attribut sur sa propre ligne et utiliser la dénomination casse Pascal :

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Évitez de placer l’attribut sur la même ligne que la valeur.
