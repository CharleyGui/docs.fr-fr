---
title: Mise en forme en texte brut
description: 'Découvrez comment utiliser printf et d’autres mises en forme de texte brut dans des scripts et des applications F #.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063781"
---
# <a name="plain-text-formatting"></a>Mise en forme de texte brut

F # prend en charge la mise en forme du texte brut par type vérifié à l’aide de `printf` ,, `printfn` et des `sprintf` fonctions associées.
Par exemple :

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

donne la sortie

```fsharp
Hello world, 2 + 2 is 4
```

F # permet également aux valeurs structurées d’être mises en forme en texte brut.
Par exemple, considérez l’exemple suivant qui met en forme la sortie sous la forme d’un affichage de tuples de type matrice.

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

La mise en forme du texte brut structuré est activée lorsque vous utilisez le `%A` format dans les `printf` chaînes de mise en forme.
Il est également activé lors de la mise en forme de la sortie des valeurs dans F # Interactive, où la sortie contient des informations supplémentaires et peut également être personnalisée.
La mise en forme de texte brut est également observable par le biais de tous les appels à `x.ToString()` sur les valeurs d’Union et d’enregistrement F #, y compris celles qui se produisent implicitement dans le débogage, la journalisation et d’autres outils.

## <a name="checking-of-printf-format-strings"></a>Vérification des `printf` chaînes de format

Une erreur de compilation est signalée si une `printf` fonction de mise en forme est utilisée avec un argument qui ne correspond pas aux spécificateurs de format printf dans la chaîne de format.  Par exemple :

```fsharp
sprintf "Hello %s" (2+2)
```

donne la sortie

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

Techniquement parlant, lorsque `printf` vous utilisez et d’autres fonctions associées, une règle spéciale dans le compilateur F # vérifie le littéral de chaîne passé comme chaîne de format, ce qui garantit que les arguments suivants appliqués sont du type correct pour correspondre aux spécificateurs de format utilisés.

## <a name="format-specifiers-for-printf"></a>Spécificateurs de format pour`printf`

Les spécifications de format pour les `printf` formats sont des chaînes avec des `%` marqueurs qui indiquent le format. Les espaces réservés de format se composent de `%[flags][width][.precision][type]` là où le type est interprété comme suit :

| Spécificateur de format   | Type (s)        | Notes                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | bool      | Mise en forme en tant que `true` ou`false`                |
| `%s`               | string    | Mise en forme en tant que contenu sans séquence d’échappement         |
| `%c`               | char      | Mise en forme en tant que littéral de caractère  |
| `%d`, `%i`         | type entier de base | Formaté comme un entier décimal, signé si le type entier de base est signé |
| `%u`               | type entier de base | Mise en forme en tant qu’entier décimal non signé   |
| `%x`, `%X`         | type entier de base | Mise en forme en tant que nombre hexadécimal non signé (a-f ou A-F pour les chiffres hexadécimaux, respectivement)  |
|  `%o`              | type entier de base | Mise en forme en tant que nombre octal non signé |
| `%e`, `%E`         | type à virgule flottante de base | Mise en forme sous la forme d’une valeur signée, `[-]d.dddde[sign]ddd` où d est un chiffre décimal unique, dddd est un ou plusieurs chiffres décimaux, ddd est exactement trois chiffres décimaux, et signe est `+` ou`-` |
| `%f`               | type à virgule flottante de base | Mise en forme sous forme de valeur signée sous la forme `[-]dddd.dddd` , où `dddd` représente un ou plusieurs chiffres décimaux. Le nombre de chiffres avant la virgule décimale dépend de l'ampleur du nombre, et le nombre de chiffres après que la virgule décimale dépend de la précision demandée. |
| `%g`, `%G` | type à virgule flottante de base |  Mise en forme à l’aide de comme valeur signée imprimée `%f` ou `%e` formatée, selon la valeur la plus petite pour la valeur et la précision données. |
| `%M` | une `System.Decimal` valeur  |    Mis en forme à l’aide du `"G"` spécificateur de format pour`System.Decimal.ToString(format)` |
| `%O` | toute valeur  |   Mis en forme en effectuant un boxing de l’objet et en appelant sa `System.Object.ToString()` méthode |
| `%A` | toute valeur  |   Formaté à l’aide de la [mise en forme du texte brut structuré](plaintext-formatting.md) avec les paramètres de disposition par défaut |
| `%a` | toute valeur  |   Nécessite deux arguments : une fonction de mise en forme qui accepte un paramètre de contexte et la valeur, ainsi que la valeur particulière à imprimer. |
| `%t` | toute valeur  |   Nécessite un argument : une fonction de mise en forme qui accepte un paramètre de contexte qui génère ou retourne le texte approprié. |
| `%%` | (aucun)  |   Ne requiert aucun argument et imprime un signe de pourcentage simple :`%` |

