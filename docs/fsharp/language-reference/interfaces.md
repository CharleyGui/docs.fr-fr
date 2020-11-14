---
title: Interfaces
description: 'Découvrez comment les interfaces F # spécifient des jeux de membres connexes que d’autres classes implémentent.'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557049"
---
# <a name="interfaces"></a>Interfaces

Les *interfaces* spécifient des ensembles de membres associés que d’autres classes implémentent.

## <a name="syntax"></a>Syntaxe

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Notes

Les déclarations d’interface ressemblent aux déclarations de classe, à ceci près qu’aucun membre n’est implémenté. Au lieu de cela, tous les membres sont abstraits, comme indiqué par le mot clé `abstract` . Vous ne fournissez pas de corps de méthode pour les méthodes abstraites. Toutefois, vous pouvez fournir une implémentation par défaut en incluant également une définition distincte du membre en tant que méthode avec le `default` mot clé. Cela revient à créer une méthode virtuelle dans une classe de base dans d’autres langages .NET. Une telle méthode virtuelle peut être substituée dans les classes qui implémentent l’interface.

L’accessibilité par défaut pour les interfaces est `public` .

Vous pouvez éventuellement attribuer un nom à chaque paramètre de méthode à l’aide d’une syntaxe F # normale :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Dans l’exemple ci-dessus `ISprintable` , la `Print` méthode a un seul paramètre du type `string` portant le nom `format` .

Il existe deux façons d’implémenter des interfaces : en utilisant des expressions d’objet et des types de classe. Dans les deux cas, le type de classe ou l’expression d’objet fournit des corps de méthode pour les méthodes abstraites de l’interface. Les implémentations sont spécifiques à chaque type qui implémente l’interface. Par conséquent, les méthodes d’interface sur des types différents peuvent être différentes les unes des autres.

Les mots clés `interface` et `end` , qui marquent le début et la fin de la définition, sont facultatifs lorsque vous utilisez la syntaxe simplifiée. Si vous n’utilisez pas ces mots clés, le compilateur tente de déduire si le type est une classe ou une interface en analysant les constructions que vous utilisez. Si vous définissez un membre ou utilisez une autre syntaxe de classe, le type est interprété comme une classe.

Le style de codage .NET consiste à commencer toutes les interfaces en majuscules `I` .

Vous pouvez spécifier plusieurs paramètres de deux manières : le style F # et le. Style NET. Les deux seront compilés de la même façon pour les consommateurs .NET, mais le style F # forcera les appelants F # à utiliser l’application de paramètre de style F # et. NET-style forcera les appelants F # à utiliser l’application d’arguments avec des tuples.

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>Implémentation d’interfaces à l’aide de types de classe

Vous pouvez implémenter une ou plusieurs interfaces dans un type de classe en utilisant le `interface` mot clé, le nom de l’interface et le `with` mot clé, suivis par les définitions de membres d’interface, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Les implémentations d’interface sont héritées, de sorte que toutes les classes dérivées n’ont pas besoin de les réimplémenter.

## <a name="calling-interface-methods"></a>Appeler des méthodes d’interface

Les méthodes d’interface peuvent être appelées uniquement par le biais de l’interface, et non par l’intermédiaire d’un objet du type qui implémente l’interface. Par conséquent, vous devrez peut-être effectuer une conversion vers le type d’interface à l’aide de l' `:>` opérateur ou `upcast` de l’opérateur pour appeler ces méthodes.

Pour appeler la méthode d’interface quand vous avez un objet de type `SomeClass` , vous devez effectuer un upcast de l’objet vers le type d’interface, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Une alternative consiste à déclarer une méthode sur l’objet qui effectue un upcast et appelle la méthode d’interface, comme dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implémentation d’interfaces à l’aide d’expressions d’objet

Les expressions d’objet fournissent un bref moyen d’implémenter une interface. Elles sont utiles lorsque vous n’avez pas besoin de créer un type nommé et que vous souhaitez simplement un objet qui prend en charge les méthodes d’interface, sans aucune méthode supplémentaire. Une expression d’objet est illustrée dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Héritage de l'interface

Les interfaces peuvent hériter d’une ou de plusieurs interfaces de base.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a>Implémentation d’interfaces avec des implémentations par défaut

C# prend en charge la définition d’interfaces avec des implémentations par défaut, comme suit :

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

Celles-ci sont directement consommables à partir de F # :

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

Vous pouvez substituer une implémentation par défaut avec `override` , comme remplacer n’importe quel membre virtuel.

Les membres d’une interface qui n’ont pas d’implémentation par défaut doivent tout de même être implémentés de manière explicite.

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a>Implémentation de la même interface à différentes instanciations génériques

F # prend en charge l’implémentation de la même interface à différentes instanciations génériques, comme ceci :

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Expressions d'objet](object-expressions.md)
- [Classes](classes.md)
