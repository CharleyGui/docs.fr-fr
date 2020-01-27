---
title: 'Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743408"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="a8102-102">Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8102-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="a8102-103">les contrôles <xref:System.Windows.Forms.ToolStrip> offrent un support facile pour les thèmes et les styles.</span><span class="sxs-lookup"><span data-stu-id="a8102-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="a8102-104">Vous pouvez obtenir une apparence et un comportement entièrement personnalisés (apparence) en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ou à la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> la valeur d’un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a8102-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="a8102-105">Vous pouvez assigner des convertisseurs à chaque <xref:System.Windows.Forms.ToolStrip>individuel, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>ou <xref:System.Windows.Forms.StatusStrip> contrôle, ou vous pouvez utiliser la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> pour affecter tous les objets en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8102-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8102-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> retourne <xref:System.Windows.Forms.ToolStripRenderMode.Custom> uniquement si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> n’est pas `null`.</span><span class="sxs-lookup"><span data-stu-id="a8102-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="a8102-107">Pour créer un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="a8102-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="a8102-108">Étendez la classe <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="a8102-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="a8102-109">Implémentez le rendu personnalisé souhaité en remplaçant *le approprié sur...*</span><span class="sxs-lookup"><span data-stu-id="a8102-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="a8102-110">Membres</span><span class="sxs-lookup"><span data-stu-id="a8102-110">members</span></span>  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="a8102-111">Pour définir le convertisseur personnalisé comme le convertisseur actuel</span><span class="sxs-lookup"><span data-stu-id="a8102-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="a8102-112">Pour définir le convertisseur personnalisé pour une <xref:System.Windows.Forms.ToolStrip>, définissez la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> sur le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a8102-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="a8102-113">Ou pour définir le convertisseur personnalisé pour toutes les classes <xref:System.Windows.Forms.ToolStrip> contenues dans votre application : définissez la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> sur le convertisseur personnalisé et définissez la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> sur <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="a8102-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a8102-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8102-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="a8102-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a8102-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="a8102-116">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a8102-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="a8102-117">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a8102-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