Les types entiers de base sont `byte` ( `System.Byte` ), `sbyte` ( `System.SByte` ), `int16` ( `System.Int16` ), `uint16` ( `System.UInt16` ), `int32` ( `System.Int32` ), `uint32` ( `System.UInt32` ), `int64` ( `System.Int64` ), `uint64` ( `System.UInt64` ), `nativeint` ( `System.IntPtr` ) et `unativeint` ( `System.UIntPtr` ).
Les types à virgule flottante de base sont `float` ( `System.Double` ) et `float32` ( `System.Single` ).

La largeur facultative est un entier indiquant la largeur minimale du résultat. Par exemple, `%6d` imprime un entier, en le préfixant avec des espaces pour remplir au moins six caractères. Si width est `*` , un argument entier supplémentaire est utilisé pour spécifier la largeur correspondante.

Les indicateurs valides sont les suivants :

| Indicateur   | Effet        | Notes                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | Ajoutez des zéros à la place des espaces pour créer la largeur requise |    |
| `-` |  Aligner à gauche le résultat dans la largeur spécifiée |   |
| `+`  | Ajoutez un `+` caractère si le nombre est positif (pour correspondre à un `-` signe pour les négatifs) |   |
| espace | Ajoutez un espace supplémentaire si le nombre est positif (pour correspondre à un signe « - » pour les valeurs négatives) |

L' `#` indicateur printf n’est pas valide et une erreur de compilation est signalée s’il est utilisé.

Les valeurs sont mises en forme à l’aide de la culture dite indifférente. Les paramètres de culture ne sont pas pertinents pour `printf` la mise en forme, sauf lorsqu’ils affectent les résultats `%O` et la `%A` mise en forme. Pour plus d’informations, consultez [mise en forme du texte brut structuré](plaintext-formatting.md).

## <a name="a-formatting"></a>`%A`mise en forme

Le `%A` spécificateur de format est utilisé pour mettre en forme les valeurs de façon lisible par l’utilisateur, et peut également être utile pour signaler des informations de diagnostic.

### <a name="primitive-values"></a>Valeurs primitives

Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les valeurs numériques F # sont mises en forme avec leur suffixe et leur culture dite indifférente. Les valeurs à virgule flottante sont mises en forme à l’aide de 10 emplacements de précision à virgule flottante. Par exemple :

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

tiges

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

Lors de l’utilisation du `%A` spécificateur, les chaînes sont mises en forme à l’aide de guillemets. Les codes d’échappement ne sont pas ajoutés, mais les caractères bruts sont imprimés. Par exemple :

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

tiges

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a>Valeurs .NET

Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les objets non F # .net sont mis en forme à l’aide `x.ToString()` des paramètres par défaut de .net fournis par `System.Globalization.CultureInfo.CurrentCulture` et `System.Globalization.CultureInfo.CurrentUICulture` .  Par exemple :

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

tiges

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a>Valeurs structurées

Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, le retrait de bloc est utilisé pour les listes et les tuples F #. Cela est illustré dans l’exemple précédent.
La structure des tableaux est également utilisée, y compris les tableaux multidimensionnels.  Les tableaux unidimensionnels sont affichés avec la `[| ... |]` syntaxe. Par exemple :

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

tiges

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

La largeur d’impression par défaut est 80.  Cette largeur peut être personnalisée à l’aide d’une largeur d’impression dans le spécificateur de format. Par exemple :

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

tiges

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

