---
title: 'Comment : modifier l’apparence du texte et des images ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746596"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="55117-102">Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55117-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="55117-103">Vous pouvez contrôler si le texte et les images sont affichés sur un <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés les uns par rapport aux autres et le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="55117-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="55117-104">Pour définir ce qui est affiché sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="55117-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="55117-105">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="55117-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="55117-106">Les possibilités sont `Image`, `ImageAndText`, `None`et `Text`.</span><span class="sxs-lookup"><span data-stu-id="55117-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="55117-107">Par défaut, il s’agit de `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="55117-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="55117-108">Pour aligner du texte sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="55117-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="55117-109">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="55117-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="55117-110">Les possibilités sont n’importe quelle combinaison des touches haut, milieu et bas avec gauche, Centre et droite.</span><span class="sxs-lookup"><span data-stu-id="55117-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="55117-111">Par défaut, il s’agit de `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="55117-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="55117-112">Pour aligner une image sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="55117-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="55117-113">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="55117-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="55117-114">Les possibilités sont n’importe quelle combinaison des touches haut, milieu et bas avec gauche, Centre et droite.</span><span class="sxs-lookup"><span data-stu-id="55117-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="55117-115">Par défaut, il s’agit de `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="55117-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="55117-116">Pour définir le mode d’affichage du texte et des images ToolStripItem les unes par rapport aux autres</span><span class="sxs-lookup"><span data-stu-id="55117-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="55117-117">Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="55117-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="55117-118">Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` et `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="55117-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="55117-119">Par défaut, il s’agit de `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="55117-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55117-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55117-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="55117-121">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55117-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="55117-122">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55117-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="55117-123">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="55117-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
