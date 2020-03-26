---
title: Interfaces - Guide de programmation C#
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: bb1b812fdbf1d521ed3fd86e23f430bcd04d00f6
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249179"
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guide de programmation C#)

Une interface contient des définitions pour un groupe de fonctionnalités connexes qu’une [classe](../../language-reference/keywords/class.md) non abstraite ou une [struct doit](../../language-reference/builtin-types/struct.md) mettre en œuvre. Une interface `static` peut définir des méthodes, qui doivent avoir une implémentation. En commençant par le C 8.0, une interface peut définir une implémentation par défaut pour les membres. Une interface ne peut pas déclarer les données d’instance telles que les champs, les propriétés auto-mises en œuvre, ou des événements de propriété-comme.

En utilisant des interfaces, vous pouvez, par exemple, inclure le comportement de plusieurs sources dans une classe. Cette fonctionnalité est importante en C#, car le langage ne prend pas en charge l'héritage multiple de classes. De plus, vous devez utiliser une interface si vous voulez simuler l'héritage pour des structs, car ils ne peuvent en fait pas hériter d'un autre struct ou d'une autre classe.

Vous définissez une interface en utilisant le mot clé [d’interface](../../language-reference/keywords/interface.md) comme le montre l’exemple suivant.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Le nom d’une interface doit être un [nom d’identifiant](../inside-a-program/identifier-names.md)C valide . Par convention, les noms d’interface commencent par un `I` majuscule.

Toute classe ou tout struct qui implémentent l'interface <xref:System.IEquatable%601> doivent contenir une définition pour une méthode <xref:System.IEquatable%601.Equals%2A> qui correspond à la signature spécifiée par l'interface. Ainsi, vous pouvez compter sur une classe qui implémente `IEquatable<T>` pour contenir une méthode `Equals` avec laquelle une instance de la classe peut déterminer si elle est égale à une autre instance de la même classe.

La définition de `IEquatable<T>` ne fournit pas d'implémentation pour `Equals`. Une classe ou une struct peut implémenter plusieurs interfaces, mais une classe ne peut hériter qu’à partir d’une seule classe.

Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Les interfaces peuvent contenir des méthodes d’instance, des propriétés, des événements, des indexateurs ou toute combinaison de ces quatre types de membres. Les interfaces peuvent contenir des constructeurs, des champs, des constantes ou des opérateurs statiques. Pour obtenir des liens vers des exemples, consultez les [Sections connexes](./index.md#BKMK_RelatedSections). Une interface ne peut pas contenir des champs d’instance, des constructeurs d’instance ou des finalisateurs. Les membres de l’interface sont publics par défaut.

Pour implémenter un membre d'interface, le membre correspondant de la classe d'implémentation doit être public, non statique et porter le même nom et la même signature que le membre d'interface.

Lorsqu’une classe ou une structure implémente une interface, la classe ou la struct doit fournir une implémentation pour tous les membres que l’interface déclare, mais ne fournit pas une implémentation par défaut pour. Toutefois, si une classe de base implémente une interface, toute classe dérivée de la classe de base hérite de cette implémentation.

L'exemple suivant illustre une implémentation de l'interface <xref:System.IEquatable%601>. La classe d'implémentation, `Car`, doit fournir une implémentation de la méthode <xref:System.IEquatable%601.Equals%2A>.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Les propriétés et indexeurs d’une classe peuvent définir des accesseurs supplémentaires pour une propriété ou un indexeur qui est défini dans une interface. Par exemple, une interface peut déclarer une propriété qui a un accesseur [get](../../language-reference/keywords/get.md). La classe qui implémente l’interface peut déclarer la même propriété avec à la fois un accesseur `get` et un accesseur [set](../../language-reference/keywords/set.md). Toutefois, si la propriété ou l’indexeur utilisent une implémentation explicite, les accesseurs doivent correspondre. Pour plus d'informations sur l'implémentation explicite, consultez les pages [Implémentation d'interface explicite](explicit-interface-implementation.md) et [Propriétés d'interface](../classes-and-structs/interface-properties.md).

Les interfaces peuvent hériter d’une ou plusieurs interfaces. L’interface dérivée des membres à partir de ses interfaces de base. Une classe qui implémente une interface dérivée doit implémenter tous les membres de l’interface dérivée, y compris tous les membres des interfaces de base de l’interface dérivée. Cette classe peut être convertie implicitement en interface dérivée ou à l’une de ses interfaces de base. Une classe peut inclure une interface plusieurs fois par le biais de classes de base qu’elle hérite ou d’interfaces dont d’autres interfaces héritent. Toutefois, la classe peut fournir une implémentation d'une interface une seule fois et uniquement si la classe déclare l'interface dans le cadre de la définition de la classe (`class ClassName : InterfaceName`). Si l'interface est héritée car vous avez hérité d'une classe de base qui implémente l'interface, la classe de base fournit l'implémentation des membres de l'interface. Toutefois, la classe dérivée peut réimplémenter des membres d’interface virtuels au lieu d’utiliser l’implémentation héritée. Lorsque les interfaces déclarent une implémentation par défaut d’une méthode, toute mise en œuvre de cette interface hérite de cette implémentation. Les implémentations définies dans les interfaces sont virtuelles et la classe de mise en œuvre peut l’emporter sur cette implémentation.

Une classe de base peut également implémenter des membres d'interface à l'aide de membres virtuels. Dans ce cas, une classe dérivée peut modifier le comportement de l'interface en substituant les membres virtuels. Pour plus d'informations sur les membres virtuels, consultez la page [Polymorphisme](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Résumé des interfaces

Une interface possède les propriétés suivantes :

- Une interface est généralement comme une classe de base abstraite avec seulement des membres abstraits. Toute classe ou tout struct qui implémentent l'interface doivent implémenter tous ses membres. Optionnellement, une interface peut définir des implémentations par défaut pour une partie ou la totalité de ses membres.
- Une interface ne peut pas être instanciée directement. Ses membres sont implémentées par une classe ou un struct qui implémentent l'interface.
- Une classe ou un struct peuvent implémenter plusieurs interfaces. Une classe peut hériter d'une classe de base et également implémenter une ou plusieurs interfaces.

## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a>Sections connexes

- [Propriété d’une interface](../classes-and-structs/interface-properties.md)  
- [Indexeurs dans les interfaces](../indexers/indexers-in-interfaces.md)  
- [Comment implémenter des événements d’interface](../events/how-to-implement-interface-events.md)
- [Classes et Structs](../classes-and-structs/index.md)  
- [Héritage](../classes-and-structs/inheritance.md)  
- [Méthodes](../classes-and-structs/methods.md)  
- [Polymorphisme](../classes-and-structs/polymorphism.md)  
- [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Propriétés](../classes-and-structs/properties.md)  
- [Événements](../events/index.md)  
- [Indexeurs](../indexers/index.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Héritage](../classes-and-structs/inheritance.md)
- [Noms d’identificateurs](../inside-a-program/identifier-names.md)
