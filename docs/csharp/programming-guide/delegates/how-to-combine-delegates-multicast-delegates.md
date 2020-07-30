---
title: Comment combiner des délégués (délégués multicast)-Guide de programmation C#
description: Découvrez comment combiner des délégués pour créer des délégués multicast. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302735"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="e0715-104">Comment combiner des délégués (délégués multicast) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e0715-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="e0715-105">Cet exemple explique comment créer des délégués multicast.</span><span class="sxs-lookup"><span data-stu-id="e0715-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="e0715-106">Une propriété utile des objets [délégués](../../language-reference/builtin-types/reference-types.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="e0715-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="e0715-107">Le délégué multicast contient une liste des délégués assignés.</span><span class="sxs-lookup"><span data-stu-id="e0715-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="e0715-108">Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="e0715-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="e0715-109">Seuls des délégués de même type peuvent être combinés.</span><span class="sxs-lookup"><span data-stu-id="e0715-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="e0715-110">Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.</span><span class="sxs-lookup"><span data-stu-id="e0715-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0715-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0715-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e0715-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0715-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="e0715-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e0715-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e0715-114">Événements</span><span class="sxs-lookup"><span data-stu-id="e0715-114">Events</span></span>](../events/index.md)
