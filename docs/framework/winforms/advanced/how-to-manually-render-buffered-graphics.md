---
title: 'Procédure : afficher manuellement les graphismes mis en mémoire tampon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931839"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="920fc-102">Procédure : afficher manuellement les graphismes mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="920fc-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="920fc-103">Si vous gérez vos propres graphismes mis en mémoire tampon, vous devez pouvoir créer et restituer des mémoires tampon de graphiques.</span><span class="sxs-lookup"><span data-stu-id="920fc-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="920fc-104">Vous pouvez créer des instances de la classe <xref:System.Drawing.BufferedGraphics> associée aux surfaces de dessin sur votre écran en appelant la méthode <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A>.</span><span class="sxs-lookup"><span data-stu-id="920fc-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="920fc-105">Cette méthode crée une instance de <xref:System.Drawing.BufferedGraphics> associée à une surface de rendu particulière, comme un formulaire ou un contrôle.</span><span class="sxs-lookup"><span data-stu-id="920fc-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="920fc-106">Après avoir créé une instance de <xref:System.Drawing.BufferedGraphics>, vous pouvez dessiner des graphismes dans la mémoire tampon qu'elle représente par le biais de la propriété <xref:System.Drawing.BufferedGraphics.Graphics%2A>.</span><span class="sxs-lookup"><span data-stu-id="920fc-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="920fc-107">Après avoir effectué toutes les opérations graphiques, vous pouvez copier le contenu de la mémoire tampon à l'écran en appelant la méthode <xref:System.Drawing.BufferedGraphics.Render%2A>.</span><span class="sxs-lookup"><span data-stu-id="920fc-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="920fc-108">Si vous effectuez votre propre rendu, la consommation de mémoire augmentera, bien que cette augmentation puisse être très légère.</span><span class="sxs-lookup"><span data-stu-id="920fc-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="920fc-109">Pour afficher manuellement des graphismes mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="920fc-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="920fc-110">Obtenez une référence à une instance de la classe <xref:System.Drawing.BufferedGraphicsContext>.</span><span class="sxs-lookup"><span data-stu-id="920fc-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="920fc-111">Pour plus d’informations, consultez [Guide pratique pour Gérer manuellement les graphiques](how-to-manually-manage-buffered-graphics.md)mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="920fc-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="920fc-112">Créez une instance de la classe <xref:System.Drawing.BufferedGraphics> en appelant la méthode <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A>, comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="920fc-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="920fc-113">Dessinez des graphismes dans la mémoire tampon de graphiques en définissant la propriété <xref:System.Drawing.BufferedGraphics.Graphics%2A>.</span><span class="sxs-lookup"><span data-stu-id="920fc-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="920fc-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="920fc-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="920fc-115">Quand vous avez terminé toutes vos opérations de dessin dans la mémoire tampon de graphiques, appelez la méthode <xref:System.Drawing.BufferedGraphics.Render%2A> pour restituer la mémoire tampon, soit sur la surface de dessin associée à cette mémoire tampon, soit sur une surface de dessin spécifiée, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="920fc-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="920fc-116">Quand vous avez terminé d'afficher les graphismes, appelez la méthode `Dispose` sur l'instance de <xref:System.Drawing.BufferedGraphics> pour libérer les ressources système.</span><span class="sxs-lookup"><span data-stu-id="920fc-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="920fc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="920fc-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="920fc-118">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="920fc-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="920fc-119">Guide pratique : Gérer manuellement les graphiques mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="920fc-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