Si vous spécifiez une largeur d’impression égale à 0, aucune largeur d’impression n’est utilisée. Une seule ligne de texte se produit, sauf lorsque les chaînes incorporées dans la sortie contiennent des sauts de ligne.  Par exemple

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

tiges

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

Une limite de profondeur de 4 est utilisée pour les `IEnumerable` valeurs Sequence (), qui sont affichées sous la forme `seq { ...}` . Une limite de profondeur de 100 est utilisée pour les valeurs de liste et de tableau.
Par exemple :

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

tiges

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

La mise en retrait de bloc est également utilisée pour la structure des valeurs d’enregistrement et d’Union publiques. Par exemple :

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

tiges

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

Si `%+A` est utilisé, la structure privée des enregistrements et des unions est également révélée à l’aide de la réflexion. Par exemple

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

tiges

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a>Valeurs volumineuses, cycliques ou profondément imbriquées

Les valeurs structurées volumineuses sont mises en forme sur un nombre total de nœuds objet de 10000.
Les valeurs profondément imbriquées sont mises en forme à une profondeur de 100.  Dans les deux cas, `...` est utilisé pour Elide une partie de la sortie.  Par exemple :

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

produit une sortie volumineuse avec quelques parties élidé :

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

Les cycles sont détectés dans les graphiques d’objets et `...` sont utilisés aux endroits où les cycles sont détectés. Par exemple

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

tiges

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a>Valeurs tardive, NULL et de fonction

Les valeurs tardives sont imprimées sous forme de `Value is not created` texte ou équivalent lorsque la valeur n’a pas encore été évaluée.

Les valeurs NULL sont imprimées sous `null` la forme, sauf si le type statique de la valeur est déterminé comme étant un type d’Union où `null` est une représentation autorisée.

Les valeurs de fonction F # sont imprimées comme nom de fermeture généré en interne, par exemple, `<fun:it@43-7>` .

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a>Personnaliser la mise en forme du texte brut avec`StructuredFormatDisplay`

Lors de l’utilisation du `%A` spécificateur, la présence de l' `StructuredFormatDisplay` attribut sur les déclarations de type est respectée.  Cela peut être utilisé pour spécifier le texte de substitution et la propriété pour afficher une valeur. Par exemple :

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

tiges

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a>Personnaliser la mise en forme du texte brut en remplaçant`ToString`

L’implémentation par défaut de `ToString` est observable dans la programmation F #. Souvent, les résultats par défaut ne sont pas adaptés à une utilisation dans l’affichage des informations du programmeur ou la sortie utilisateur, et par conséquent, il est courant de remplacer l’implémentation par défaut.  

Par défaut, les types d’enregistrement et d’Union F # remplacent l’implémentation de `ToString` par une implémentation de qui utilise `sprintf "%+A"` .  Par exemple :

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

tiges

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

Pour les types de classe, aucune implémentation par défaut de `ToString` n’est fournie et la valeur par défaut .net est utilisée, qui indique le nom du type. Par exemple :

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

tiges

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

L’ajout d’un remplacement pour `ToString` peut offrir une meilleure mise en forme.

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

tiges

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a>F# Interactive l’impression structurée

F# Interactive ( `dotnet fsi` ) utilise une version étendue de la mise en forme de texte brut structurée pour signaler des valeurs et permet une personnalisation supplémentaire. Pour plus d’informations, consultez [F# Interactive](fsharp-interactive-options.md).

## <a name="customize-debug-displays"></a>Personnaliser les affichages de débogage

Les débogueurs pour .NET respectent l’utilisation d’attributs tels que `DebuggerDisplay` et `DebuggerTypeProxy` , et ceux-ci affectent l’affichage structuré des objets dans les fenêtres d’inspection du débogueur.
Le compilateur F # a généré automatiquement ces attributs pour les types d’Union et d’enregistrement discriminés, mais pas pour les types de classe, d’interface ou de struct.

Ces attributs sont ignorés dans la mise en forme de texte brut F #, mais il peut être utile d’implémenter ces méthodes pour améliorer les affichages lors du débogage de types F #.

## <a name="see-also"></a>Voir aussi

- [Chaînes](strings.md)
- [Enregistrements](records.md)
- [Unions discriminées](discriminated-unions.md)
- [F# Interactive](fsharp-interactive-options.md)
