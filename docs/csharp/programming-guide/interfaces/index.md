---
title: Interfaces - Guide de programmation C#
description: Une interface en C# contient des définitions pour un groupe de fonctionnalités connexes qu’une classe non abstraite ou un struct doit implémenter.
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 4485a9f8e3581aa80ed65221258dc40310b3a695
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303047"
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guide de programmation C#)

Une interface contient des définitions pour un groupe de fonctionnalités connexes qu’une [classe](../../language-reference/keywords/class.md) non abstraite ou un [struct](../../language-reference/builtin-types/struct.md) doit implémenter. Une interface peut définir des `static` méthodes, qui doivent avoir une implémentation. À compter de C# 8,0, une interface peut définir une implémentation par défaut pour les membres. Une interface ne peut pas déclarer des données d’instance, telles que des champs, des propriétés implémentées automatiquement ou des événements de type propriété.

En utilisant des interfaces, vous pouvez, par exemple, inclure le comportement de plusieurs sources dans une classe. Cette fonctionnalité est importante en C#, car le langage ne prend pas en charge l'héritage multiple de classes. De plus, vous devez utiliser une interface si vous voulez simuler l'héritage pour des structs, car ils ne peuvent en fait pas hériter d'un autre struct ou d'une autre classe.

Vous définissez une interface à l’aide du mot clé [interface](../../language-reference/keywords/interface.md) , comme le montre l’exemple suivant.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Le nom d’une interface doit être un nom d' [identificateur](../inside-a-program/identifier-names.md)C# valide. Par convention, les noms d’interface commencent par un `I` majuscule.

Toute classe ou tout struct qui implémentent l'interface <xref:System.IEquatable%601> doivent contenir une définition pour une méthode <xref:System.IEquatable%601.Equals%2A> qui correspond à la signature spécifiée par l'interface. Ainsi, vous pouvez compter sur une classe qui implémente `IEquatable<T>` pour contenir une méthode `Equals` avec laquelle une instance de la classe peut déterminer si elle est égale à une autre instance de la même classe.

La définition de `IEquatable<T>` ne fournit pas d’implémentation pour `Equals` . Une classe ou un struct peut implémenter plusieurs interfaces, mais une classe peut uniquement hériter d’une classe unique.

Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Les interfaces peuvent contenir des méthodes d’instance, des propriétés, des événements, des indexeurs ou toute combinaison de ces quatre types de membres. Les interfaces peuvent contenir des constructeurs statiques, des champs, des constantes ou des opérateurs. Pour obtenir des liens vers des exemples, consultez les [Sections connexes](./index.md#BKMK_RelatedSections). Une interface ne peut pas contenir de champs d’instance, de constructeurs d’instance ou de finaliseurs. Les membres d’interface sont publics par défaut.

Pour implémenter un membre d'interface, le membre correspondant de la classe d'implémentation doit être public, non statique et porter le même nom et la même signature que le membre d'interface.

Quand une classe ou un struct implémente une interface, la classe ou le struct doivent fournir une implémentation pour tous les membres que l’interface déclare, mais ne fournit pas d’implémentation par défaut pour. Toutefois, si une classe de base implémente une interface, toute classe dérivée de la classe de base hérite de cette implémentation.

L'exemple suivant illustre une implémentation de l'interface <xref:System.IEquatable%601>. La classe d'implémentation, `Car`, doit fournir une implémentation de la méthode <xref:System.IEquatable%601.Equals%2A>.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Les propriétés et indexeurs d’une classe peuvent définir des accesseurs supplémentaires pour une propriété ou un indexeur qui est défini dans une interface. Par exemple, une interface peut déclarer une propriété qui a un accesseur [get](../../language-reference/keywords/get.md). La classe qui implémente l’interface peut déclarer la même propriété avec à la fois un accesseur `get` et un accesseur [set](../../language-reference/keywords/set.md). Toutefois, si la propriété ou l’indexeur utilisent une implémentation explicite, les accesseurs doivent correspondre. Pour plus d'informations sur l'implémentation explicite, consultez les pages [Implémentation d'interface explicite](explicit-interface-implementation.md) et [Propriétés d'interface](../classes-and-structs/interface-properties.md).

Les interfaces peuvent hériter d’une ou de plusieurs interfaces. L’interface dérivée hérite des membres de ses interfaces de base. Une classe qui implémente une interface dérivée doit implémenter tous les membres de l’interface dérivée, y compris tous les membres des interfaces de base de l’interface dérivée. Cette classe peut être implicitement convertie en une interface dérivée ou l’une de ses interfaces de base. Une classe peut inclure une interface plusieurs fois par le biais de classes de base qu’elle hérite ou d’interfaces dont d’autres interfaces héritent. Toutefois, la classe peut fournir une implémentation d'une interface une seule fois et uniquement si la classe déclare l'interface dans le cadre de la définition de la classe (`class ClassName : InterfaceName`). Si l'interface est héritée car vous avez hérité d'une classe de base qui implémente l'interface, la classe de base fournit l'implémentation des membres de l'interface. Toutefois, la classe dérivée peut réimplémenter des membres d’interface virtuels au lieu d’utiliser l’implémentation héritée. Quand les interfaces déclarent une implémentation par défaut d’une méthode, toute classe qui implémente cette interface hérite de cette implémentation. Les implémentations définies dans les interfaces sont virtuelles et la classe d’implémentation peut remplacer cette implémentation.

Une classe de base peut également implémenter des membres d'interface à l'aide de membres virtuels. Dans ce cas, une classe dérivée peut modifier le comportement de l'interface en substituant les membres virtuels. Pour plus d'informations sur les membres virtuels, consultez la page [Polymorphisme](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Résumé des interfaces

Une interface possède les propriétés suivantes :

- Une interface est généralement similaire à une classe de base abstraite avec des membres abstraits uniquement. Toute classe ou tout struct qui implémentent l'interface doivent implémenter tous ses membres. Éventuellement, une interface peut définir des implémentations par défaut pour tout ou partie de ses membres. Pour plus d’informations, consultez [méthodes d’interface par défaut](../../tutorials/default-interface-methods-versions.md).
- Une interface ne peut pas être instanciée directement. Ses membres sont implémentées par une classe ou un struct qui implémentent l'interface.
- Une classe ou un struct peuvent implémenter plusieurs interfaces. Une classe peut hériter d'une classe de base et également implémenter une ou plusieurs interfaces.

## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a>Sections connexes

- [Propriétés de l’interface](../classes-and-structs/interface-properties.md)  
- [Indexeurs dans les interfaces](../indexers/indexers-in-interfaces.md)  
- [Comment implémenter des événements d’interface](../events/how-to-implement-interface-events.md)
- [Classes et structs](../classes-and-structs/index.md)  
- [Héritage](../classes-and-structs/inheritance.md)  
- [Interfaces](../../language-reference/keywords/interface.md)
- [Méthodes](../classes-and-structs/methods.md)  
- [Polymorphisme](../classes-and-structs/polymorphism.md)  
- [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Propriétés](../classes-and-structs/properties.md)  
- [Événements](../events/index.md)  
- [Indexeurs](../indexers/index.md)
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Héritage](../classes-and-structs/inheritance.md)
- [Noms d’identificateurs](../inside-a-program/identifier-names.md)
