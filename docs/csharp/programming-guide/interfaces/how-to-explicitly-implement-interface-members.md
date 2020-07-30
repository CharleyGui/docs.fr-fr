---
title: Comment implémenter de manière explicite des membres d’interface-Guide de programmation C#
description: Découvrez comment implémenter de manière explicite des membres d’interface dans cet exemple C#. Les membres sont accessibles par le biais de l’instance d’interface.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303073"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="838d0-104">Comment implémenter de manière explicite des membres d’interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="838d0-104">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="838d0-105">Cet exemple déclare une [interface](../../language-reference/keywords/interface.md), `IDimensions` , et une classe, `Box` , qui implémente explicitement les membres d’interface `GetLength` et `GetWidth` .</span><span class="sxs-lookup"><span data-stu-id="838d0-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="838d0-106">Les membres sont accessibles via l’instance d’interface `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="838d0-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="838d0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="838d0-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="838d0-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="838d0-108">Robust Programming</span></span>  
  
- <span data-ttu-id="838d0-109">Notez que les lignes suivantes de la méthode `Main` sont commentées car elles produiraient des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="838d0-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="838d0-110">Un membre d’interface qui est implémenté de façon explicite n’est pas accessible à partir d’une instance de [classe](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="838d0-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="838d0-111">Notez également que les lignes suivantes de la méthode `Main` impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d’une instance de l’interface :</span><span class="sxs-lookup"><span data-stu-id="838d0-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="838d0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="838d0-112">See also</span></span>

- [<span data-ttu-id="838d0-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="838d0-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="838d0-114">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="838d0-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="838d0-115">Interfaces</span><span class="sxs-lookup"><span data-stu-id="838d0-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="838d0-116">Comment implémenter explicitement des membres de deux interfaces</span><span class="sxs-lookup"><span data-stu-id="838d0-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
