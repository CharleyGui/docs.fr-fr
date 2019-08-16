---
title: Cast et conversions
description: Découvrez comment le F# langage de programmation fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630438"
---
# <a name="casting-and-conversions-f"></a>Cast et conversions (F#)

Cette rubrique décrit la prise en charge des conversions de types dans F#.

## <a name="arithmetic-types"></a>Types arithmétiques

F#fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs, tels qu’un entier et des types à virgule flottante. Les opérateurs de conversion intégrale et de caractère ont des formes vérifiées et non vérifiées; les opérateurs à virgule flottante `enum` et l’opérateur de conversion ne le font pas. Les formulaires désactivés sont définis dans `Microsoft.FSharp.Core.Operators` et les formulaires vérifiés sont définis `Microsoft.FSharp.Core.Operators.Checked`dans. La vérification des formulaires cochés pour le dépassement de capacité et génère une exception Runtime si la valeur résultante dépasse les limites du type cible.

Chacun de ces opérateurs porte le même nom que le nom du type de destination. Par exemple, dans le code suivant, dans lequel les types sont annotés explicitement `byte` , apparaît avec deux significations différentes. La première occurrence est le type et la seconde est l’opérateur de conversion.

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

En plus des types primitifs intégrés, vous pouvez utiliser ces opérateurs avec des types qui `op_Explicit` implémentent `op_Implicit` des méthodes ou avec des signatures appropriées. Par exemple, l' `int` opérateur de conversion fonctionne avec n’importe quel type qui fournit `op_Explicit` une méthode statique qui prend le type comme paramètre `int`et retourne. En tant qu’exception particulière à la règle générale, que les méthodes ne peuvent pas être surchargées par le type de `op_Explicit` retour `op_Implicit`, vous pouvez le faire pour et.

## <a name="enumerated-types"></a>Types énumérés

L' `enum` opérateur est un opérateur générique qui accepte un paramètre de type qui représente le type du `enum` vers lequel effectuer la conversion. Quand elle est convertie en un type énuméré, les tentatives d’inférence de type permettent de `enum` déterminer le type du vers lequel vous souhaitez effectuer la conversion. Dans l’exemple suivant, la variable `col1` n’est pas annotée explicitement, mais son type est déduit du test d’égalité ultérieur. Par conséquent, le compilateur peut déduire que vous convertissez `Color` en une énumération. Vous pouvez également fournir une annotation de type, comme `col2` dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Vous pouvez également spécifier explicitement le type d’énumération cible comme paramètre de type, comme dans le code suivant:

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

La conversion entre les types dans une hiérarchie d’objets est fondamentale pour la programmation orientée objet. Il existe deux types de conversions de base: la conversion ascendante (cast) et la conversion vers le haut (passer). Effectuer un cast vers le haut d’une hiérarchie signifie effectuer un cast à partir d’une référence d’objet dérivé vers une référence d’objet de base. Ce type de conversion est garanti fonctionner tant que la classe de base est dans la hiérarchie d’héritage de la classe dérivée. La conversion descendante d’une hiérarchie, d’une référence d’objet de base à une référence d’objet dérivée, ne fonctionne que si l’objet est réellement une instance du type de destination (dérivé) correct ou un type dérivé du type de destination.

F#fournit des opérateurs pour ces types de conversions. L' `:>` opérateur effectue un cast vers le haut de la `:?>` hiérarchie et l’opérateur convertit la hiérarchie.

### <a name="upcasting"></a>Un upcast

Dans de nombreux langages orientés objet, la conversion est implicite; dans F#, les règles sont légèrement différentes. Le cast est appliqué automatiquement quand vous transmettez des arguments aux méthodes sur un type d’objet. Toutefois, pour les fonctions liées à Let dans un module, le transtypage n’est pas automatique, sauf si le type de paramètre est déclaré comme étant un type flexible. Pour plus d’informations, consultez [types flexibles](flexible-Types.md).

L' `:>` opérateur effectue un cast statique, ce qui signifie que le succès du cast est déterminé au moment de la compilation. Si un cast qui utilise `:>` des compilations réussit, il s’agit d’un cast valide qui n’a aucun risque d’échec au moment de l’exécution.

Vous pouvez également utiliser l' `upcast` opérateur pour effectuer une telle conversion. L’expression suivante spécifie une conversion vers le haut de la hiérarchie:

```fsharp
upcast expression
```

Lorsque vous utilisez l’opérateur de transtypage, le compilateur tente de déduire le type vers lequel vous effectuez la conversion à partir du contexte. Si le compilateur ne parvient pas à déterminer le type cible, le compilateur signale une erreur.

### <a name="downcasting"></a>Passer

L' `:?>` opérateur effectue un cast dynamique, ce qui signifie que le succès du cast est déterminé au moment de l’exécution. Un cast qui utilise l' `:?>` opérateur n’est pas vérifié au moment de la compilation; mais au moment de l’exécution, une tentative est effectuée pour effectuer un cast vers le type spécifié. Si l’objet est compatible avec le type cible, le cast se déroule correctement. Si l’objet n’est pas compatible avec le type cible, le runtime lève `InvalidCastException`une.

Vous pouvez également utiliser l' `downcast` opérateur pour effectuer une conversion de type dynamique. L’expression suivante spécifie une conversion descendante de la hiérarchie en un type déduit à partir du contexte du programme:

```fsharp
downcast expression
```

Comme pour l' `upcast` opérateur, si le compilateur ne peut pas déduire un type cible spécifique à partir du contexte, il signale une erreur.

Le code suivant illustre l’utilisation des `:>` opérateurs et. `:?>` Le code illustre l’utilisation de `:?>` l’opérateur lorsque vous savez que la conversion réussira, car elle `InvalidCastException` lève une exception en cas d’échec de la conversion. Si vous ne savez pas qu’une conversion est réussie, un test de type qui utilise `match` une expression est mieux, car il évite la surcharge liée à la génération d’une exception.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Étant donné que `downcast` les `upcast` opérateurs génériques et s’appuient sur l’inférence de type pour déterminer l’argument et le type de retour, dans le code ci-dessus, vous pouvez remplacer

```fsharp
let base1 = d1 :> Base1
```

par

```fsharp
let base1 = upcast d1
```

Dans le code précédent, le type d’argument et les types `Derived1` de `Base1`retour sont respectivement et.

Pour plus d’informations sur les tests de type, consultez [expressions de correspondance](match-Expressions.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
