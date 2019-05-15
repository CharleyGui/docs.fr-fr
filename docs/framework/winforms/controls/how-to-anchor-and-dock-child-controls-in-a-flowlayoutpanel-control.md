---
title: 'Procédure : ancrer et arrimer des contrôles enfants dans un contrôle FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: f67733b89d2bde652449e2338362868fdb84bcf3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592942"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="f73ce-102">Procédure : ancrer et arrimer des contrôles enfants dans un contrôle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f73ce-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="f73ce-103">Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="f73ce-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="f73ce-104">Pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f73ce-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="f73ce-105">Créez un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="f73ce-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="f73ce-106">Définir le <xref:System.Windows.Forms.Control.Width%2A> de la <xref:System.Windows.Forms.FlowLayoutPanel> le contrôle à **300**et définissez son <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> à <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="f73ce-107">Créez deux contrôles <xref:System.Windows.Forms.Button> et placez-les dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="f73ce-108">Définir le <xref:System.Windows.Forms.Control.Width%2A> du premier bouton **200**.</span><span class="sxs-lookup"><span data-stu-id="f73ce-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="f73ce-109">Affectez la valeur <xref:System.Windows.Forms.DockStyle.Fill> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton.</span><span class="sxs-lookup"><span data-stu-id="f73ce-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f73ce-110">Le deuxième bouton a la même largeur que le premier.</span><span class="sxs-lookup"><span data-stu-id="f73ce-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="f73ce-111">Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="f73ce-112">Affectez la valeur `None` à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton.</span><span class="sxs-lookup"><span data-stu-id="f73ce-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="f73ce-113">Le bouton reprend sa largeur d'origine.</span><span class="sxs-lookup"><span data-stu-id="f73ce-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="f73ce-114">Affectez la valeur `Left, Right` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du deuxième bouton.</span><span class="sxs-lookup"><span data-stu-id="f73ce-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f73ce-115">Le deuxième bouton a la même largeur que le premier.</span><span class="sxs-lookup"><span data-stu-id="f73ce-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="f73ce-116">Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="f73ce-117">Il s'agit de la règle générale pour l'ancrage et l'arrimage dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> : pour les sens de flux verticaux, le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la largeur d'une colonne implicite à partir du contrôle enfant le plus large dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="f73ce-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="f73ce-118">Tous les autres contrôles dans cette colonne avec des propriétés <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> sont alignés ou étirés pour s'ajuster à cette colonne implicite.</span><span class="sxs-lookup"><span data-stu-id="f73ce-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="f73ce-119">Le comportement fonctionne de façon similaire pour les sens de flux horizontaux.</span><span class="sxs-lookup"><span data-stu-id="f73ce-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="f73ce-120">Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la hauteur d'une ligne implicite à partir du plus grand contrôle enfant sur la ligne et tous les contrôles enfants ancrés ou arrimés sur cette ligne sont alignés ou dimensionnés pour s'ajuster à la ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="f73ce-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f73ce-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f73ce-121">Example</span></span>  
 <span data-ttu-id="f73ce-122">L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="f73ce-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> a la valeur <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="f73ce-124">![Ancrage FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="f73ce-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="f73ce-125">L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="f73ce-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> a la valeur <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="f73ce-127">![Ancrage FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="f73ce-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="f73ce-128">L'exemple de code suivant illustre différentes valeurs de propriétés <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f73ce-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f73ce-129">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f73ce-129">Compiling the Code</span></span>  
 <span data-ttu-id="f73ce-130">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f73ce-130">This example requires:</span></span>  
  
- <span data-ttu-id="f73ce-131">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f73ce-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73ce-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f73ce-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="f73ce-133">Vue d’ensemble du contrôle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f73ce-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
