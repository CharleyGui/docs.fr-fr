---
title: Comment combiner des délégués (délégués multicast)-Guide de programmation C#
description: Découvrez comment combiner des délégués pour créer des délégués multicast. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 3e86c8ed4b7b091ee8c75930d427c22aa5bc0c52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185949"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="41fc7-104">Comment combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="41fc7-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>

<span data-ttu-id="41fc7-105">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="41fc7-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="41fc7-106">Une propriété utile des objets [délégués](../../language-reference/builtin-types/reference-types.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="41fc7-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="41fc7-107">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="41fc7-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="41fc7-108">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="41fc7-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="41fc7-109">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="41fc7-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="41fc7-110">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="41fc7-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41fc7-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="41fc7-111">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="41fc7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41fc7-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="41fc7-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="41fc7-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41fc7-114">Événements</span><span class="sxs-lookup"><span data-stu-id="41fc7-114">Events</span></span>](../events/index.md)
