---
title: Comment combiner les délégués (délégués multicast) - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705377"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="90f21-102">Comment combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="90f21-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="90f21-103">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="90f21-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="90f21-104">Une propriété utile des objets [délégués](../../language-reference/builtin-types/reference-types.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="90f21-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="90f21-105">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="90f21-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="90f21-106">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="90f21-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="90f21-107">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="90f21-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="90f21-108">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="90f21-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90f21-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="90f21-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="90f21-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90f21-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="90f21-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="90f21-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90f21-112">Événements</span><span class="sxs-lookup"><span data-stu-id="90f21-112">Events</span></span>](../events/index.md)
