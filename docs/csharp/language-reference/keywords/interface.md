---
description: ':::no-loc text=interface::: (Référence C#)'
title: interface - Référence C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134586"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface"::: (Référence C#)

Une interface définit un contrat. Tout [`class`](class.md) ou [`struct`](../builtin-types/struct.md) qui implémente ce contrat doit fournir une implémentation des membres définis dans l’interface. À compter de C# 8,0, une interface peut définir une implémentation par défaut pour les membres. Il peut également définir des membres afin de [`static`](static.md) fournir une implémentation unique pour les fonctionnalités communes.

Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.

Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Exemple

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Une interface peut être membre d’un espace de noms ou d’une classe. Une déclaration d’interface peut contenir des déclarations (signatures sans implémentation) des membres suivants :

- [Méthodes](../../programming-guide/classes-and-structs/methods.md)
- [Propriétés](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexeurs](../../programming-guide/indexers/using-indexers.md)
- [Événements](event.md)

Les déclarations de membre précédentes ne contiennent généralement pas de corps. À compter de C# 8,0, un membre d’interface peut déclarer un corps. C’est ce qu’on appelle une *implémentation par défaut*. Les membres avec des corps permettent à l’interface de fournir une implémentation « par défaut » pour les classes et les structs qui ne fournissent pas d’implémentation de substitution. En outre, à compter de C# 8,0, une interface peut inclure les éléments suivants :

- [Constantes](const.md)
- [Opérateurs](../operators/operator-overloading.md)
- [Constructeur statique](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Types imbriqués](../../programming-guide/classes-and-structs/nested-types.md)
- [Champs, méthodes, propriétés, indexeurs et événements statiques](static.md)
- Déclarations de membre à l’aide de la syntaxe d’implémentation d’interface explicite.
- Modificateurs d’accès explicites (l’accès par défaut est [`public`](access-modifiers.md) ).

Les interfaces ne peuvent pas contenir l’état de l’instance. Alors que les champs statiques sont désormais autorisés, les champs d’instance ne sont pas autorisés dans les interfaces. Les [propriétés auto des instances](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ne sont pas prises en charge dans les interfaces, car elles déclarent implicitement un champ masqué. Cette règle a un effet subtil sur les déclarations de propriété. Dans une déclaration d’interface, le code suivant ne déclare pas une propriété implémentée automatiquement comme elle le fait dans un `class` ou un `struct` . Au lieu de cela, elle déclare une propriété qui n’a pas d’implémentation par défaut, mais qui doit être implémentée dans tout type qui implémente l’interface :

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Une interface peut hériter d’une ou de plusieurs interfaces de base. Quand une interface [se substitue à une méthode](override.md) implémentée dans une interface de base, elle doit utiliser la syntaxe d' [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md) .

Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.

Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface. Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface. En outre, les membres d’interface par défaut sont accessibles uniquement par le biais d’une instance de l’interface.

Pour plus d’informations sur l’implémentation d’interface explicite, consultez [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Exemple

L’exemple suivant montre une implémentation d’interface. Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation. Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [interfaces](~/_csharplang/spec/interfaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md) et la spécification des fonctionnalités pour les [membres d’interface par défaut-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Types référence](reference-types.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
- [Utilisation de propriétés](../../programming-guide/classes-and-structs/using-properties.md)
- [Utilisation d'indexeurs](../../programming-guide/indexers/using-indexers.md)
