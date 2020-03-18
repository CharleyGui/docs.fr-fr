---
title: Héritage - Guide de programmation C#
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 448b1695a4afc50f4afa20383e5fda280b9f12e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626657"
---
# <a name="inheritance-c-programming-guide"></a>Héritage (Guide de programmation C#)

L’héritage, avec l’encapsulation et le polymorphisme, est l’une des trois principales caractéristiques de la programmation orientée objet. L’héritage vous permet de créer de nouvelles classes qui réutilisent, prolongent et modifient le comportement défini dans d’autres classes. La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*. Une classe dérivée ne peut avoir qu’une seule classe de base directe. Toutefois, l’héritage est transitif. Si `ClassC` est `ClassB`dérivé `ClassB` de , `ClassA` `ClassC` et est dérivé `ClassB` de `ClassA`, hérite des membres déclarés dans et .

> [!NOTE]
> Les structs ne prennent pas en charge l’héritage, mais ils peuvent implémenter les interfaces. Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).

D’un point de vue conceptuel, une classe dérivée est une spécialisation de la classe de base. Par exemple, si vous avez une classe de base `Animal`, vous pouvez avoir une classe dérivée nommée `Mammal` et une autre classe dérivée nommée `Reptile`. Un `Mammal` est un `Animal`, et un `Reptile` est un `Animal`, mais chaque classe dérivée représente des spécialisations différentes de la classe de base.

Les déclarations d’interface peuvent définir une implémentation par défaut pour ses membres. Ces implémentations sont héritées par des interfaces dérivées, et par des classes qui implémentent ces interfaces. Pour plus d’informations sur les méthodes d’interface par défaut, voir l’article sur [les interfaces](../../language-reference/keywords/interface.md) dans la section de référence linguistique.

Quand vous définissez une classe à dériver d’une autre classe, la classe dérivée obtient implicitement tous les membres de la classe de base, à l’exception de ses constructeurs et de ses finaliseurs. La classe dérivée réutilise le code dans la classe de base sans avoir à le réimplanter. Vous pouvez ajouter plus de membres dans la classe dérivée. La classe dérivée étend la fonctionnalité de la classe de base.

L’illustration suivante montre une classe `WorkItem` qui représente un élément de travail dans un processus métier. Comme toutes les classes, elle dérive de <xref:System.Object?displayProperty=nameWithType> et hérite de toutes ses méthodes. `WorkItem` ajoute cinq de ses propres membres. Ces membres comprennent un constructeur, parce que les constructeurs ne sont pas hérités. La classe `ChangeRequest` hérite de `WorkItem` et représente un type particulier d’élément de travail. `ChangeRequest` ajoute deux membres supplémentaires aux membres qu’elle hérite de `WorkItem` et de <xref:System.Object>. Elle doit ajouter son propre constructeur et ajoute également `originalItemID`. La propriété `originalItemID` permet à l’instance `ChangeRequest` d’être associée au `WorkItem` d’origine auquel s’applique la demande de modification.

![Diagramme illustrant l’héritage de classe](./media/inheritance/class-inheritance-diagram.png)

L’exemple suivant montre comment les relations de classe de l’illustration précédente sont exprimées en langage C#. L’exemple montre également comment `WorkItem` substitue la méthode virtuelle <xref:System.Object.ToString%2A?displayProperty=nameWithType>, et comment la classe `ChangeRequest` hérite de l’implémentation `WorkItem` de la méthode. Le premier bloc définit les classes :

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Ce prochain bloc montre comment utiliser la base et les classes dérivées:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Méthodes abstraites et virtuelles

Lorsqu’une classe de base [`virtual`](../../language-reference/keywords/virtual.md)déclare une [`override`](../../language-reference/keywords/override.md) méthode comme , une classe dérivée peut la méthode avec sa propre mise en œuvre. Si une classe de base [`abstract`](../../language-reference/keywords/abstract.md)déclare un membre comme , cette méthode doit être remplacée dans toute classe non abstraite qui hérite directement de cette classe. Si une classe dérivée est abstraite, elle hérite des membres abstraits sans les implémenter. Les membres virtuels et abstraits sont la base du polymorphisme, qui est la deuxième caractéristique principale de la programmation orientée objet. Pour plus d’informations, consultez [Polymorphisme](./polymorphism.md).

## <a name="abstract-base-classes"></a>Classes de base abstraites

Pour empêcher l’instanciation directe, vous pouvez déclarer une classe comme étant [abstract](../../language-reference/keywords/abstract.md) à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md). Une classe abstraite ne peut être utilisée que si une nouvelle classe en tire. Une classe abstraite peut contenir une ou plusieurs signatures de méthode qui sont également déclarées comme abstraites. Ces signatures spécifient les paramètres et la valeur de retour, mais n’ont aucune implémentation (corps de méthode). Une classe abstraite n’a pas à contenir de membres abstraits; toutefois, si une classe contient un membre abstrait, la classe elle-même doit être déclarée abstraite. Les classes dérivées qui ne sont pas abstraites elles-mêmes doivent fournir la mise en œuvre pour toutes les méthodes abstraites d’une classe de base abstraite. Pour plus d’informations, consultez [Classes abstract et sealed, et membres de classe](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Interfaces

Une *interface* est un type de référence qui définit un ensemble de membres. Toutes les classes et les structs qui implémentent cette interface doivent mettre en œuvre cet ensemble de membres. Une interface peut définir une implémentation par défaut pour l’un ou l’autre de ces membres. Une classe peut implémenter plusieurs interfaces, même si elle ne peut dériver que d’une seule classe de base directe.

Les interfaces sont utilisées pour définir des capacités spécifiques pour les classes qui n’ont pas nécessairement une relation « est ». Par exemple, <xref:System.IEquatable%601?displayProperty=nameWithType> l’interface peut être implémentée par n’importe quelle classe ou struct pour déterminer si deux objets du type sont équivalents (toutefois le type définit l’équivalence). <xref:System.IEquatable%601>n’implique pas le même type de "est une" relation qui existe entre une `Mammal` classe `Animal`de base et une classe dérivée (par exemple, a est un ). Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Prévenir d’autres dérivations  

Une classe peut empêcher d’autres classes d’en hériter, ou de [`sealed`](../../language-reference/keywords/sealed.md)l’un de ses membres, en se déclarant lui-même ou le membre comme . Pour plus d’informations, consultez [Classes abstract et sealed, et membres de classe](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Se cacher de classe dérivée des membres de la classe de base  

Une classe dérivée peut masquer des membres de la classe de base en déclarant les membres à l’aide du même nom et de la même signature. Le [`new`](../../language-reference/keywords/new-modifier.md) modificateur peut être utilisé pour indiquer explicitement que le membre n’est pas destiné à être une dérogation au membre de base. L’utilisation [`new`](../../language-reference/keywords/new-modifier.md) de n’est pas nécessaire, mais un [`new`](../../language-reference/keywords/new-modifier.md) avertissement compilateur sera généré si n’est pas utilisé. Pour plus d’informations, consultez [Gestion de version avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Classe](../../language-reference/keywords/class.md)
