---
title: Comment implémenter de manière explicite des membres d’interface-Guide de programmation C#
description: Découvrez comment implémenter de manière explicite des membres d’interface dans cet exemple C#. Les membres sont accessibles par le biais de l’instance d’interface.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: a9c019cdcf6e229199d980a2d1913df7c72a2169
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157393"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Comment implémenter de manière explicite des membres d’interface (Guide de programmation C#)

Cet exemple déclare une [interface](../../language-reference/keywords/interface.md), `IDimensions` , et une classe, `Box` , qui implémente explicitement les membres d’interface `GetLength` et `GetWidth` . Les membres sont accessibles via l’instance d’interface `dimensions`.  
  
## <a name="example"></a>Exemple  

 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
- Notez que les lignes suivantes de la méthode `Main` sont commentées car elles produiraient des erreurs de compilation. Un membre d’interface qui est implémenté de façon explicite n’est pas accessible à partir d’une instance de [classe](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Notez également que les lignes suivantes de la méthode `Main` impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d’une instance de l’interface :  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Comment implémenter explicitement des membres de deux interfaces](./how-to-explicitly-implement-members-of-two-interfaces.md)
