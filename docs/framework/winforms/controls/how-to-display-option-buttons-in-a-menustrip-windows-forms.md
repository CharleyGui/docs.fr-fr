---
title: 'Procédure : Afficher les boutons d’Option dans un MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 2ee8f75725fada624e7075c51e111b970acc80b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610110"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Procédure : Afficher les boutons d’Option dans un MenuStrip (Windows Forms)
Cases d’option, également connu sous les boutons radio, sont similaires aux cases à cocher sauf que les utilisateurs peuvent sélectionner qu’un seul à la fois. Bien que, par défaut le <xref:System.Windows.Forms.ToolStripMenuItem> classe ne fournit pas de comportement de case d’option, la classe fournit un comportement de case à cocher que vous pouvez personnaliser pour implémenter le comportement de case d’option pour les éléments de menu dans un <xref:System.Windows.Forms.MenuStrip> contrôle.  
  
 Lorsque le <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété d’un élément de menu est `true`, les utilisateurs peuvent cliquer sur l’élément pour désactiver l’affichage d’une case à cocher. Le <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété indique l’état actuel de l’élément. Pour implémenter le comportement de case d’option de base, vous devez vous assurer que lorsqu’un élément est sélectionné, vous définissez le <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété pour l’élément sélectionné précédemment à `false`.  
  
 Les procédures suivantes décrivent comment implémenter cela et des fonctionnalités supplémentaires dans une classe qui hérite de la <xref:System.Windows.Forms.ToolStripMenuItem> classe. Le `ToolStripRadioButtonMenuItem` classe remplace les membres comme <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour fournir le comportement de la sélection et l’apparence de cases d’option. En outre, cette classe substitue la <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que les options d’un sous-menu sont désactivées, sauf si l’élément parent est sélectionné.  
  
### <a name="to-implement-option-button-selection-behavior"></a>Pour implémenter le comportement de sélection de case d’option  
  
1. Initialiser le <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété `true` pour activer la sélection de l’élément.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> méthode pour effacer la sélection de l’élément sélectionné précédemment lorsqu’un nouvel élément est sélectionné.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> pour s’assurer que cliquer sur un élément qui a déjà été sélectionné n’effacera pas la sélection.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Pour modifier l’apparence des éléments de case d’option  
  
1. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> méthode pour remplacer la coche par défaut avec une case d’option à l’aide de la <xref:System.Windows.Forms.RadioButtonRenderer> classe.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, et <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> méthodes pour suivre l’état de la souris et vérifiez que le <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> méthode peint l’état de case d’option correct.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Pour désactiver les options d’un sous-menu lorsque l’élément parent n’est pas sélectionné.  
  
1. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que l’élément est désactivé lorsqu’il a un élément parent avec à la fois un <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> valeur `true` et un <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> valeur de `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2. Remplacer le <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> méthode pour vous abonner à la <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> événements de l’élément parent.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3. Dans le gestionnaire pour l’élément parent <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> événement, rendez l’élément pour mettre à jour l’affichage avec le nouvel état activé.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant fournit le texte complet `ToolStripRadioButtonMenuItem` (classe) et un <xref:System.Windows.Forms.Form> classe et `Program` classe afin d’illustrer le comportement de case d’option.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
- [Guide pratique pour Implémenter un ToolStripRenderer personnalisé](how-to-implement-a-custom-toolstriprenderer.md)
