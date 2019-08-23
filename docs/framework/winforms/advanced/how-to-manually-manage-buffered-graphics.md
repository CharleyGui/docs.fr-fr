---
title: 'Procédure : gérer manuellement les graphismes mis en mémoire tampon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968603"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="5ca9d-102">Procédure : gérer manuellement les graphismes mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="5ca9d-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="5ca9d-103">Pour les scénarios de double mise en mémoire tampon plus avancés, vous pouvez utiliser les classes .NET Framework pour implémenter votre propre logique de double mise en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-103">For more advanced double buffering scenarios, you can use the .NET Framework classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="5ca9d-104">La classe responsable de l’allocation et de la gestion de mémoires tampons de graphiques individuelles est la <xref:System.Drawing.BufferedGraphicsContext> classe.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="5ca9d-105">Chaque application possède sa propre valeur <xref:System.Drawing.BufferedGraphicsContext> par défaut qui gère l’ensemble de la double mise en mémoire tampon par défaut pour cette application.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="5ca9d-106">Vous pouvez récupérer une référence à cette instance en appelant <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="5ca9d-107">Pour obtenir une référence au BufferedGraphicsContext par défaut</span><span class="sxs-lookup"><span data-stu-id="5ca9d-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="5ca9d-108">Définissez la <xref:System.Drawing.BufferedGraphicsManager.Current%2A> propriété, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > <span data-ttu-id="5ca9d-109">Vous n’avez pas besoin d’appeler `Dispose` la méthode sur <xref:System.Drawing.BufferedGraphicsContext> la référence que vous recevez de <xref:System.Drawing.BufferedGraphicsManager> la classe.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="5ca9d-110">Le <xref:System.Drawing.BufferedGraphicsManager> gère l’ensemble de l’allocation et de la distribution <xref:System.Drawing.BufferedGraphicsContext> de la mémoire pour les instances par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="5ca9d-111">Pour les applications gourmandes en graphique, telles que l’animation, vous pouvez parfois améliorer les <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsContext> performances à l’aide d’un <xref:System.Drawing.BufferedGraphicsManager>dédié au lieu du fourni par le.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="5ca9d-112">Cela vous permet de créer et de gérer des mémoires tampons de graphiques individuellement, sans entraîner la surcharge de performances de la gestion de tous les autres graphiques mis en mémoire tampon associés à votre application, bien que la mémoire consommée par l’application soit supérieure.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="5ca9d-113">Pour créer un BufferedGraphicsContext dédié</span><span class="sxs-lookup"><span data-stu-id="5ca9d-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="5ca9d-114">Déclarez et créez une nouvelle instance de <xref:System.Drawing.BufferedGraphicsContext> la classe, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="5ca9d-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="5ca9d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca9d-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="5ca9d-116">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="5ca9d-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="5ca9d-117">Guide pratique : Rendu manuel des graphiques mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="5ca9d-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
