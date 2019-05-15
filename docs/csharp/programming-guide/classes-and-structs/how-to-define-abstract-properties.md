---
title: 'Procédure : Définir des propriétés abstraites - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: ef19b80e7f4c32830aabfcf1ad595348c2107228
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599989"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Procédure : Définir des propriétés abstraites (Guide de programmation C#)
L’exemple suivant montre comment définir des propriétés [abstract](../../../csharp/language-reference/keywords/abstract.md). Une déclaration de propriété abstraite ne fournit pas une implémentation des accesseurs de propriété ; elle déclare que la classe prend en charge des propriétés, mais laisse l’implémentation de l’accesseur aux classes dérivées. L’exemple suivant montre comment implémenter les propriétés abstraites héritées d’une classe de base.  
  
 Cet exemple se compose de trois fichiers, chacun étant compilé individuellement, et l’assembly obtenu est référencé par la compilation suivante :  
  
- abstractshape.cs : classe `Shape` qui contient une propriété `Area` abstraite.  
  
- shapes.cs : sous-classes de la classe `Shape`.  
  
- shapetest.cs : programme de test destiné à afficher les zones de certains objets dérivés de `Shape`.  
  
 Pour compiler l’exemple, utilisez la commande suivante :  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Cette commande crée le fichier exécutable shapetest.exe.  
  
## <a name="example"></a>Exemple  
 Ce fichier déclare la classe `Shape` qui contient la propriété `Area` du type `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Les modificateurs sur la propriété sont placés sur la déclaration de propriété proprement dite. Par exemple :  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Quand vous déclarez une propriété abstraite (telle que `Area` dans cet exemple), vous indiquez simplement quels les accesseurs de propriété sont disponibles, mais vous ne les implémentez pas. Dans cet exemple, seul un accesseur [get](../../../csharp/language-reference/keywords/get.md) est disponible, donc la propriété est en lecture seule.  
  
## <a name="example"></a>Exemple  
 Le code suivant présente trois sous-classes de `Shape` et indique comment elles substituent la propriété `Area` pour fournir leur propre implémentation.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Exemple  
 Le code suivant montre un programme de test qui crée un certain nombre d’objets dérivés de `Shape` et imprime les zones correspondantes.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
