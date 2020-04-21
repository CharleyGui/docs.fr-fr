---
title: Indications de mise en forme du code F#
description: Apprenez des lignes directrices pour le formatage du code F.
ms.date: 11/04/2019
ms.openlocfilehash: b8be70dd29a04e71614308164e541b99a1724305
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739554"
---
# <a name="f-code-formatting-guidelines"></a>Indications de mise en forme du code F#

Cet article offre des lignes directrices sur la façon de formater votre code afin que votre code F est :

* Plus lisible
* Conformément aux conventions appliquées par les outils de formatage dans Visual Studio et d’autres éditeurs
* Semblable à d’autres codes en ligne

Ces lignes directrices sont basées sur [un guide complet des conventions de formatage de F par](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Règles générales d’indentation

F ' utilise l’espace blanc significatif par défaut. Les lignes directrices suivantes visent à fournir des conseils sur la façon de jongler avec certains défis que cela peut imposer.

### <a name="using-spaces"></a>Utilisation d’espaces

Lorsque l’indentation est nécessaire, vous devez utiliser des espaces, pas des onglets. Au moins un espace est nécessaire. Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour l’indentation; deux, trois ou quatre espaces d’indentation à chaque niveau où l’indentation se produit est typique.

**Nous recommandons quatre espaces par indentation.**

Cela dit, l’indentation des programmes est une question subjective. Les variations sont OK, mais la première règle que vous devez suivre est *la cohérence de l’indentation*. Choisissez un style d’indentation généralement accepté et utilisez-le systématiquement dans votre base de code.

## <a name="formatting-white-space"></a>Formater l’espace blanc

L’espace blanc est sensible à l’espace blanc. Bien que la plupart des sémantiques de l’espace blanc sont couverts par l’indentation appropriée, il ya d’autres choses à considérer.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Formater les opérateurs dans les expressions arithmétiques

Utilisez toujours l’espace blanc autour des expressions arithmétiques binaires :

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Les `-` opérateurs non anistes doivent toujours être immédiatement suivis par la valeur qu’ils némentent :

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

L’ajout d’un `-` caractère d’espace blanc après l’opérateur peut conduire à la confusion pour les autres.

En résumé, il est important de toujours :

* Entourer les opérateurs binaires d’espace blanc
* N’ont jamais d’espace blanc de fuite après un opérateur unary

La ligne directrice de l’opérateur arithmétique binaire est particulièrement importante. Ne pas entourer un opérateur binaire, `-` lorsqu’il est combiné avec certains `-`choix de formatage, pourrait conduire à l’interpréter comme un unary .

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Entourez une définition d’opérateur personnalisé avec l’espace blanc

Utilisez toujours l’espace blanc pour entourer une définition de l’opérateur :

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pour tout opérateur personnalisé `*` qui commence par et qui a plus d’un caractère, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté compilateur. Pour cette raison, nous vous recommandons tout simplement d’entourer les définitions de tous les opérateurs avec un seul caractère d’espace blanc.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Entourer les flèches de paramètres de fonction avec l’espace blanc

Lors de la définition de la signature `->` d’une fonction, utilisez l’espace blanc autour du symbole :

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Entourer les arguments de fonction avec l’espace blanc

Lors de la définition d’une fonction, utilisez l’espace blanc autour de chaque argument.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>Placez les paramètres sur une nouvelle ligne pour les définitions de membres longs

Si vous avez une définition de membre très longue, placez les paramètres sur de nouvelles lignes et en indent une portée.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

Cela s’applique également aux constructeurs :

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Annotations de type

#### <a name="right-pad-function-argument-type-annotations"></a>Annotations de type d’argument de fonction de fonction de right-pad

Lors de la définition des arguments avec des `:` annotations de type, utilisez l’espace blanc après le symbole:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Annotations de type retour surround avec l’espace blanc

Dans une fonction let-lié ou une annotation de type de valeur (type `:` de retour dans le cas d’une fonction), utilisez l’espace blanc avant et après le symbole :

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Formater les lignes blanches

* Séparez les définitions de fonction et de classe de haut niveau avec deux lignes blanches.
* Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne blanche.
* Des lignes blanches supplémentaires peuvent être utilisées (avec parcimonie) pour séparer les groupes de fonctions connexes. Des lignes blanches peuvent être omises entre un groupe d’une ligne (par exemple, un ensemble d’implémentations factices).
* Utilisez des lignes blanches dans les fonctions, avec parcimonie, pour indiquer les sections logiques.

## <a name="formatting-comments"></a>Formater les commentaires

Généralement préfèrent plusieurs commentaires à double slash sur ml-style commentaires bloc.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Les commentaires inline devraient capitaliser la première lettre.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Conventions d'attribution d'un nom

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Utilisez camelCase pour les valeurs et les fonctions liées à la classe, liées à l’expression et liées aux motifs

Il est commun et accepté de style F ' d’utiliser camelCase pour tous les noms liés comme des variables locales ou dans les correspondances de modèle et les définitions de fonction.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Les fonctions liées localement dans les classes devraient également utiliser camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Utilisez camelCase pour des fonctions publiques liées au module

Lorsqu’une fonction reliée par un module fait partie d’une API publique, elle doit utiliser camelCase :

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Utilisez camelCase pour des valeurs et des fonctions internes et privées liées au module

Utilisez camelCase pour des valeurs privées liées au module, y compris les suivantes :

* Fonctions ad hoc dans les scripts

* Valeurs constituant la mise en œuvre interne d’un module ou d’un type

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Utilisez camelCase pour les paramètres

Tous les paramètres doivent utiliser camelCase conformément aux conventions de nommage .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Utilisez PascalCase pour les modules

Tous les modules (haut niveau, interne, privé, imbriqué) doivent utiliser PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Utilisez PascalCase pour les déclarations de type, les membres et les étiquettes

Les classes, les interfaces, les structs, les recensements, les délégués, les dossiers et les syndicats discriminés devraient tous être nommés avec PascalCase. Les membres des types et des étiquettes pour les documents et les syndicats discriminés devraient également utiliser PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Utilisez PascalCase pour des constructions intrinsèques à .NET

Les espaces de noms, les`.dll` exceptions, les événements et les noms de projets/noms devraient également utiliser PascalCase. Non seulement cela rend la consommation d’autres langues .NET se sentent plus naturels pour les consommateurs, il est également compatible avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.

### <a name="avoid-underscores-in-names"></a>Éviter les souligne dans les noms

Historiquement, certaines bibliothèques de F ont utilisé des soulignements dans les noms. Cependant, ce n’est plus largement accepté, en partie parce qu’il se heurte à des conventions de nommage .NET. Cela dit, certains programmeurs de F’emploient des souligne fortement, en partie pour des raisons historiques, et la tolérance et le respect sont importants. Cependant, sachez que le style est souvent détesté par d’autres qui ont le choix de l’utiliser ou non.

Une exception comprend l’interopération avec les composants autochtones, où les soulignements sont communs.

### <a name="use-standard-f-operators"></a>Utiliser des opérateurs FMD standard

Les opérateurs suivants sont définis dans la bibliothèque standard de F et doivent être utilisés au lieu de définir des équivalents. L’utilisation de ces opérateurs est recommandée car elle tend à rendre le code plus lisible et idiomatique. Les développeurs ayant une formation en OCaml ou dans d’autres langages de programmation fonctionnel peuvent être habitués à différents idiomes. La liste suivante résume les opérateurs de FMD recommandés.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Utilisez la syntaxe préfixe pour les génériques (`Foo<T>`) de préférence à la syntaxe postfixe (`T Foo`)

F ' hérite à la fois du style postfix ML de nommer les types génériques (par exemple, `int list`) ainsi que le style préfixe .NET (par exemple, `list<int>`). Préférez le style .NET, à l’exception de cinq types spécifiques:

1. Pour les listes de F, `int list` utilisez `list<int>`le formulaire postfix : plutôt que .
2. Pour les options F, utilisez `int option` le `option<int>`formulaire postfixe : plutôt que .
3. Pour les options de valeur F, `int voption` utilisez `voption<int>`le formulaire postfix : plutôt que .
4. Pour les tableaux de F, utilisez `int[]` le `int array` `array<int>`nom syntaxique plutôt que ou .
5. Pour les cellules `int ref` de `ref<int>` `Ref<int>`référence, utilisez plutôt que ou .

Pour tous les autres types, utilisez le formulaire de préfixe.

## <a name="formatting-tuples"></a>Formatage tuples

Une instantanéie de tuple devrait être parenthèse, et les virgules délimitantes à `(1, 2)`l’intérieur devraient être suivies d’un seul espace, par exemple: , `(x, y, z)`.

Il est communément admis d’omettre les parenthèses dans l’appariement des modèles de tuples :

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Il est également communément admis d’omettre les parenthèses si le tuple est la valeur de retour d’une fonction :

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

En résumé, préférez les instantanéiations de tuple entre parenthèses, mais lorsque vous utilisez des tuples pour l’appariement des motifs ou une valeur de retour, il est considéré comme très bien d’éviter les parenthèses.

## <a name="formatting-discriminated-union-declarations"></a>Formater les déclarations syndicales discriminatoires

Définition `|` de type indent par quatre espaces :

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

## <a name="formatting-discriminated-unions"></a>Formater les syndicats discriminés

Les unions discriminées instantanées qui se divisent entre plusieurs lignes devraient donner aux données contenues une nouvelle portée avec l’indentation :

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

La parenthèse de clôture peut également être sur une nouvelle ligne :

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formater les déclarations d’enregistrement

Indent `{` dans la définition de type par quatre espaces et commencer la liste de champ sur la même ligne:

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

Placer le jeton d’ouverture sur une nouvelle ligne et le jeton de clôture sur une nouvelle ligne est préférable si vous déclarez les implémentations d’interface ou les membres sur le dossier:

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

## <a name="formatting-records"></a>Formatage des enregistrements

Les enregistrements courts peuvent être écrits en une seule ligne :

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Les enregistrements plus longs devraient utiliser de nouvelles lignes pour les étiquettes :

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabbed sur une portée, et le jeton de clôture sur une nouvelle ligne est préférable si vous êtes:

* Déplacer les enregistrements dans le code avec différentes portées d’indentation
* Les jeter dans une fonction

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

Les mêmes règles s’appliquent pour les éléments de liste et de tableau.

## <a name="formatting-copy-and-update-record-expressions"></a>Formater les expressions d’enregistrement de copie et de mise à jour

Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, de sorte que des lignes directrices similaires s’appliquent.

Les expressions courtes peuvent s’adapter sur une seule ligne :

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Les expressions plus longues devraient utiliser de nouvelles lignes :

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Et comme avec les conseils d’enregistrement, vous pouvez consacrer des lignes séparées pour les accolades et en retrait une portée à droite avec l’expression. Dans certains cas particuliers, comme l’emballage d’une valeur avec une option sans parenthèses, vous devrez peut-être garder une accolade sur une seule ligne :

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

## <a name="formatting-lists-and-arrays"></a>Classement des listes et des tableaux

Écrivez `x :: l` avec `::` des`::` espaces autour de l’opérateur (est un opérateur infix, donc entouré d’espaces).

Liste et tableaux déclarés sur une seule ligne doivent avoir un espace après le support d’ouverture et avant le support de clôture:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Utilisez toujours au moins un espace entre deux opérateurs distincts ressemblant à des accolades. Par exemple, laissez un `[` espace `{`entre un et un .

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

La même ligne directrice s’applique aux listes ou aux tableaux de tuples.

Les listes et les tableaux qui se divisent entre plusieurs lignes suivent une règle similaire comme le font les enregistrements :

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

Et comme avec les dossiers, déclarer les supports d’ouverture et de fermeture sur leur propre ligne rendra le code de déplacement autour et la tuyauterie dans les fonctions plus facile.

Lorsque vous généez des tableaux `->` `do ... yield` et des listes programmatiquement, préférez-vous lorsque une valeur est toujours générée :

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

Les anciennes versions de la `yield` langue F requises spécifiant dans les situations où les données peuvent être générées sous condition, ou il peut y avoir des expressions consécutives à évaluer. Préférez omettre `yield` ces mots clés à moins que vous ne devez compiler avec une ancienne version linguistique de F :

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

Dans certains `do...yield` cas, peut aider à la lisibilité. Ces cas, bien que subjectifs, doivent être pris en considération.

## <a name="formatting-if-expressions"></a>Formatage si expressions

L’indentation des conditionnels dépend de la taille des expressions qui les composent. Si `cond` `e1` , `e2` et sont courts, il suffit de les écrire sur une ligne:

```fsharp
if cond then e1 else e2
```

Si `cond`l’un ou l’autre, `e1` ou `e2` sont plus longs, mais pas multi-lignes:

```fsharp
if cond
then e1
else e2
```

Si l’une des expressions sont multi-lignes:

```fsharp
if cond then
    e1
else
    e2
```

Plusieurs conditionnels avec `elif` et `else` sont en retrait `if`à la même portée que le :

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Constructions assorties de modèles

Utilisez `|` un pour chaque clause d’un match sans indentation. Si l’expression est courte, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.

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

Si l’expression à droite de la flèche assortie du motif est trop grande, `match` / `|`déplacez-la à la ligne suivante, en retrait à un pas de la .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

L’appariement des motifs des fonctions anonymes, à partir `function`de , ne devrait généralement pas s’en prendre trop loin. Par exemple, l’indentage d’une portée comme suit est très bien :

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

L’appariement des `let` `let rec` motifs dans les fonctions `let`définies `function` par ou doit être en retrait quatre espaces après le début de , même si le mot clé est utilisé:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nous ne recommandons pas d’aligner les flèches.

## <a name="formatting-trywith-expressions"></a>Formater l’essai/avec des expressions

L’appariement des modèles sur le type `with`d’exception doit être en retrait au même niveau que .

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

## <a name="formatting-function-parameter-application"></a>Application de paramètre de fonction de formatage

En général, la plupart des applications de paramètres de fonction se font sur la même ligne.

Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, en indent par une portée.

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

Les mêmes lignes directrices s’appliquent pour les expressions lambda que les arguments de fonction. Si le corps d’une expression lambda, le corps peut avoir une autre ligne, en retrait par une portée

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

Cependant, si le corps d’une expression lambda est plus d’une ligne, envisager de l’affacturage dans une fonction distincte plutôt que d’avoir une construction multi-lignes appliquée comme un seul argument à une fonction.

### <a name="formatting-infix-operators"></a>Formater les opérateurs d’infixe

Séparer les opérateurs par espaces. Les exceptions évidentes `!` à `.` cette règle sont les opérateurs et les opérateurs.

Les expressions Infix sont OK pour lineup sur la même colonne:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formater les exploitants de pipelines

Les `|>` exploitants de pipelines devraient passer sous les expressions sur laquelle ils opèrent.

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

### <a name="formatting-modules"></a>Modules de formatage

Le code d’un module local doit être en retrait par rapport au module, mais le code d’un module de haut niveau ne doit pas être en retrait. Les éléments de l’espace de nom n’ont pas besoin d’être en retrait.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formater les expressions et les interfaces d’objets

Les expressions et interfaces d’objet doivent `member` être alignées de la même manière avec l’en retrait après quatre espaces.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formater l’espace blanc dans les expressions

Évitez l’espace blanc extra-nant dans les expressions F.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Les arguments nommés ne `=`devraient pas non plus avoir d’espace autour de la :

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Formatage des attributs

[Les attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :

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

### <a name="formatting-attributes-on-parameters"></a>Formatage des attributs sur les paramètres

Les attributs peuvent également être des endroits sur les paramètres. Dans ce cas, placez-le alors sur la même ligne que le paramètre et avant le nom :

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formater plusieurs attributs

Lorsque plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de telle sorte qu’il y ait un attribut par ligne :

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Lorsqu’ils sont appliqués à un paramètre, `;` ils doivent être sur la même ligne et séparés par un séparateur.

## <a name="formatting-literals"></a>Formater les littérals

[Les littérals](../language-reference/literals.md) `Literal` de F à l’aide de l’attribut doivent placer l’attribut sur sa propre ligne et utiliser PascalCase nommant :

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Évitez de placer l’attribut sur la même ligne que la valeur.
