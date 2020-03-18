---
title: interface - Référence C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625850"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(Référence de C)

Une interface définit un contrat. Tout [`class`](class.md) [`struct`](../builtin-types/struct.md) ou tel implémentation du contrat doit fournir une mise en œuvre des membres définis dans l’interface. En commençant par le C 8.0, une interface peut définir une implémentation par défaut pour les membres. Il peut [`static`](static.md) également définir les membres afin de fournir une implémentation unique pour les fonctionnalités communes.

Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.

Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).

## <a name="example"></a> Exemple

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Une interface peut être membre d’un espace de nom ou d’une classe. Une déclaration d’interface peut contenir des déclarations (signatures sans aucune mise en œuvre) des membres suivants :

- [Méthodes](../../programming-guide/classes-and-structs/methods.md)
- [Propriétés](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexeurs](../../programming-guide/indexers/using-indexers.md)
- [Événements](event.md)

Ces déclarations précédentes ne contiennent généralement pas d’organe. En commençant par le C 8.0, un membre de l’interface peut déclarer un corps. C’est ce qu’on appelle une *implémentation par défaut*. Les membres avec des organismes permettent à l’interface de fournir une mise en œuvre « par défaut » pour les classes et les structs qui ne fournissent pas une mise en œuvre primordiale. En outre, à partir de C 8.0, une interface peut inclure:

- [Constantes](const.md)
- [Opérateurs](../operators/operator-overloading.md)
- [Constructeur statique](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Types imbriqués](../../programming-guide/classes-and-structs/nested-types.md)
- [Champs, méthodes, propriétés, indexateurs et événements statiques](static.md)
- Déclarations des membres à l’aide de la syntaxe explicite de mise en œuvre de l’interface.
- Modificateurs d’accès explicites (l’accès par défaut est [`public`](access-modifiers.md)).

Les interfaces ne peuvent pas contenir l’état d’instance. Bien que les champs statiques soient maintenant autorisés, les champs d’instance ne sont pas autorisés dans les interfaces. [Les auto-propriétés d’instance](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ne sont pas prises en charge dans les interfaces, car elles déclareraient implicitement un champ caché. Cette règle a un effet subtil sur les déclarations de propriété. Dans une déclaration d’interface, le code suivant ne déclare `class` pas `struct`une propriété auto-mise en œuvre comme il le fait dans un ou . Au lieu de cela, il déclare une propriété qui n’a pas de mise en œuvre par défaut, mais doit être implémentée dans n’importe quel type qui implémente l’interface:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Une interface peut hériter d’une ou de plusieurs interfaces de base. Lorsqu’une interface [remplace une méthode](override.md) implémentée dans une interface de base, elle doit utiliser la syntaxe explicite de [implémentation de l’interface.](../../programming-guide/interfaces/explicit-interface-implementation.md)

Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.

Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface. Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface. En outre, les membres de l’interface par défaut ne peuvent être consultés que par une instance de l’interface.

Pour plus d’informations sur la mise en œuvre explicite de l’interface, voir [Implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a> Exemple

L’exemple suivant montre une implémentation d’interface. Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation. Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section Interfaces de la [spécification linguistique C et](~/_csharplang/spec/introduction.md) la spécification des [fonctionnalités](~/_csharplang/spec/interfaces.md) pour [les membres de l’interface par défaut - C 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Types de référence](reference-types.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
- [Utilisation de propriétés](../../programming-guide/classes-and-structs/using-properties.md)
- [Utilisation des indexeurs](../../programming-guide/indexers/using-indexers.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
