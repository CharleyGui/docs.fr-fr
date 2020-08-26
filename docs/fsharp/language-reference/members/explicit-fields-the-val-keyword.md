---
title: 'Champs explicites : mot clé val'
description: "En savoir plus sur le mot clé F # 'Val', qui est utilisé pour déclarer un emplacement pour stocker une valeur dans un type de classe ou de structure sans initialiser le type."
ms.date: 08/15/2020
ms.openlocfilehash: 9f5599a241f27b234eeacf48327b4ccbc46ed38c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811780"
---
# <a name="explicit-fields-the-val-keyword"></a>Champs explicites : mot clé val

Le mot clé `val` est utilisé pour déclarer un emplacement pour stocker une valeur dans un type de classe ou de structure sans l'initialiser. Les emplacements de stockage déclarés de cette manière sont appelés *champs explicites*. Une autre utilisation du mot clé `val` consiste à l'associer avec le mot clé `member` pour déclarer une propriété implémentée automatiquement. Pour plus d’informations sur les propriétés implémentées automatiquement, consultez [Propriétés](properties.md).

## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Notes

La façon habituelle de définir des champs dans un type de classe ou de structure consiste à utiliser une liaison `let`. Toutefois, les liaisons `let` doivent être initialisées dans le cadre du constructeur de classe, ce qui n'est pas toujours possible, nécessaire ou souhaitable. Vous pouvez utiliser le mot clé `val` quand vous voulez un champ qui n'est pas initialisé.

Les champs explicites peuvent être statiques ou non statiques. Le *modificateur d’accès* peut être `public` , `private` ou `internal` . Par défaut, les champs explicites sont publics. À la différence des liaisons `let` dans les classes, qui elles sont toujours privées.

L’attribut [DefaultValue](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-defaultvalueattribute.html) est requis sur les champs explicites dans les types de classe qui ont un constructeur principal. Cet attribut spécifie que le champ est initialisé à zéro. Le type du champ doit prendre en charge l'initialisation à zéro. Un type prend en charge l'initialisation à zéro s'il s'agit d'un type suivant :

- Type primitif qui a une valeur zéro.
- Type qui prend en charge une valeur null, en tant que valeur normale, en tant que valeur anormale ou en tant que représentation d'une valeur. Sont inclus les classes, les tuples, les enregistrements, les fonctions, les interfaces, les types référence .NET, le type `unit` et les types union discriminée.
- Type valeur .NET.
- Structure dont les champs prennent tous en charge une valeur zéro par défaut.

Par exemple, un champ immuable appelé `someField` a un champ de stockage dans la représentation compilée .NET portant le nom `someField@` et vous accédez à la valeur stockée à l'aide d'une propriété nommée `someField`.

Pour un champ mutable, la représentation compilée .NET est un champ .NET.

> [!WARNING]
> L’espace de noms .NET Framework `System.ComponentModel` contient un attribut qui porte le même nom. Pour plus d'informations sur cet attribut, consultez <xref:System.ComponentModel.DefaultValueAttribute>.

Le code suivant illustre l'utilisation de champs explicites et, à titre de comparaison, d'une liaison `let` dans une classe qui a un constructeur principal. Notez que le champ lié à `let``myInt1` est privé. Quand le champ lié à `let``myInt1` est référencé à partir d'une méthode membre, l'auto-identificateur `this` n'est pas requis. Mais quand vous référencez les champs explicites `myInt2` et `myString`, l'auto-identificateur est requis.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

La sortie se présente comme suit :

```console
11 12 abc
30 def
```

Le code suivant illustre l'utilisation de champs explicites dans une classe qui n'a pas de constructeur principal. Dans ce cas, l'attribut `DefaultValue` n'est pas requis, mais tous les champs doivent être initialisés dans les constructeurs définis pour le type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

La sortie est `35 22`.

Le code suivant illustre l'utilisation de champs explicites dans une structure. Comme une structure est un type valeur, elle a automatiquement un constructeur sans paramètre qui définit les valeurs de ses champs à zéro. Ainsi, l'attribut `DefaultValue` n'est pas requis.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

La sortie est `11 xyz`.

**Attention**: Si vous envisagez d’initialiser votre structure avec des `mutable` champs sans `mutable` mot clé, vos attributions fonctionneront sur une copie de la structure qui sera ignorée juste après l’affectation. Par conséquent, votre structure ne changera pas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Les champs explicites n'ont pas vocation à être utilisés dans le cadre d'une routine. En général, quand cela est possible, vous devez utiliser une liaison `let` dans une classe au lieu d’un champ explicite. Les champs explicites s'avèrent utiles dans certains scénarios d'interopérabilité, notamment quand vous devez définir une structure qui sera utilisée dans un appel de code non managé à une API native ou dans des scénarios COM interop. Pour plus d’informations, consultez [fonctions externes](../functions/external-functions.md). Une autre situation dans laquelle un champ explicite peut s'avérer nécessaire est liée à l'utilisation d'un générateur de code F# qui émet des classes sans constructeur principal. Les champs explicites s'avèrent également utiles pour les variables static de thread ou les constructions similaires. Pour plus d'informations, consultez `System.ThreadStaticAttribute`.

Quand les mots clés `member val` apparaissent ensemble dans une définition de type, il s'agit de la définition d'une propriété implémentée automatiquement. Pour plus d'informations, consultez [Propriétés](properties.md).

## <a name="see-also"></a>Voir aussi

- [Propriétés](properties.md)
- [Members](index.md) (Membres)
- [`let` Liaisons dans des classes](let-bindings-in-classes.md)
