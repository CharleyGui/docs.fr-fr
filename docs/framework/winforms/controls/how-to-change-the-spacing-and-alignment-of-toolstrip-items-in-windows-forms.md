---
title: 'Comment : modifier l’espacement et l’alignement des éléments ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746565"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="55e7f-102">Comment : modifier l'espacement et l'alignement d'éléments ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55e7f-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="55e7f-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> prend entièrement en charge les fonctionnalités de disposition, telles que le dimensionnement, l’espacement des contrôles <xref:System.Windows.Forms.ToolStripItem> l’un par rapport à l’autre, la disposition des contrôles sur le <xref:System.Windows.Forms.ToolStrip>et l’espacement des contrôles par rapport au <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="55e7f-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="55e7f-104">Étant donné que la valeur par défaut de la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> est `true`, les contrôles sont dimensionnés automatiquement, sauf si vous affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="55e7f-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="55e7f-105">Pour dimensionner manuellement un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="55e7f-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="55e7f-106">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false` pour le contrôle associé.</span><span class="sxs-lookup"><span data-stu-id="55e7f-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="55e7f-107">Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Size%2A> comme vous le souhaitez pour le <xref:System.Windows.Forms.ToolStripItem>associé.</span><span class="sxs-lookup"><span data-stu-id="55e7f-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="55e7f-108">Pour définir l’espacement d’un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="55e7f-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="55e7f-109">Insérez les valeurs souhaitées, en pixels, dans la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> du contrôle associé.</span><span class="sxs-lookup"><span data-stu-id="55e7f-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="55e7f-110">Les valeurs de la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> spécifient l’espacement entre l’élément et les éléments adjacents dans l’ordre suivant : gauche, haut, droite et bas.</span><span class="sxs-lookup"><span data-stu-id="55e7f-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="55e7f-111">Pour aligner un ToolStripItem sur le côté droit du ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55e7f-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="55e7f-112">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> la valeur <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pour le contrôle associé.</span><span class="sxs-lookup"><span data-stu-id="55e7f-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="55e7f-113">Par défaut, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a la valeur <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, qui aligne les contrôles sur le côté gauche du <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="55e7f-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="55e7f-114">Pour réorganiser des éléments ToolStrip sur le ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55e7f-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="55e7f-115">Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> la valeur de <xref:System.Windows.Forms.ToolStripLayoutStyle> souhaitée.</span><span class="sxs-lookup"><span data-stu-id="55e7f-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55e7f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55e7f-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="55e7f-117">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55e7f-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="55e7f-118">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55e7f-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="55e7f-119">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55e7f-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
