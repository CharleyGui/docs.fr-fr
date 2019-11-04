---
title: 'Comment : combiner des délégués (délégués multicast)- C# Guide de programmation'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d7098bb5518b92b407f905ddabbfafdcb77536bf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423352"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Comment : combiner des délégués (délégués multicast) (Guide de programmation C#)
Cet exemple explique comment créer des délégués multicast. Une propriété utile des objets [délégués](../../language-reference/builtin-types/reference-types.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`. Le délégué multicast contient une liste des délégués assignés. Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre. Seuls des délégués de même type peuvent être combinés.  
  
 Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.MulticastDelegate>
- [Guide de programmation C#](../index.md)
- [Événements](../events/index.md)
