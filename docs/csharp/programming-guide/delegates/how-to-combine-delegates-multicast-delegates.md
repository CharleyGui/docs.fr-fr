---
title: 'Procédure : Combiner des délégués (délégués multicast) - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590666"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Procédure : Combiner des délégués (délégués multicast) (Guide de programmation C#)
Cet exemple explique comment créer des délégués multicast. Une propriété utile des objets [délégués](../../language-reference/keywords/delegate.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`. Le délégué multicast contient une liste des délégués assignés. Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre. Seuls des délégués de même type peuvent être combinés.  
  
 Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.  
  
## <a name="example"></a>Exemples  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.MulticastDelegate>
- [Guide de programmation C#](../index.md)
- [Événements](../events/index.md)
