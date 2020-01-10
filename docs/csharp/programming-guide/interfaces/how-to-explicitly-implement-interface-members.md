---
title: Comment implémenter de manière explicite des C# membres d’interface-Guide de programmation
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d006db2a7501a3273f5cd11e82bc589b21e1ce9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712089"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="fcb53-102">Comment implémenter de manière explicite desC# membres d’interface (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="fcb53-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="fcb53-103">Cet exemple déclare une [interface](../../language-reference/keywords/interface.md), `IDimensions` et une classe `Box`, qui implémente de manière explicite les membres d’interface `getLength` et `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="fcb53-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="fcb53-104">Les membres sont accessibles via l’instance d’interface `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="fcb53-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb53-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="fcb53-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fcb53-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fcb53-106">Robust Programming</span></span>  
  
- <span data-ttu-id="fcb53-107">Notez que les lignes suivantes de la méthode `Main` sont commentées car elles produiraient des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="fcb53-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="fcb53-108">Un membre d’interface qui est implémenté de façon explicite n’est pas accessible à partir d’une instance de [classe](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="fcb53-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="fcb53-109">Notez également que les lignes suivantes de la méthode `Main` impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d’une instance de l’interface :</span><span class="sxs-lookup"><span data-stu-id="fcb53-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb53-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcb53-110">See also</span></span>

- [<span data-ttu-id="fcb53-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fcb53-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fcb53-112">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="fcb53-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="fcb53-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="fcb53-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="fcb53-114">Comment implémenter explicitement des membres de deux interfaces</span><span class="sxs-lookup"><span data-stu-id="fcb53-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
