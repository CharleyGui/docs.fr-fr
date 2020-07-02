---
title: "Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles"
description: Découvrez comment réduire le scintillement des graphiques avec la double mise en mémoire tampon pour Windows Forms et utiliser les contrôles pour résoudre les problèmes de scintillement associés aux opérations de peinture.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618127"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="6b2fd-103">Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles</span><span class="sxs-lookup"><span data-stu-id="6b2fd-103">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="6b2fd-104">La double mise en mémoire tampon utilise une mémoire tampon pour résoudre les problèmes de scintillement associés aux opérations de dessin multiples.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-104">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="6b2fd-105">Quand la double mise en mémoire tampon est activée, toutes les opérations de dessin sont d’abord rendues dans une mémoire tampon au lieu de l’être sur la surface de dessin à l’écran.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-105">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="6b2fd-106">Une fois que toutes les opérations de dessin sont terminées, la mémoire tampon est copiée directement sur la surface de dessin qui y est associée.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-106">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="6b2fd-107">Étant donné qu’une seule opération Graphics est exécutée sur l’écran, le scintillement d’image associé aux opérations de dessin complexes est éliminé. Pour la plupart des applications, la double mise en mémoire tampon par défaut fournie par l' .NET Framework fournira les meilleurs résultats.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-107">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the .NET Framework will provide the best results.</span></span> <span data-ttu-id="6b2fd-108">Les contrôles de Windows Forms standard sont doubles mis en mémoire tampon par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-108">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="6b2fd-109">Vous pouvez activer la double mise en mémoire tampon par défaut dans vos formulaires et contrôles créés de deux manières.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-109">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="6b2fd-110">Vous pouvez affecter la valeur à la <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriété `true` ou appeler la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour affecter la valeur à l' <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true` .</span><span class="sxs-lookup"><span data-stu-id="6b2fd-110">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="6b2fd-111">Les deux méthodes activent la double mise en mémoire tampon par défaut pour votre formulaire ou contrôle et fournissent un rendu graphique sans scintillement.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-111">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="6b2fd-112">L’appel de la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode est recommandé uniquement pour les contrôles personnalisés pour lesquels vous avez écrit l’ensemble du code de rendu.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-112">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="6b2fd-113">Pour les scénarios de double mise en mémoire tampon plus avancés, tels que l’animation ou la gestion de mémoire avancée, vous pouvez implémenter votre propre logique de mise en mémoire tampon double.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-113">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="6b2fd-114">Pour plus d’informations, consultez [Comment : gérer manuellement des graphiques mis en mémoire tampon](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="6b2fd-114">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="6b2fd-115">Pour réduire le scintillement</span><span class="sxs-lookup"><span data-stu-id="6b2fd-115">To reduce flicker</span></span>  
  
- <span data-ttu-id="6b2fd-116">Attribuez à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6b2fd-116">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="6b2fd-117">\- ou -</span><span class="sxs-lookup"><span data-stu-id="6b2fd-117">\- or -</span></span>  
  
- <span data-ttu-id="6b2fd-118">Appelez la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour affecter la valeur <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> à l’indicateur `true` .</span><span class="sxs-lookup"><span data-stu-id="6b2fd-118">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="6b2fd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2fd-119">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="6b2fd-120">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="6b2fd-120">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="6b2fd-121">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b2fd-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
