---
title: 'Procédure : modifier l’aspect du texte et des images du contrôle ToolStrip dans Windows Forms'
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
ms.openlocfilehash: cf2f332b17bf6ff5b6ffb7cbc2d5777649728ec6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650854"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="4a2f7-102">Procédure : modifier l’aspect du texte et des images du contrôle ToolStrip dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a2f7-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="4a2f7-103">Vous pouvez contrôler si le texte et les images sont affichés sur un <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés par rapport aux autres et le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="4a2f7-104">Pour définir ce qui est affiché sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4a2f7-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="4a2f7-105">Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="4a2f7-106">Les possibilités sont `Image`, `ImageAndText`, `None`, et `Text`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="4a2f7-107">La valeur par défaut est `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="4a2f7-108">Pour aligner le texte sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4a2f7-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="4a2f7-109">Définir le <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="4a2f7-110">Les possibilités sont n’importe quelle combinaison de haut, intermédiaire et en bas à gauche, centre et droite.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="4a2f7-111">La valeur par défaut est `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="4a2f7-112">Pour aligner une image sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4a2f7-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="4a2f7-113">Définir le <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="4a2f7-114">Les possibilités sont n’importe quelle combinaison de haut, intermédiaire et en bas à gauche, centre et droite.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="4a2f7-115">La valeur par défaut est `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="4a2f7-116">Pour définir l’affichent des images et du texte de ToolStripItem par rapport aux autres</span><span class="sxs-lookup"><span data-stu-id="4a2f7-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="4a2f7-117">Définir le <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="4a2f7-118">Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, et `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="4a2f7-119">La valeur par défaut est `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="4a2f7-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a2f7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a2f7-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="4a2f7-121">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4a2f7-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="4a2f7-122">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4a2f7-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="4a2f7-123">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4a2f7-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
