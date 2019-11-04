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
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="651ef-102">Comment : combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="651ef-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="651ef-103">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="651ef-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="651ef-104">Une propriété utile des objets [délégués](../../language-reference/builtin-types/reference-types.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="651ef-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="651ef-105">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="651ef-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="651ef-106">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="651ef-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="651ef-107">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="651ef-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="651ef-108">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="651ef-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="651ef-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="651ef-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="651ef-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="651ef-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="651ef-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="651ef-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="651ef-112">Événements</span><span class="sxs-lookup"><span data-stu-id="651ef-112">Events</span></span>](../events/index.md)
