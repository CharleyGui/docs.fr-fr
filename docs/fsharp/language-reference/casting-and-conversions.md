---
title: Cast et conversions
description: Découvrez comment le F# langage de programmation fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543584"
---
# <a name="casting-and-conversions-f"></a>Cast et conversions (F#)

Cette rubrique décrit la prise en charge des conversions de types dans F#.

## <a name="arithmetic-types"></a>Types arithmétiques

F#fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs, tels qu’un entier et des types à virgule flottante. Les opérateurs de conversion intégrale et de caractère ont des formes vérifiées et non vérifiées ; les opérateurs à virgule flottante et l’opérateur de conversion `enum` ne le font pas. Les formulaires désactivés sont définis dans `Microsoft.FSharp.Core.Operators` et les formulaires vérifiés sont définis dans `Microsoft.FSharp.Core.Operators.Checked`. La vérification des formulaires cochés pour le dépassement de capacité et génère une exception Runtime si la valeur résultante dépasse les limites du type cible.

Chacun de ces opérateurs porte le même nom que le nom du type de destination. Par exemple, dans le code suivant, dans lequel les types sont annotés explicitement, `byte` apparaît avec deux significations différentes. La première occurrence est le type et la seconde est l’opérateur de conversion.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

Le tableau suivant présente les opérateurs de conversion F#définis dans.

|Opérateur|Description|
|--------|-----------|
|`byte`|Convertit en Byte, un type non signé 8 bits.|
|`sbyte`|Convertir en octet signé.|
|`int16`|Convertit en entier 16 bits signé.|
|`uint16`|Convertit en entier 16 bits non signé.|
|`int32, int`|Convertit en entier signé 32 bits.|
|`uint32`|Convertit en entier non signé 32 bits.|
|`int64`|Convertit en entier signé 64 bits.|
|`uint64`|Convertit en entier non signé 64 bits.|
|`nativeint`|Convertit en entier natif.|
|`unativeint`|Convertit en entier natif non signé.|
|`float, double`|Convertit en nombre à virgule flottante IEEE double précision 64 bits.|
|`float32, single`|Convertit en nombre à virgule flottante IEEE simple précision 32 bits.|
|`decimal`|Convertit en `System.Decimal`.|
|`char`|Convertit en `System.Char`, un caractère Unicode.|
|`enum`|Convertit en type énuméré.|

En plus des types primitifs intégrés, vous pouvez utiliser ces opérateurs avec des types qui implémentent des méthodes `op_Explicit` ou `op_Implicit` avec les signatures appropriées. Par exemple, l’opérateur de conversion `int` fonctionne avec n’importe quel type qui fournit une méthode statique `op_Explicit` qui prend le type comme paramètre et retourne `int`. En tant qu’exception particulière à la règle générale, que les méthodes ne peuvent pas être surchargées par le type de retour, vous pouvez le faire pour `op_Explicit` et `op_Implicit`.

## <a name="enumerated-types"></a>Types énumérés

L’opérateur `enum` est un opérateur générique qui accepte un paramètre de type qui représente le type de l' `enum` vers lequel effectuer la conversion. Lorsqu’elle est convertie en un type énuméré, les tentatives d’inférence de type permettent de déterminer le type de l' `enum` vers lequel vous souhaitez effectuer la conversion. Dans l’exemple suivant, la variable `col1` n’est pas annotée explicitement, mais son type est déduit du test d’égalité ultérieur. Par conséquent, le compilateur peut déduire que vous convertissez en une énumération `Color`. Vous pouvez également fournir une annotation de type, comme avec `col2` dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Vous pouvez également spécifier explicitement le type d’énumération cible comme paramètre de type, comme dans le code suivant :

```fsharp
let col3 = enum<Color> 3
```

