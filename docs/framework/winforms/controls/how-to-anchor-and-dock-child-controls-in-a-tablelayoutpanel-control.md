---
title: 'Procédure : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 7adbf9a98b25b237ee49d2689154e903d8fc0b5a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586173"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="542d7-102">Procédure : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="542d7-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="542d7-103">Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="542d7-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="542d7-104">Pour aligner un contrôle enfant dans une cellule TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="542d7-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="542d7-105">Créez un contrôle <xref:System.Windows.Forms.TableLayoutPanel> sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="542d7-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="542d7-106">Définissez la valeur de la <xref:System.Windows.Forms.TableLayoutPanel> du contrôle <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> et <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> propriétés à **1**.</span><span class="sxs-lookup"><span data-stu-id="542d7-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="542d7-107">Créez un contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="542d7-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="542d7-108">Le <xref:System.Windows.Forms.Button> occupe le coin supérieur gauche de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="542d7-109">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Left`.</span><span class="sxs-lookup"><span data-stu-id="542d7-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="542d7-110">Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="542d7-111">Ce comportement diffère du comportement des autres contrôles conteneurs.</span><span class="sxs-lookup"><span data-stu-id="542d7-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="542d7-112">Dans d'autres contrôles conteneurs, le contrôle enfant ne bouge pas quand la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie et la distance entre le contrôle ancré et la limite du parent conteneur est fixée au moment où la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie.</span><span class="sxs-lookup"><span data-stu-id="542d7-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="542d7-113">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="542d7-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="542d7-114">Le contrôle <xref:System.Windows.Forms.Button> se déplace pour occuper l'angle supérieur gauche de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="542d7-115">Répétez l’étape 5 avec une valeur de `Top, Right` pour déplacer le <xref:System.Windows.Forms.Button> contrôle à l’angle supérieur droit de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="542d7-116">Répétez l’opération avec les valeurs `Bottom, Left` et `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="542d7-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="542d7-117">Pour étendre un contrôle enfant dans une cellule TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="542d7-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="542d7-118">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="542d7-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="542d7-119">Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre sur toute la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="542d7-120">Ce comportement diffère du comportement des autres contrôles conteneurs.</span><span class="sxs-lookup"><span data-stu-id="542d7-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="542d7-121">Dans d’autres contrôles conteneurs, le contrôle enfant n’est pas redimensionné quand la <xref:System.Windows.Forms.Control.Anchor%2A> propriété est définie sur `Left, Right` ou `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="542d7-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="542d7-122">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="542d7-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="542d7-123">Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre du haut en bas de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="542d7-124">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="542d7-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="542d7-125">Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="542d7-126">Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `None`.</span><span class="sxs-lookup"><span data-stu-id="542d7-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="542d7-127">Le contrôle <xref:System.Windows.Forms.Button> est redimensionné et centré dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="542d7-128">Affectez la valeur <xref:System.Windows.Forms.DockStyle.Left> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="542d7-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="542d7-129">Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="542d7-130">Le contrôle <xref:System.Windows.Forms.Button> conserve sa largeur, mais sa hauteur est redimensionnée pour remplir la cellule verticalement.</span><span class="sxs-lookup"><span data-stu-id="542d7-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="542d7-131">Il s'agit du même comportement que celui des autres contrôles conteneurs.</span><span class="sxs-lookup"><span data-stu-id="542d7-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="542d7-132">Affectez la valeur <xref:System.Windows.Forms.DockStyle.Fill> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="542d7-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="542d7-133">Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="542d7-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="542d7-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="542d7-134">Example</span></span>  
 <span data-ttu-id="542d7-135">L'illustration suivante montre cinq boutons ancrés dans cinq cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.</span><span class="sxs-lookup"><span data-stu-id="542d7-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="542d7-136">![Ancrage de TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="542d7-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="542d7-137">L'illustration suivante montre quatre boutons ancrés dans les coins de quatre cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.</span><span class="sxs-lookup"><span data-stu-id="542d7-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="542d7-138">![Ancrage de TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="542d7-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="542d7-139">L'illustration suivante montre trois boutons étirés par ancrage dans trois cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.</span><span class="sxs-lookup"><span data-stu-id="542d7-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="542d7-140">![Ancrage de TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPanchor3")</span><span class="sxs-lookup"><span data-stu-id="542d7-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="542d7-141">L'exemple de code suivant montre toutes les combinaisons de valeurs de propriété <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="542d7-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="542d7-142">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="542d7-142">Compiling the Code</span></span>  
 <span data-ttu-id="542d7-143">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="542d7-143">This example requires:</span></span>  
  
- <span data-ttu-id="542d7-144">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="542d7-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542d7-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="542d7-145">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="542d7-146">TableLayoutPanel, contrôle</span><span class="sxs-lookup"><span data-stu-id="542d7-146">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
