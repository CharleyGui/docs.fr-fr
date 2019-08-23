---
title: 'Procédure : créer et définir un renderer personnalisé pour le contrôle ToolStrip dans Windows Forms'
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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929741"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="2fb06-102">Procédure : créer et définir un renderer personnalisé pour le contrôle ToolStrip dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2fb06-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="2fb06-103"><xref:System.Windows.Forms.ToolStrip>les contrôles offrent un support facile pour les thèmes et les styles.</span><span class="sxs-lookup"><span data-stu-id="2fb06-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="2fb06-104">Vous pouvez obtenir une apparence et un comportement entièrement personnalisés (apparence) en affectant à <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> la propriété ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> à la propriété un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2fb06-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="2fb06-105">Vous pouvez assigner des convertisseurs <xref:System.Windows.Forms.ToolStrip>à <xref:System.Windows.Forms.MenuStrip>chaque <xref:System.Windows.Forms.ContextMenuStrip>contrôle individuel <xref:System.Windows.Forms.StatusStrip> ,, ou, ou vous pouvez <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> utiliser la propriété pour affecter tous les objets <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> en affectant à <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="2fb06-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb06-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>retourne <xref:System.Windows.Forms.ToolStripRenderMode.Custom> uniquement si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> n’est `null`pas.</span><span class="sxs-lookup"><span data-stu-id="2fb06-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="2fb06-107">Pour créer un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="2fb06-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="2fb06-108">Étendez <xref:System.Windows.Forms.ToolStripRenderer> la classe.</span><span class="sxs-lookup"><span data-stu-id="2fb06-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="2fb06-109">Implémentez le rendu personnalisé souhaité en remplaçant *le approprié sur...*</span><span class="sxs-lookup"><span data-stu-id="2fb06-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="2fb06-110">membres</span><span class="sxs-lookup"><span data-stu-id="2fb06-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="2fb06-111">Pour définir le convertisseur personnalisé comme le convertisseur actuel</span><span class="sxs-lookup"><span data-stu-id="2fb06-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="2fb06-112">Pour définir le convertisseur personnalisé pour un <xref:System.Windows.Forms.ToolStrip>, définissez la <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriété sur le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2fb06-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="2fb06-113">Ou pour définir le convertisseur personnalisé pour toutes les <xref:System.Windows.Forms.ToolStrip> classes contenues dans votre application: Définissez la <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>propriété sur le convertisseur personnalisé et affectez à la propriété la valeur. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2fb06-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2fb06-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fb06-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="2fb06-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2fb06-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="2fb06-116">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2fb06-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="2fb06-117">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2fb06-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