Notez que les conversions d’énumération fonctionnent uniquement si le type sous-jacent de l’énumération est compatible avec le type en cours de conversion. Dans le code suivant, la compilation échoue en raison de l’incompatibilité entre `int32` et `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Pour plus d’informations, consultez [énumérations](enumerations.md).

## <a name="casting-object-types"></a>Cast de types d’objet

La conversion entre les types dans une hiérarchie d’objets est fondamentale pour la programmation orientée objet. Il existe deux types de conversions de base : la conversion ascendante (cast) et la conversion vers le haut (passer). Effectuer un cast vers le haut d’une hiérarchie signifie effectuer un cast à partir d’une référence d’objet dérivé vers une référence d’objet de base. Ce type de conversion est garanti fonctionner tant que la classe de base est dans la hiérarchie d’héritage de la classe dérivée. La conversion descendante d’une hiérarchie, d’une référence d’objet de base à une référence d’objet dérivée, ne fonctionne que si l’objet est réellement une instance du type de destination (dérivé) correct ou un type dérivé du type de destination.

F#fournit des opérateurs pour ces types de conversions. L’opérateur `:>` effectue un cast vers le haut de la hiérarchie, et l’opérateur `:?>` convertit la hiérarchie.

### <a name="upcasting"></a>Un upcast

Dans de nombreux langages orientés objet, la conversion est implicite ; dans F#, les règles sont légèrement différentes. Le cast est appliqué automatiquement quand vous transmettez des arguments aux méthodes sur un type d’objet. Toutefois, pour les fonctions liées à Let dans un module, le transtypage n’est pas automatique, sauf si le type de paramètre est déclaré comme étant un type flexible. Pour plus d’informations, consultez [types flexibles](flexible-Types.md).

L’opérateur `:>` effectue un cast statique, ce qui signifie que le succès du cast est déterminé au moment de la compilation. Si un cast qui utilise `:>` est compilé avec succès, il s’agit d’un cast valide qui n’a aucun risque d’échec au moment de l’exécution.

Vous pouvez également utiliser l’opérateur `upcast` pour effectuer une telle conversion. L’expression suivante spécifie une conversion vers le haut de la hiérarchie :

```fsharp
upcast expression
```

Lorsque vous utilisez l’opérateur de transtypage, le compilateur tente de déduire le type vers lequel vous effectuez la conversion à partir du contexte. Si le compilateur ne parvient pas à déterminer le type cible, le compilateur signale une erreur. Une annotation de type peut être requise.

### <a name="downcasting"></a>Passer

L’opérateur `:?>` effectue un cast dynamique, ce qui signifie que le succès du cast est déterminé au moment de l’exécution. Un cast qui utilise l’opérateur `:?>` n’est pas vérifié au moment de la compilation ; mais au moment de l’exécution, une tentative est effectuée pour effectuer un cast vers le type spécifié. Si l’objet est compatible avec le type cible, le cast se déroule correctement. Si l’objet n’est pas compatible avec le type cible, le runtime lève une `InvalidCastException`.

Vous pouvez également utiliser l’opérateur `downcast` pour effectuer une conversion de type dynamique. L’expression suivante spécifie une conversion descendante de la hiérarchie en un type déduit à partir du contexte du programme :

```fsharp
downcast expression
```

Comme pour l’opérateur `upcast`, si le compilateur ne peut pas déduire un type cible spécifique à partir du contexte, il signale une erreur. Une annotation de type peut être requise.

Le code suivant illustre l’utilisation des opérateurs `:>` et `:?>`. Le code illustre l’utilisation de l’opérateur `:?>` lorsque vous savez que la conversion réussira, car elle lève `InvalidCastException` en cas d’échec de la conversion. Si vous ne savez pas qu’une conversion est réussie, un test de type qui utilise une expression `match` est mieux, car il évite la surcharge liée à la génération d’une exception.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Étant donné que les opérateurs génériques `downcast` et `upcast` s’appuient sur l’inférence de type pour déterminer l’argument et le type de retour, dans le code ci-dessus, vous pouvez remplacer

```fsharp
let base1 = d1 :> Base1
```

par

```fsharp
let base1: Base1 = upcast d1
```

Notez qu’une annotation de type est requise, car `upcast` en elle-même ne peut pas déterminer la classe de base.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
