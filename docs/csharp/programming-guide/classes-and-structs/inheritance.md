---
title: Héritage - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 3c59741fa646111d27f6d1087a9275178c1a41a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705546"
---
# <a name="inheritance-c-programming-guide"></a>Héritage (Guide de programmation C#)

L’héritage, avec l’encapsulation et le polymorphisme, est l’une des trois principales caractéristiques de la programmation orientée objet. Il permet de créer de nouvelles classes qui réutilisent, étendent et modifient le comportement défini dans les autres classes. La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*. Une classe dérivée ne peut avoir qu’une seule classe de base directe. Toutefois, l’héritage est transitif. Si la classe C est dérivée de la classe B et la classe B dérivée de la classe A, la classe C hérite des membres déclarés dans la classe B et la classe A.  
  
> [!NOTE]
> Les structs ne prennent pas en charge l’héritage, mais ils peuvent implémenter les interfaces. Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).  
  
 D’un point de vue conceptuel, une classe dérivée est une spécialisation de la classe de base. Par exemple, si vous avez une classe de base `Animal`, vous pouvez avoir une classe dérivée nommée `Mammal` et une autre classe dérivée nommée `Reptile`. Un `Mammal` est un `Animal`, et un `Reptile` est un `Animal`, mais chaque classe dérivée représente des spécialisations différentes de la classe de base.  
  
 Quand vous définissez une classe à dériver d’une autre classe, la classe dérivée obtient implicitement tous les membres de la classe de base, à l’exception de ses constructeurs et de ses finaliseurs. La classe dérivée peut ainsi réutiliser le code de la classe de base sans avoir à le réimplémenter. Vous pouvez ajouter d’autres membres à la classe dérivée. De cette manière, la classe dérivée étend les fonctionnalités de la classe de base.  
  
 L’illustration suivante montre une classe `WorkItem` qui représente un élément de travail dans un processus métier. Comme toutes les classes, elle dérive de <xref:System.Object?displayProperty=nameWithType> et hérite de toutes ses méthodes. `WorkItem` ajoute cinq de ses propres membres. Cela inclut un constructeur, parce que les constructeurs ne sont pas hérités. La classe `ChangeRequest` hérite de `WorkItem` et représente un type particulier d’élément de travail. `ChangeRequest` ajoute deux membres supplémentaires aux membres qu’elle hérite de `WorkItem` et de <xref:System.Object>. Elle doit ajouter son propre constructeur et ajoute également `originalItemID`. La propriété `originalItemID` permet à l’instance `ChangeRequest` d’être associée au `WorkItem` d’origine auquel s’applique la demande de modification.  
  
 ![Diagramme illustrant l’héritage de classe](./media/inheritance/class-inheritance-diagram.png)  
  
 L’exemple suivant montre comment les relations de classe de l’illustration précédente sont exprimées en langage C#. L’exemple montre également comment `WorkItem` substitue la méthode virtuelle <xref:System.Object.ToString%2A?displayProperty=nameWithType>, et comment la classe `ChangeRequest` hérite de l’implémentation `WorkItem` de la méthode.  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>Méthodes abstraites et virtuelles  
 Lorsqu’une classe de base déclare une méthode comme étant [virtual](../../language-reference/keywords/virtual.md) (virtuelle), une classe dérivée peut [substituer](../../language-reference/keywords/override.md) la méthode avec sa propre implémentation. Si une classe de base déclare un membre comme étant [abstract](../../language-reference/keywords/abstract.md) (abstraite), la méthode doit être substituée dans toutes les classes non abstraites qui héritent directement de cette classe. Si une classe dérivée est abstraite, elle hérite des membres abstraits sans les implémenter. Les membres virtuels et abstraits sont la base du polymorphisme, qui est la deuxième caractéristique principale de la programmation orientée objet. Pour plus d’informations, consultez [Polymorphisme](./polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Classes de base abstraites  
 Pour empêcher l’instanciation directe, vous pouvez déclarer une classe comme étant [abstract](../../language-reference/keywords/abstract.md) à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md). Si vous procédez ainsi, la classe ne peut être utilisée que si une nouvelle classe en est dérivée. Une classe abstraite peut contenir une ou plusieurs signatures de méthode qui sont également déclarées comme abstraites. Ces signatures spécifient les paramètres et la valeur de retour, mais n’ont aucune implémentation (corps de méthode). Une classe abstraite ne doit pas nécessairement contenir des membres abstraits. Toutefois, si une classe contient un membre abstrait, elle doit être déclarée comme abstraite. Les classes dérivées qui ne sont pas abstraites doivent fournir une implémentation pour toutes les méthodes abstraites d’une classe de base abstraite. Pour plus d’informations, consultez [Classes abstract et sealed, et membres de classe](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Interfaces  
 Une *interface* est un type référence similaire à une classe de base abstraite qui se compose uniquement de membres abstraits. Quand une classe implémente une interface, elle doit fournir une implémentation pour tous les membres de l’interface. Une classe peut implémenter plusieurs interfaces, même si elle ne peut dériver que d’une seule classe de base directe.  
  
 Les interfaces sont utilisées pour définir des fonctions spécifiques pour les classes qui n’ont pas nécessairement de relation de type « est un ». Par exemple, l’interface <xref:System.IEquatable%601?displayProperty=nameWithType> peut être implémentée par toute classe ou tout struct qui doit permettre au code client de déterminer si deux objets du type sont équivalents (toutefois, le type définit l’équivalence). <xref:System.IEquatable%601> n’implique pas le même type de relation « est un » qui existe entre une classe de base et une classe dérivée (par exemple, un `Mammal` est un `Animal`). Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Empêcher une dérivation supplémentaire  
 Une classe peut empêcher d’autres classes d’hériter d’elle, ou de l’un de ses membres, en se déclarant elle-même ou en déclarant un membre comme [sealed](../../language-reference/keywords/sealed.md) (scellé). Pour plus d’informations, consultez [Classes abstract et sealed, et membres de classe](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Masquage des membres de la classe de base par une classe dérivée  
 Une classe dérivée peut masquer des membres de la classe de base en déclarant les membres à l’aide du même nom et de la même signature. Le modificateur [new](../../language-reference/keywords/new-modifier.md) peut être utilisé pour indiquer explicitement que le membre n’est pas censé substituer le membre de base. L’utilisation du modificateur [new](../../language-reference/keywords/new-modifier.md) n’est pas obligatoire. Toutefois, un avertissement du compilateur est généré si [new](../../language-reference/keywords/new-modifier.md) n’est pas utilisé. Pour plus d’informations, consultez [Gestion de version avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [classe](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
