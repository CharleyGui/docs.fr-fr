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
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922825"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Procédure : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel
Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Pour aligner un contrôle enfant dans une cellule TableLayoutPanel  
  
1. Créez un contrôle <xref:System.Windows.Forms.TableLayoutPanel> sur votre formulaire.  
  
2. <xref:System.Windows.Forms.TableLayoutPanel> Affectez la valeur **1**aux propriétés <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> et <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> du contrôle.  
  
3. Créez un contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>. Le <xref:System.Windows.Forms.Button> occupe le coin supérieur gauche de la cellule.  
  
4. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Left`. Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule.  
  
    > [!NOTE]
    > Ce comportement diffère du comportement des autres contrôles conteneurs. Dans d'autres contrôles conteneurs, le contrôle enfant ne bouge pas quand la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie et la distance entre le contrôle ancré et la limite du parent conteneur est fixée au moment où la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie.  
  
5. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Left`. Le contrôle <xref:System.Windows.Forms.Button> se déplace pour occuper l'angle supérieur gauche de la cellule.  
  
6. Répétez l’étape 5 avec la `Top, Right` valeur pour déplacer <xref:System.Windows.Forms.Button> le contrôle vers l’angle supérieur droit de la cellule. Répétez l’opération avec les valeurs `Bottom, Left` et `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Pour étendre un contrôle enfant dans une cellule TableLayoutPanel  
  
1. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Left, Right`. Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre sur toute la cellule.  
  
    > [!NOTE]
    > Ce comportement diffère du comportement des autres contrôles conteneurs. Dans d’autres contrôles conteneurs, le contrôle enfant n’est pas redimensionné lorsque <xref:System.Windows.Forms.Control.Anchor%2A> la propriété a la `Left, Right` valeur `Top, Bottom`ou.  
  
2. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Bottom`. Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre du haut en bas de la cellule.  
  
3. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `Top, Bottom, Left, Right`. Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.  
  
4. Affectez la valeur <xref:System.Windows.Forms.Button> à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle `None`. Le contrôle <xref:System.Windows.Forms.Button> est redimensionné et centré dans la cellule.  
  
5. Affectez la valeur <xref:System.Windows.Forms.DockStyle.Left> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>. Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule. Le contrôle <xref:System.Windows.Forms.Button> conserve sa largeur, mais sa hauteur est redimensionnée pour remplir la cellule verticalement.  
  
    > [!NOTE]
    > Il s'agit du même comportement que celui des autres contrôles conteneurs.  
  
6. Affectez la valeur <xref:System.Windows.Forms.DockStyle.Fill> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>. Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.  
  
## <a name="example"></a>Exemple  
 L'illustration suivante montre cinq boutons ancrés dans cinq cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 L'illustration suivante montre quatre boutons ancrés dans les coins de quatre cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 L'illustration suivante montre trois boutons étirés par ancrage dans trois cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPanchor3")  
  
 L'exemple de code suivant montre toutes les combinaisons de valeurs de propriété <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel, contrôle](tablelayoutpanel-control-windows-forms.md)
