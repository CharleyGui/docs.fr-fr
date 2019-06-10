---
title: Enregistrements
description: Découvrez comment F# enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.
ms.date: 06/09/2019
ms.openlocfilehash: cfb8de8272b479571119ae4cf91ea1d6fd5db73c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816193"
---
# <a name="records"></a>Enregistrements

Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres. Ils peuvent être soit les types de structures ou de référence.  Ils sont des types de référence par défaut.

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

Dans la syntaxe précédente, *typename* est le nom du type d’enregistrement, *label1* et *label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs. *liste des membres* est la liste facultative de membres pour le type.  Vous pouvez utiliser le `[<Struct>]` attribut pour créer un enregistrement struct plutôt qu’un enregistrement qui est un type référence.

Voici quelques exemples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.

Vous pouvez définir des valeurs dans les expressions appelées *enregistrer expressions*. Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment différents de ceux des autres types d’enregistrements). Accolades ({}) placez l’expression d’enregistrement. Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec des étiquettes `x`, `y` et `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

S’il peut y avoir un autre type qui possède également les étiquettes de mêmes, n’utilisez pas la forme abrégée.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Les étiquettes de type le plus récemment déclaré ont priorité sur ceux du type déclaré précédemment, c’est le cas dans l’exemple précédent, `mypoint3D` est déduite comme étant `Point3D`. Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Méthodes peuvent être définies pour les types d’enregistrements comme pour les types de classe.

## <a name="creating-records-by-using-record-expressions"></a>Création d’enregistrements à l’aide d’Expressions d’enregistrement

Vous pouvez initialiser des enregistrements en utilisant les étiquettes qui sont définis dans l’enregistrement. Une expression qui s’en charge est appelée un *enregistrement expression*. Utiliser des accolades pour encadrer l’expression d’enregistrement et le point-virgule comme délimiteur.

L’exemple suivant montre comment créer un enregistrement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Les points-virgules après le dernier champ dans l’expression d’enregistrement et dans la définition de type sont facultatifs, que les champs soient tous sur une ligne.

Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ. Vous ne pouvez pas référencer les valeurs des autres champs dans l’expression d’initialisation pour n’importe quel champ.

Dans le code suivant, le type de `myRecord2` est déduit des noms des champs. Si vous le souhaitez, vous pouvez spécifier le nom de type explicitement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ. La ligne de code suivante illustre cela.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Cette forme de l’expression d’enregistrement est appelée le *copier et mettre à jour d’expression d’enregistrement*.

Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez créer facilement des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour. Vous pouvez également spécifier explicitement un champ mutable.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

N’utilisez pas l’attribut DefaultValue avec des champs d’enregistrement. Une meilleure approche consiste à définir les instances par défaut des enregistrements avec des champs qui sont initialisées aux valeurs par défaut et utiliser une copie, puis mettre à jour d’expression d’enregistrement pour définir tous les champs qui diffèrent des valeurs par défaut.

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

## <a name="creating-mutually-recursive-records"></a>Création de mutuellement récursives enregistrements

Un certain temps lorsque vous créez un enregistrement, vous souhaiterez probablement qu’il dépend d’un autre type que vous souhaitez définir par la suite. Il s’agit d’une erreur de compilation, sauf si vous définissez les types d’enregistrement pour être mutuellement récursives.

Définition mutuellement récursives enregistrements est effectuée avec la `and` mot clé. Cela vous permet de relier les types de 2 ou plus d’enregistrements.

Par exemple, le code suivant définit un `Person` et `Address` type comme mutuellement récursives :

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
    PostCode: string }
```

Si vous deviez définir l’exemple précédent, sans le `and` mot clé, puis il n’est pas compilée. Le `and` mot clé est requise pour les définitions récursives s’excluent mutuellement.

## <a name="pattern-matching-with-records"></a>Critères spéciaux avec enregistrements

Enregistrements peuvent être utilisés avec les critères spéciaux. Vous pouvez spécifier des champs explicitement et fournir des variables pour les autres champs qui seront affectés lors d’une correspondance est trouvée. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

La sortie de ce code est comme suit.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Différences entre les Classes et les enregistrements

Champs d’enregistrement diffèrent des classes dans la mesure où ils sont automatiquement exposés en tant que propriétés, et ils sont utilisés dans la création et de copie d’enregistrements. Construction d’enregistrement diffère également de construction de classe. Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur. Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique. Classes n’ont aucune relation directe entre les paramètres du constructeur, des champs et propriétés.

Comme les types d’union et de structure, les enregistrements ont une sémantique d’égalité structurelle. Classes ont référence une sémantique d’égalité. L'exemple de code suivant illustre cette tâche.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

La sortie de ce code est comme suit :

```
The records are equal.
```

Si vous écrivez le même code avec les classes, les deux objets de classe seraient inégaux, car les deux valeurs représenteraient deux objets sur le tas et seules les adresses seraient comparées (à moins que le type de la classe substitue la `System.Object.Equals` méthode).

Si vous avez besoin de référencer l’égalité des enregistrements, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.

## <a name="see-also"></a>Voir aussi

- [Types F#](fsharp-types.md)
- [Classes](classes.md)
- [Informations de référence du langage F#](index.md)
- [Égalité de référence](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [Critères spéciaux](pattern-matching.md)
