---
title: Classes abstract et sealed et membres de classe - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715007"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Classes abstract et sealed et membres de classe (Guide de programmation C#)
Le mot clé [abstract](../../language-reference/keywords/abstract.md) vous permet de créer des classes et des membres de [class](../../language-reference/keywords/class.md) qui sont incomplets et doivent être implémentés dans une classe dérivée.  
  
 Le mot clé [sealed](../../language-reference/keywords/sealed.md) vous permet d’empêcher l’héritage d’une classe ou de certains membres de classe qui étaient précédemment marqués comme [virtual](../../language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Classes abstraites et membres de classe  
 Les classes peuvent être déclarées comme abstraites en plaçant le mot clé `abstract` avant la définition de classe. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Une classe abstraite ne peut pas être instanciée. Le but d'une classe abstraite est de fournir une définition commune d'une classe de base pouvant être partagée par plusieurs classes dérivées. Par exemple, une bibliothèque de classes peut définir une classe abstraite qui est utilisée comme un paramètre pour beaucoup de ses fonctions, et exiger des programmeurs qui l'utilisent de fournir leur propre implémentation de la classe en créant une classe dérivée.  
  
 Les classes abstraites peuvent également définir des méthodes abstraites. Pour ce faire, ajoutez le mot clé `abstract` avant le type de retour de la méthode. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Les méthodes abstraites n'ont pas d'implémentation. Ainsi, la définition de la méthode est suivie d'un point-virgule au lieu d'un bloc de méthode normal. Les classes dérivées de la classe abstraite doivent implémenter toutes les méthodes abstraites. Lorsqu'une classe abstraite hérite d'une méthode virtuelle d'une classe de base, la classe abstraite peut substituer la méthode virtuelle par une méthode abstraite. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Si une méthode `virtual` est déclarée `abstract`, elle demeure virtuelle pour toutes les classes qui héritent de la classe abstraite. Une classe qui hérite d’une méthode abstraite ne peut pas accéder à l’implémentation d’origine de la méthode. Dans l’exemple précédent, `DoWork` sur la classe F ne peut pas appeler `DoWork` sur la classe D. De cette manière, une classe abstraite peut forcer les classes dérivées à fournir de nouvelles implémentations de méthode pour les méthodes virtuelles.  
  
## <a name="sealed-classes-and-class-members"></a>Classes sealed et membres de classe  
 Les classes peuvent être déclarées comme [sealed](../../language-reference/keywords/sealed.md) en plaçant le mot clé `sealed` avant la définition de classe. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Une classe sealed ne peut pas être utilisée comme une classe de base. Pour cette raison, elle ne peut pas également être une classe abstraite. Les classes sealed empêchent la dérivation. Étant donné qu'elles ne peuvent pas être utilisées comme une classe de base, quelques optimisations au moment de l'exécution permettent d'accélérer un peu les appels aux membres des classes sealed.  
  
 Une méthode, un indexeur, une propriété ou un événement sur une classe dérivée qui substitue un membre virtuel de la classe de base peut déclarer ce membre comme sealed. Cela nie l'aspect virtuel du membre pour toute classe dérivée ultérieure. Pour ce faire, mettez le mot clé `sealed` avant le mot clé [override](../../language-reference/keywords/override.md) dans la déclaration de membre de classe. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Héritage](./inheritance.md)
- [Méthodes](./methods.md)
- [Champs](./fields.md)
- [Comment définir les propriétés abstraites](./how-to-define-abstract-properties.md)
