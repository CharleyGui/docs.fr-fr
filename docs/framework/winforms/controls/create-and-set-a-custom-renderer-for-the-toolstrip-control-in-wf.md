---
title: 'Comment : Créer et définir un rendu personnalisé pour le contrôle ToolStrip'
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182405"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="b2642-102">Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2642-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="b2642-103"><xref:System.Windows.Forms.ToolStrip>les contrôles donnent un soutien facile aux thèmes et aux styles.</span><span class="sxs-lookup"><span data-stu-id="b2642-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="b2642-104">Vous pouvez atteindre l’apparence et le comportement complètement <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> personnalisés <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> (regardez et sentez) en définissant soit la propriété ou la propriété à un rendu personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b2642-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="b2642-105">Vous pouvez attribuer des <xref:System.Windows.Forms.ToolStrip>rendus <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>à <xref:System.Windows.Forms.StatusStrip> chaque individu, , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> , ou le contrôle, <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>vous pouvez utiliser la propriété pour affecter tous les objets en définissant la propriété à .</span><span class="sxs-lookup"><span data-stu-id="b2642-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2642-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>rendements <xref:System.Windows.Forms.ToolStripRenderMode.Custom> seulement si <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> la `null`valeur de n’est pas .</span><span class="sxs-lookup"><span data-stu-id="b2642-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="b2642-107">Pour créer un rendu personnalisé</span><span class="sxs-lookup"><span data-stu-id="b2642-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="b2642-108">Prolongez <xref:System.Windows.Forms.ToolStripRenderer> la classe.</span><span class="sxs-lookup"><span data-stu-id="b2642-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="b2642-109">Implémentez le rendu personnalisé souhaité en dominant approprié *on...*</span><span class="sxs-lookup"><span data-stu-id="b2642-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="b2642-110">membres</span><span class="sxs-lookup"><span data-stu-id="b2642-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="b2642-111">Pour définir le rendu personnalisé pour être le rendu actuel</span><span class="sxs-lookup"><span data-stu-id="b2642-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="b2642-112">Pour définir le rendu <xref:System.Windows.Forms.ToolStrip>personnalisé pour <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> un, définissez la propriété sur le rendu personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b2642-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="b2642-113">Ou pour définir le rendu <xref:System.Windows.Forms.ToolStrip> personnalisé pour toutes les <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> classes contenues dans votre <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> application: Réglez la propriété au rendu personnalisé et définissez la propriété à <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="b2642-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b2642-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2642-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="b2642-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b2642-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="b2642-116">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b2642-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="b2642-117">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b2642-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
