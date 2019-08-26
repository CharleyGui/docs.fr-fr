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
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="a26d1-102">Procédure : Combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a26d1-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="a26d1-103">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="a26d1-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="a26d1-104">Une propriété utile des objets [délégués](../../language-reference/keywords/delegate.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="a26d1-104">A useful property of [delegate](../../language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="a26d1-105">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="a26d1-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="a26d1-106">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="a26d1-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="a26d1-107">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="a26d1-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="a26d1-108">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="a26d1-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a26d1-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="a26d1-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a26d1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a26d1-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="a26d1-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a26d1-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a26d1-112">Événements</span><span class="sxs-lookup"><span data-stu-id="a26d1-112">Events</span></span>](../events/index.md)
