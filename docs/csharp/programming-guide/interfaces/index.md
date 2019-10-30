---
title: Interfaces - Guide de programmation C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 950a74dd663249b2a59bf746d02b5992733d0ce9
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039339"
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guide de programmation C#)

Une interface contient des définitions pour un groupe de fonctionnalités connexes qu’une [classe](../../language-reference/keywords/class.md) non abstraite ou un [struct](../../language-reference/keywords/struct.md) doit implémenter.
  
En utilisant des interfaces, vous pouvez, par exemple, inclure le comportement de plusieurs sources dans une classe. Cette fonctionnalité est importante en C#, car le langage ne prend pas en charge l'héritage multiple de classes. De plus, vous devez utiliser une interface si vous voulez simuler l'héritage pour des structs, car ils ne peuvent en fait pas hériter d'un autre struct ou d'une autre classe.  
  
Vous définissez une interface à l'aide du mot clé [interface](../../language-reference/keywords/interface.md), comme le montre l’exemple suivant.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Le nom du struct doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide. Par convention, les noms d’interface commencent par un `I` majuscule.

Toute classe ou tout struct qui implémentent l'interface <xref:System.IEquatable%601> doivent contenir une définition pour une méthode <xref:System.IEquatable%601.Equals%2A> qui correspond à la signature spécifiée par l'interface. Ainsi, vous pouvez compter sur une classe qui implémente `IEquatable<T>` pour contenir une méthode `Equals` avec laquelle une instance de la classe peut déterminer si elle est égale à une autre instance de la même classe.  
  
La définition de `IEquatable<T>` ne fournit pas d'implémentation pour `Equals`. Une classe ou un struct peut implémenter plusieurs interfaces, mais une classe peut uniquement hériter d’une classe unique.
  
Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Les interfaces peuvent contenir des méthodes, propriétés, événements, indexeurs ou toute combinaison de ces quatre types de membres. Pour obtenir des liens vers des exemples, consultez les [Sections connexes](./index.md#BKMK_RelatedSections). Une interface ne peut pas contenir de constantes, champs, opérateurs, constructeurs d'instance, finaliseurs ou types. Les membres d’interface sont automatiquement publics et ils ne peuvent pas inclure de modificateurs d’accès. Les membres ne peuvent pas non plus être [statiques](../../language-reference/keywords/static.md).  
  
Pour implémenter un membre d'interface, le membre correspondant de la classe d'implémentation doit être public, non statique et porter le même nom et la même signature que le membre d'interface.  
  
Quand une classe ou un struct implémentent une interface, la classe ou le struct doivent fournir une implémentation pour tous les membres que l'interface définit. L'interface elle-même n'offre aucune fonctionnalité dont une classe ou un struct peuvent hériter de la manière qu'ils peuvent hériter d'une fonctionnalité de classe de base. Toutefois, si une classe de base implémente une interface, toute classe dérivée de la classe de base hérite de cette implémentation.  
  
L'exemple suivant illustre une implémentation de l'interface <xref:System.IEquatable%601>. La classe d'implémentation, `Car`, doit fournir une implémentation de la méthode <xref:System.IEquatable%601.Equals%2A>.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Les propriétés et indexeurs d’une classe peuvent définir des accesseurs supplémentaires pour une propriété ou un indexeur qui est défini dans une interface. Par exemple, une interface peut déclarer une propriété qui a un accesseur [get](../../language-reference/keywords/get.md). La classe qui implémente l’interface peut déclarer la même propriété avec à la fois un accesseur `get` et un accesseur [set](../../language-reference/keywords/set.md). Toutefois, si la propriété ou l’indexeur utilisent une implémentation explicite, les accesseurs doivent correspondre. Pour plus d'informations sur l'implémentation explicite, consultez les pages [Implémentation d'interface explicite](explicit-interface-implementation.md) et [Propriétés d'interface](../classes-and-structs/interface-properties.md).  

Les interfaces peuvent hériter d’autres interfaces. Une classe peut inclure une interface plusieurs fois par le biais de classes de base qu’elle hérite ou d’interfaces dont d’autres interfaces héritent. Toutefois, la classe peut fournir une implémentation d'une interface une seule fois et uniquement si la classe déclare l'interface dans le cadre de la définition de la classe (`class ClassName : InterfaceName`). Si l'interface est héritée car vous avez hérité d'une classe de base qui implémente l'interface, la classe de base fournit l'implémentation des membres de l'interface. Toutefois, la classe dérivée peut réimplémenter des membres d’interface virtuels au lieu d’utiliser l’implémentation héritée.  
  
Une classe de base peut également implémenter des membres d'interface à l'aide de membres virtuels. Dans ce cas, une classe dérivée peut modifier le comportement de l'interface en substituant les membres virtuels. Pour plus d'informations sur les membres virtuels, consultez la page [Polymorphisme](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Résumé des interfaces

Une interface possède les propriétés suivantes :  

- Une interface est comme une classe de base abstraite avec uniquement des membres abstraits. Toute classe ou tout struct qui implémentent l'interface doivent implémenter tous ses membres.
- Une interface ne peut pas être instanciée directement. Ses membres sont implémentées par une classe ou un struct qui implémentent l'interface.
- Les interfaces peuvent contenir des événements, des indexeurs, des méthodes et des propriétés.
- Les interfaces ne contiennent aucune implémentation de méthodes.
- Une classe ou un struct peuvent implémenter plusieurs interfaces. Une classe peut hériter d'une classe de base et également implémenter une ou plusieurs interfaces.

## <a name="in-this-section"></a>Dans cette section

[Implémentation d’interface explicite](explicit-interface-implementation.md)  
 Explique comment créer un membre de classe spécifique à une interface.  
  
 [Comment : implémenter de manière explicite des membres d’interface](how-to-explicitly-implement-interface-members.md)  
 Fournit un exemple montrant comment implémenter explicitement des membres d'interface.  
  
 [Comment : implémenter de manière explicite des membres de deux interfaces](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Fournit un exemple montrant comment implémenter explicitement des membres d'interface avec héritage.  
  
## <a name="BKMK_RelatedSections"></a> Sections connexes

- [Propriétés de l’interface](../classes-and-structs/interface-properties.md)  
- [Indexeurs dans les interfaces](../indexers/indexers-in-interfaces.md)  
- [Guide pratique d’implémentation d’événements d’interface](../events/how-to-implement-interface-events.md)  
- [Classes et structs](../classes-and-structs/index.md)  
- [Héritage](../classes-and-structs/inheritance.md)  
- [Méthodes](../classes-and-structs/methods.md)  
- [Polymorphisme](../classes-and-structs/polymorphism.md)  
- [Classes abstract et sealed et membres de classe](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Propriétés](../classes-and-structs/properties.md)  
- [Événements](../events/index.md)  
- [Indexeurs](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>chapitre proposé

[Interfaces](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) dans [Learning C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Héritage](../classes-and-structs/inheritance.md)
- [Noms d’identificateur](../inside-a-program/identifier-names.md)
