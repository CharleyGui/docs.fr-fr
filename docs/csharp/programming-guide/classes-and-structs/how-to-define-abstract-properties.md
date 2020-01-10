---
title: Comment définir des propriétés abstraites C# -Guide de programmation
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705611"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Comment définir des propriétés abstraitesC# (Guide de programmation)
L’exemple suivant montre comment définir des propriétés [abstract](../../language-reference/keywords/abstract.md). Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées. L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.  
  
 Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :  
  
- abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.  
  
- shapes.cs : sous-classes de la classe `Shape`.  
  
- shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.  
  
 Pour compiler l’exemple, utilisez la commande suivante :  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Cette commande crée le fichier exécutable shapetest.exe.  
  
## <a name="example"></a>Exemple  
 Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite. Par exemple :  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas. Dans cet exemple, seul un accesseur [get](../../language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.  
  
## <a name="example"></a>Exemple  
 Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Exemple  
 Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Classes abstract et sealed et membres de classe](./abstract-and-sealed-classes-and-class-members.md)
- [Propriétés](./properties.md)
