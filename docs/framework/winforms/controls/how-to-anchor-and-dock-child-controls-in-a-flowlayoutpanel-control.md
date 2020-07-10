---
title: 'Comment : ancrer des contrôles enfants dans un contrôle FlowLayoutPanel'
description: Découvrez comment ancrer et ancrer par programmation des contrôles enfants dans un contrôle Windows Forms FlowLayoutPanel.
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174534"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Comment : ancrer des contrôles enfants dans un contrôle FlowLayoutPanel

Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel

1. Créez un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> sur votre formulaire.

2. Affectez <xref:System.Windows.Forms.Control.Width%2A> à la valeur du contrôle la valeur <xref:System.Windows.Forms.FlowLayoutPanel> **300**et <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> à la valeur <xref:System.Windows.Forms.FlowDirection.TopDown> .

3. Créez deux contrôles <xref:System.Windows.Forms.Button> et placez-les dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.

4. Affectez la valeur <xref:System.Windows.Forms.Control.Width%2A> **200**à l’du premier bouton.

5. Affectez la valeur <xref:System.Windows.Forms.DockStyle.Fill> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton.

    > [!NOTE]
    > Le deuxième bouton a la même largeur que le premier. Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.

6. Affectez la valeur `None` à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton. Le bouton reprend sa largeur d'origine.

7. Affectez la valeur `Left, Right` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du deuxième bouton.

    > [!IMPORTANT]
    > Le deuxième bouton a la même largeur que le premier. Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>. Il s'agit de la règle générale pour l'ancrage et l'arrimage dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> : pour les sens de flux verticaux, le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la largeur d'une colonne implicite à partir du contrôle enfant le plus large dans la colonne. Tous les autres contrôles dans cette colonne avec des propriétés <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> sont alignés ou étirés pour s'ajuster à cette colonne implicite. Le comportement fonctionne de façon similaire pour les sens de flux horizontaux. Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la hauteur d'une ligne implicite à partir du plus grand contrôle enfant sur la ligne et tous les contrôles enfants ancrés ou arrimés sur cette ligne sont alignés ou dimensionnés pour s'ajuster à la ligne implicite.

## <a name="example"></a>Exemple

L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>. Le <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> est <xref:System.Windows.Forms.FlowDirection.LeftToRight>.

![Ancrage de FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>. Le <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> est <xref:System.Windows.Forms.FlowDirection.TopDown>.

![Ancrage de FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")

L'exemple de code suivant illustre différentes valeurs de propriétés <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Vue d'ensemble du contrôle FlowLayoutPanel](flowlayoutpanel-control-overview.md)
