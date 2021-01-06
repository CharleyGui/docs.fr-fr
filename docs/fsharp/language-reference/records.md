---
title: Enregistrements
description: 'Découvrez comment les enregistrements F # représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.'
ms.date: 08/15/2020
ms.openlocfilehash: 2da31da0ec830d458a370e64ca105048181f5d74
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899637"
---
# <a name="records"></a>Enregistrements

Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres. Ils peuvent être des structs ou des types référence.  Il s’agit de types référence par défaut.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *TypeName* est le nom du type d’enregistrement, *Label1* et *Label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs. *member-List* est la liste facultative de membres pour le type.  Vous pouvez utiliser l' `[<Struct>]` attribut pour créer un enregistrement de struct plutôt qu’un enregistrement qui est un type référence.

Voici quelques exemples.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.

Vous pouvez définir des valeurs dans des expressions appelées *expressions d’enregistrement*. Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment distinctes de celles des autres types d’enregistrements). Les accolades ({}) encadrent l’expression d’enregistrement. Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec des étiquettes `x` , `y` et `z` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

N’utilisez pas la forme abrégée s’il peut y avoir un autre type qui a également les mêmes étiquettes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Les étiquettes du type déclaré le plus récemment sont prioritaires sur celles du type déclaré précédemment. par conséquent, dans l’exemple précédent, `mypoint3D` est déduit comme étant `Point3D` . Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Les méthodes peuvent être définies pour les types d’enregistrements comme pour les types de classe.

## <a name="creating-records-by-using-record-expressions"></a>Création d’enregistrements à l’aide d’expressions d’enregistrement

Vous pouvez initialiser des enregistrements à l’aide des étiquettes définies dans l’enregistrement. Une expression qui le fait est appelée *expression d’enregistrement*. Utilisez des accolades pour encadrer l’expression d’enregistrement et utilisez le point-virgule comme délimiteur.

L’exemple suivant montre comment créer un enregistrement.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Les points-virgules situés après le dernier champ dans l’expression d’enregistrement et dans la définition de type sont facultatifs, que les champs soient tous en une seule ligne ou non.

Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ. Vous ne pouvez pas faire référence aux valeurs d’autres champs dans l’expression d’initialisation d’un champ.

Dans le code suivant, le type de `myRecord2` est déduit à partir des noms des champs. Si vous le souhaitez, vous pouvez spécifier le nom du type explicitement.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ. La ligne de code suivante illustre cela.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Cette forme de l’expression d’enregistrement est appelée *expression d’enregistrement de copie et de mise à jour*.

Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez facilement créer des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour. Vous pouvez également spécifier explicitement un champ mutable.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

N’utilisez pas l’attribut DefaultValue avec les champs d’enregistrement. Une meilleure approche consiste à définir des instances par défaut d’enregistrements avec des champs qui sont initialisés aux valeurs par défaut, puis à utiliser une expression d’enregistrement de copie et de mise à jour pour définir tous les champs qui diffèrent des valeurs par défaut.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a>Création d’enregistrements mutuellement récursifs

Pendant la création d’un enregistrement, vous souhaiterez peut-être qu’il dépende d’un autre type que vous aimeriez définir par la suite. Il s’agit d’une erreur de compilation, sauf si vous définissez les types d’enregistrements qui doivent être mutuellement récursifs.

La définition des enregistrements mutuellement récursifs s’effectue à l’aide du `and` mot clé. Cela vous permet de lier simultanément 2 types d’enregistrements ou plus.

Par exemple, le code suivant définit un `Person` `Address` type et comme étant mutuellement récursif :

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

Si vous deviez définir l’exemple précédent sans le `and` mot clé, il n’est pas compilé. Le `and` mot clé est requis pour les définitions mutuellement récursives.

## <a name="pattern-matching-with-records"></a>Critères spéciaux avec enregistrements

Les enregistrements peuvent être utilisés avec des critères spéciaux. Vous pouvez spécifier des champs explicitement et fournir des variables pour d’autres champs qui seront affectés quand une correspondance se produit. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Le résultat de ce code est le suivant.

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a>Enregistrements et membres

Vous pouvez spécifier des membres sur des enregistrements de la même façon que vous pouvez utiliser des classes. Les champs ne sont pas pris en charge. Une approche courante consiste à définir un `Default` membre statique pour une création d’enregistrement facile :

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

Si vous utilisez un auto-identificateur, cet identificateur fait référence à l’instance de l’enregistrement dont le membre est appelé :

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123" }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a>Différences entre les enregistrements et les classes

Les champs d’enregistrement diffèrent des champs de classe dans la mesure où ils sont automatiquement exposés en tant que propriétés et sont utilisés lors de la création et de la copie des enregistrements. La construction d’enregistrement diffère également de la construction de classe. Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur. Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique. Les classes n’ont aucune relation directe entre les paramètres de constructeur, les champs et les propriétés.

Comme les types d’Union et de structure, les enregistrements ont une sémantique d’égalité structurelle. Les classes ont une sémantique d’égalité des références. L'exemple de code suivant illustre cette tâche.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Le résultat de ce code est le suivant :

```console
The records are equal.
```

Si vous écrivez le même code avec des classes, les deux objets de classe seraient inégaux, car les deux valeurs représenteront deux objets sur le tas et seules les adresses seraient comparées (sauf si le type de classe substitue la `System.Object.Equals` méthode).

Si vous avez besoin d’une égalité de référence pour les enregistrements, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.

## <a name="see-also"></a>Voir aussi

- [Types F#](fsharp-types.md)
- [Classes](classes.md)
- [Informations de référence sur le langage F #](index.md)
- [Référence-égalité](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [Critères spéciaux](pattern-matching.md)
