---
title: Indications de mise en forme du code F#
description: Découvrez des instructions pour la mise en forme F# code.
ms.date: 02/08/2019
ms.openlocfilehash: 8be5337d3f593c7e5a2f32cb7231cb7f759fb509
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833904"
---
# <a name="f-code-formatting-guidelines"></a>Indications de mise en forme du code F#

Cet article propose des conseils pour savoir comment mettre en forme votre code afin que votre F# code est :

* Généralement considérée comme plus lisibles
* Est conformément aux conventions appliquées par la mise en forme des outils dans Visual Studio et autres éditeurs
* Similaire à un autre code en ligne

Ces instructions sont basées sur [un guide complet sur F# Conventions de mise en forme](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Règles générales pour la mise en retrait

F#par défaut, utilise un espace blanc significatif. Les instructions suivantes sont destinées à fournir des conseils quant à jongler avec des défis que cela peut imposer.

### <a name="using-spaces"></a>L’utilisation des espaces

Lors de la mise en retrait est requise, vous devez utiliser des espaces, tabulations pas. Au moins un espace est requis. Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait est typique.

**Nous vous recommandons 4 espaces par mise en retrait.**

Ceci dit, la mise en retrait de programmes est très subjective. Variations sont OK, mais la première règle, vous devez suivre est *la cohérence de la mise en retrait*. Choisir un style généralement accepté de mise en retrait et l’utiliser systématiquement tout au long de votre base de code.

## <a name="formatting-white-space"></a>Mise en forme d’un espace blanc

F#est un espace blanc sensibles. Bien que la plupart des sémantiques à partir d’un espace blanc sont couverts par la mise en retrait appropriée, il existe quelques autres points à prendre en compte.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Mise en forme des opérateurs dans les expressions arithmétiques

Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Unaire `-` opérateurs doivent avoir toujours la valeur qu’ils sont la négation suivent immédiatement :

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Ajout d’un espace après le `-` opérateur peut prêter à confusion pour les autres.

En résumé, il est important de toujours :

* Entourez les opérateurs binaires par un espace blanc
* Espace blanc de fin n’ont jamais après un opérateur unaire

L’indication de l’opérateur arithmétique binaire est particulièrement importante. Échec de l’entourer d’un fichier binaire `-` opérateur, lorsqu’elles sont combinées avec certaines options de mise en forme, risque d’interpréter comme un opérateur unaire `-`.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Une définition d’opérateur personnalisé avec un espace blanc à effet surround

Utilisez toujours un espace blanc pour entourer une définition d’opérateur :

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pour n’importe quel opérateur personnalisé qui commence par `*` et qui a plusieurs caractères, vous devez ajouter un espace blanc au début de la définition afin d’éviter une ambiguïté du compilateur. Pour cette raison, nous recommandons que vous devez simplement placer les définitions de tous les opérateurs avec un seul caractère espace blanc.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Entourez les flèches de paramètre de fonction avec un espace blanc

Lorsque vous définissez la signature d’une fonction, utilisez un espace blanc autour du `->` symbole :

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Entourez les arguments de fonction avec un espace blanc

Lorsque vous définissez une fonction, utilisez un espace blanc autour de chaque argument.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="type-annotations"></a>Annotations de type

#### <a name="right-pad-function-argument-type-annotations"></a>Annotations de type d’argument droite (fonction)

Lorsque vous définissez les arguments avec des annotations de type, utilisez un espace blanc après le `:` symbole :

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Annotations de type de retour à effet surround par un espace blanc

Dans un lié aux permettent de fonction ou valeur annotation de type (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le `:` symbole :

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

* Distinct niveau supérieur (fonction) et classe les définitions avec deux lignes vides.
* Les définitions de méthode à l’intérieur d’une classe sont séparées par une ligne vierge.
* Lignes vierges supplémentaires peuvent servir (avec parcimonie) pour séparer les groupes de fonctions associées. Peuvent être omis des lignes vides entre un ensemble de commandes associées à une ligne (par exemple, un ensemble d’implémentations factices).
* Utiliser avec parcimonie, des lignes vides dans les fonctions, pour indiquer les sections logiques.

## <a name="formatting-comments"></a>Mise en forme de commentaires

Préférez généralement plusieurs commentaires double barre oblique sur les commentaires de bloc de style de ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Les commentaires incorporés doivent mettre en majuscule la première lettre.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Conventions d'attribution d'un nom

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Utilisent une casse mixte pour les fonctions et les valeurs de limite de classe, expression-liées aux et modèle

Il est courant et acceptés F# style à utiliser une casse mixte pour tous les noms liée en tant que variables locales ou dans les correspondances de modèles et de définitions de fonctions.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Fonctions liées à localement dans les classes doivent également utiliser une casse mixte.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Utilisent une casse mixte pour les fonctions publiques liées à un module

Quand une fonction liée au module fait partie d’une API publique, il doit utiliser une casse mixte :

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Utilisent une casse mixte pour les fonctions et les valeurs de module dépendant internes et privés

Utilisez la casse mixte pour les valeurs liée aux module privées, y compris les éléments suivants :

* Fonctions ad hoc dans les scripts

* Valeurs constituant l’implémentation interne d’un module ou un type

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Utilisez la casse mixte pour les paramètres

Tous les paramètres doivent utiliser une casse mixte conformément aux conventions d’affectation de noms .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Utiliser la casse Pascal pour les modules

Tous les modules (niveau supérieur, internes, privés, imbriquées) doivent utiliser la casse Pascal.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Utilisez la casse Pascal pour les déclarations de type, les membres et les étiquettes

Classes, interfaces, structures, énumérations, délégués, les enregistrements et les unions discriminées doivent être nommées avec la casse Pascal. Membres au sein des types et des étiquettes pour les enregistrements et les unions discriminées doivent également utiliser la casse Pascal.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Utilisez la casse Pascal pour les constructions intrinsèques pour .NET

Espaces de noms, exceptions, événements et projet /`.dll` noms doivent également utiliser la casse Pascal. Non seulement est-ce que la consommation à partir d’autres langages .NET sembler plus naturelle pour les consommateurs, il est également cohérente avec les conventions d’affectation de noms .NET que vous êtes susceptible de rencontrer.

### <a name="avoid-underscores-in-names"></a>Éviter les traits de soulignement dans les noms

Historiquement, certaines F# bibliothèques ont utilisé des traits de soulignement dans les noms. Toutefois, cela est n’est plus largement acceptée, en partie parce qu’il est en conflit avec les conventions d’affectation de noms .NET. Cela étant dit, certains F# les programmeurs utilisent des traits de soulignement fortement, en partie pour des raisons historiques, et la tolérance de panne et le respect important. Toutefois, n’oubliez pas que le style n’est souvent pas satisfaisant par d’autres personnes qui ont la possibilité d’utiliser.

Certaines exceptions inclut l’interopérabilité avec les composants natifs, où des traits de soulignement sont très courantes.

### <a name="use-standard-f-operators"></a>Standard d’utilisation F# opérateurs

Les opérateurs suivants sont définis dans le F# bibliothèque standard et doit être utilisé au lieu de définir des équivalents. L’utilisation de ces opérateurs est recommandée car elle a tendance à rendre le code plus lisible et idiomatique. Les développeurs avec un arrière-plan dans OCaml ou autre langage de programmation fonctionnel peut-être habitués à différents idiomes. La liste suivante résume l’architecture recommandée F# opérateurs.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Utiliser la syntaxe du préfixe pour les génériques (`Foo<T>`) plutôt que de la syntaxe de suffixe (`T Foo`)

F#hérite à la fois le style de ML suffixe de nommage des types génériques (par exemple, `int list`), ainsi que le préfixe de style .NET (par exemple, `list<int>`). Préférer le style de .NET, à l’exception des cinq types spécifiques :

1. Pour F# listes, utilisez la forme suffixée : `int list` plutôt que `list<int>`.
2. Pour F# Options, utilisez la forme suffixée : `int option` plutôt que `option<int>`.
3. Pour F# Options de valeur, utilisez la forme suffixée : `int voption` plutôt que `voption<int>`.
4. Pour F# tableaux, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>`.
5. Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>`.

Pour tous les autres types, utilisez la forme de préfixe.

## <a name="formatting-tuples"></a>Mise en forme de tuples

Une instanciation de tuple doit être entre parenthèses, et les virgules de délimitation dans doivent être suivies par un espace, par exemple : `(1, 2)`, `(x, y, z)`.

Il est généralement admis pour omettre les parenthèses dans les critères spéciaux de tuples :

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Il est également couramment acceptée pour omettre les parenthèses si le tuple est la valeur de retour d’une fonction :

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

En résumé, préférez les instanciations de tuple entre parenthèses, mais lorsque vous utilisez des tuples pour une valeur de retour ou de critères spéciaux, il est considéré comme acceptable d’éviter des parenthèses.

## <a name="formatting-discriminated-union-declarations"></a>Mise en forme discriminée des déclarations d’union

Mettre en retrait `|` dans la définition de type par des 4 espaces :

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

Instancié Unions discriminées qui réparties sur plusieurs lignes doit fournir des données qu’il contient une nouvelle étendue avec la mise en retrait :

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

La parenthèse fermante peut également être sur une nouvelle ligne :

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Mise en forme de déclarations d’enregistrement

Mettre en retrait `{` dans le type de définition par 4 espaces et démarrer la liste de champs sur la même ligne :

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

Il est préférable si vous déclarez des implémentations d’interface ou de membres sur l’enregistrement de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne :

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Mise en forme d’enregistrements

Enregistrements courts peuvent être écrite sur une seule ligne :

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Les enregistrements qui sont plus longs doivent utiliser les nouvelles lignes pour les étiquettes :

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Placer l’ouverture jeton sur une nouvelle ligne, le contenu avec onglets sur une étendue, et le jeton de fermeture sur une nouvelle ligne est préférable si vous êtes :

* Déplacer les enregistrements dans le code avec des étendues de mise en retrait différente
* Transférant dans une fonction

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

Les mêmes règles s’appliquent pour les éléments de liste et tableau.

## <a name="formatting-copy-and-update-record-expressions"></a>Expressions d’enregistrement de copie--mise à jour et de mise en forme

Une expression d’enregistrement de copie--mise à jour et est toujours un enregistrement, des instructions similaires s’appliquent donc pas.

Expressions courtes peuvent tenir sur une seule ligne :

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

De plus longues expressions doivent utiliser les nouvelles lignes :

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Et comme avec les conseils d’enregistrement, vous souhaiterez dédier des lignes distinctes pour les accolades et mettre en retrait d’une étendue à droite avec l’expression. Notez que dans certains cas spéciaux, tels que l’encapsulation d’une valeur avec une option sans parenthèses, vous devrez peut-être conserver une accolade sur une seule ligne :

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

Écrire `x :: l` avec des espaces autour de la `::` opérateur (`::` est un opérateur infixe, par conséquent, entouré d’espaces).

Liste et les tableaux déclarés sur une seule ligne doivent contenir un espace après le crochet ouvrant et avant le crochet fermant :

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Utilisez toujours au moins un espace entre les deux opérateurs distincts de type accolade. Par exemple, laissez un espace entre un `[` et un `{`.

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

La même règle s’applique pour les listes ou des tableaux de tuples.

Listes et des tableaux réparties sur plusieurs lignes suivent une règle similaire comme enregistrements :

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

Et comme avec les enregistrements, déclaration de l’ouverture et crochet fermant sur leur propre ligne facilitera migration autour du code et tuyauterie dans des fonctions.

## <a name="formatting-if-expressions"></a>Mise en forme if expressions

Mise en retrait des instructions conditionnelles varie selon les tailles des expressions qui les composent. Si `cond`, `e1` et `e2` sont courtes, il vous suffit de les écrire sur une seule ligne :

```fsharp
if cond then e1 else e2
```

Si `cond`, `e1` ou `e2` sont plus de temps, mais pas plusieurs lignes :

```fsharp
if cond
then e1
else e2
```

Si une des expressions est multiligne :

```fsharp
if cond then
    e1
else
    e2
```

Plusieurs instructions conditionnelles avec `elif` et `else` sont mises en retrait dans la même étendue en tant que le `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Constructions de correspondance de modèle

Utilisez un `|` pour chaque clause d’une correspondance avec aucune mise en retrait. Si l’expression est courte, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.

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

Si l’expression à droite de la flèche de critères spéciaux est trop volumineuse, déplacez-le vers la ligne suivante, mis en retrait d’une seule étape à partir de la `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Filtre de correspondance de fonctions anonymes, en commençant par `function`, doit généralement pas mettre en retrait trop loin. Par exemple, il est bien de mise en retrait d’une étendue comme suit :

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Critères spéciaux dans les fonctions définies par `let` ou `let rec` doit être mis en retrait 4 espaces après le démarrage de `let`, même si `function` mot clé est utilisé :

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nous vous déconseillons d’alignement des flèches.

## <a name="formatting-trywith-expressions"></a>Mise en forme try / with expressions

Critères spéciaux sur le type d’exception doit être mis en retrait au même niveau que `with`.

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

## <a name="formatting-function-parameter-application"></a>Mise en forme d’application de paramètre de fonction

En règle générale, la plupart des applications de paramètre de fonction sont effectuée sur la même ligne.

Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, mettre en retrait les par une étendue.

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

Les mêmes règles s’appliquent pour les expressions lambda en tant qu’arguments de fonction. Si le corps d’une expression lambda, le corps peut avoir une autre ligne, la mise en retrait par une étendue

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

Toutefois, si le corps d’une expression lambda est plusieurs lignes, envisagez factorisant dans une fonction distincte plutôt que d’avoir une construction multiligne appliquée en tant qu’un seul argument à une fonction.

### <a name="formatting-infix-operators"></a>Opérateurs infixes mise en forme

Opérateurs distincts par des espaces. Exceptions évident à cette règle sont les `!` et `.` opérateurs.

Expressions de correspondance des infixes sont OK pour l’alignement sur la même colonne :

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Mise en forme des opérateurs de pipeline

Pipeline `|>` opérateurs doivent figurer sous elles opèrent selon des expressions.

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

### <a name="formatting-modules"></a>Mise en forme de modules

Code dans un module local doit être mis en retrait par rapport au module, mais le code dans un module de niveau supérieur ne doit pas être mis en retrait. Les éléments Namespace n’ont pas à être mis en retrait.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Mise en forme d’expressions d’objet et des interfaces

Expressions d’objet et les interfaces doivent être alignées dans la même façon avec `member` en cours de mise en retrait après 4 espaces.

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

Éviter les espaces superflus dans F# expressions.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Arguments nommés doivent avoir également pas espace entourant le `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Attributs de mise en forme

[Attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :

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

### <a name="formatting-attributes-on-parameters"></a>Attributs sur les paramètres de mise en forme

Attributs peuvent également être des emplacements sur les paramètres. Placez dans ce cas, puis sur la même ligne que le paramètre et avant le nom :

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Plusieurs attributs de mise en forme

Lorsque plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés qu’il y ait un seul attribut par ligne :

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Lorsqu’il est appliqué à un paramètre, ils doivent se trouver sur la même ligne et séparés par un `;` séparateur.

## <a name="formatting-literals"></a>Mise en forme de littéraux

[F#littéraux](../language-reference/literals.md) à l’aide de la `Literal` attribut doit placer l’attribut sur sa propre ligne et utiliser la casse Pascal d’affectation de noms :

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Évitez de placer l’attribut sur la même ligne que la valeur.
