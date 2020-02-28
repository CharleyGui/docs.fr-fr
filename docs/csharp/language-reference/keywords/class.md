---
title: class, mot clé - Référence C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673093"
---
# <a name="class-c-reference"></a>class (référence C#)

Les classes sont déclarées à l’aide du mot clé `class`, comme l’illustre l’exemple suivant :

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Notes

Le langage C# ne permet qu'un seul héritage. Cela signifie qu’une classe peut uniquement hériter de l’implémentation d’une seule classe de base. Toutefois, une classe peut implémenter plusieurs interfaces. Le tableau suivant répertorie des exemples d’héritage de classe et d’implémentation d’interface :

|Héritage|Exemple|
|-----------------|-------------|
|None|`class ClassA { }`|
|Unique|`class DerivedClass : BaseClass { }`|
|Aucun, implémente deux interfaces|`class ImplClass : IFace1, IFace2 { }`|
|Unique, implémente une seule interface|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Les classes que vous déclarez directement dans un espace de noms, non imbriquées dans d’autres classes, peuvent être [public](./public.md) ou [internal](./internal.md). Par défaut, les classes sont `internal`.

Les membres de classe, notamment les classes imbriquées, peuvent être [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md) ou [private protected](private-protected.md). Par défaut, ils sont `private`.

Pour plus d’informations, consultez la page [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).

Vous pouvez déclarer des classes génériques qui ont des paramètres de type. Pour plus d’informations, consultez [Classes génériques](../../programming-guide/generics/generic-classes.md).

Une classe peut contenir les déclarations des membres suivants :

- [Constructeurs](../../programming-guide/classes-and-structs/constructors.md)

- [Constantes](../../programming-guide/classes-and-structs/constants.md)

- [Fields](../../programming-guide/classes-and-structs/fields.md)

- [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md)

- [Méthodes](../../programming-guide/classes-and-structs/methods.md)

- [Propriétés](../../programming-guide/classes-and-structs/properties.md)

- [Indexeurs](../../programming-guide/indexers/index.md)

- [Opérateurs](../operators/index.md)

- [Événements](../../programming-guide/events/index.md)

- [Délégués](../../programming-guide/delegates/index.md)

- [Classes](../../programming-guide/classes-and-structs/classes.md)

- [Interfaces](../../programming-guide/interfaces/index.md)

- [Types de structures](../builtin-types/struct.md)

- [Types énumération](../builtin-types/enum.md)

## <a name="example"></a>Exemple

L’exemple suivant explique comment déclarer des champs, des constructeurs et des méthodes de classe. Il illustre également l’instanciation d’un objet et l’impression des données d’une instance. Dans cet exemple, deux classes sont déclarées. La première, `Child`, contient deux champs privés (`name` et `age`), deux constructeurs publics et une méthode publique. La deuxième, `StringTest`, contient `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Commentaires

Notez que, dans l’exemple précédant, les champs privés (`name` et `age`) ne sont accessibles que par le biais de la méthode publique de la classe `Child`. Par exemple, vous ne pouvez pas imprimer le nom de l’enfant à partir de la méthode `Main` en utilisant une instruction comme celle-ci :

```csharp
Console.Write(child1.name);   // Error
```

L’accès aux membres privés de `Child` à partir de `Main` est uniquement possible si `Main` est un membre de la classe.

Du fait que les types déclarés dans une classe sans modificateur d’accès sont par défaut `private`, les données membres dans cet exemple sont toujours `private` si le mot clé est supprimé.

Notez enfin que pour l’objet créé à l’aide du constructeur sans paramètre (`child3`), le champ `age` est initialisé par défaut à la valeur zéro.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Types référence](./reference-types.md)
