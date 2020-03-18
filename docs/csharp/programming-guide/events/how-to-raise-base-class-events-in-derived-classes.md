---
title: Comment élever les événements de la classe de base dans les classes dérivées - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712323"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Comment élever les événements de la classe de base dans les classes dérivées (Guide de programmation C)
L’exemple suivant montre la méthode standard employée pour déclarer des événements dans une classe de base pour qu’ils puissent être déclenchés à partir de classes dérivées. Ce modèle est largement utilisé dans les classes Windows Forms de la bibliothèque de classes .NET Framework.  
  
 Lorsque vous créez une classe qui peut être utilisée comme classe de base pour d’autres classes, tenez compte du fait que les événements constituent un type spécial de délégué qui ne peut être appelé qu’à partir de la classe qui les a déclarés. Les classes dérivées ne peuvent pas appeler directement les événements qui sont déclarés dans la classe de base. Même si vous pouvez avoir besoin d’un événement qui ne peut être déclenché que par la classe de base, la plupart du temps, vous devez permettre à la classe dérivée d’appeler les événements de la classe de base. Pour ce faire, vous pouvez créer une méthode d’appel protégée dans la classe de base qui encapsule l’événement. En appelant ou en substituant cette méthode d’appel, les classes dérivées peuvent appeler indirectement l’événement.  
  
> [!NOTE]
> Ne déclarez pas les événements virtuels dans une classe de base et substituez-les dans une classe dérivée. Le compilateur C# ne gère pas correctement ce type d’événement et il n’est pas possible de prévoir si un abonné de l’événement dérivé s’abonnera à l’événement de classe de base.  
  
## <a name="example"></a> Exemple  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Événements](./index.md)
- [Délégués](../delegates/index.md)
- [Modificateurs d’accès](../classes-and-structs/access-modifiers.md)
- [Création de gestionnaires d’événements dans Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
