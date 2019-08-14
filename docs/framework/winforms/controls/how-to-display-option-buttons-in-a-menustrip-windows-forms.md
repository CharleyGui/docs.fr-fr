---
title: 'Procédure : Afficher des cases d’option dans un MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971925"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Procédure : Afficher des cases d’option dans un MenuStrip (Windows Forms)

Les cases d’option, également appelées cases d’option, sont similaires aux cases à cocher, à ceci près que les utilisateurs ne peuvent sélectionner qu’un seul à la fois. Même si, par <xref:System.Windows.Forms.ToolStripMenuItem> défaut, la classe ne fournit pas de comportement de bouton d’option, la classe fournit un comportement de case à cocher que vous pouvez personnaliser pour implémenter le <xref:System.Windows.Forms.MenuStrip> comportement de bouton d’option pour les éléments de menu dans un contrôle.

Lorsque la <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété d’un élément de menu `true`est, les utilisateurs peuvent cliquer sur l’élément pour basculer l’affichage d’une coche. La <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriété indique l’état actuel de l’élément. Pour implémenter un comportement de bouton d’option de base, vous devez vous assurer que lorsqu’un élément est <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> sélectionné, vous affectez à `false`la propriété de l’élément sélectionné précédemment la valeur.

Les procédures suivantes décrivent comment implémenter cette fonctionnalité et d’autres fonctionnalités dans une classe qui <xref:System.Windows.Forms.ToolStripMenuItem> hérite de la classe. La `ToolStripRadioButtonMenuItem` classe substitue des membres tels que <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour fournir le comportement de sélection et l’apparence des cases d’option. En outre, cette classe remplace la <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que les options d’un sous-menu soient désactivées, sauf si l’élément parent est sélectionné.

## <a name="to-implement-option-button-selection-behavior"></a>Pour implémenter le comportement de sélection d’un bouton d’option

1. Initialisez la <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriété à `true` pour activer la sélection de l’élément.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Substituez la <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> méthode pour effacer la sélection de l’élément sélectionné précédemment lorsqu’un nouvel élément est sélectionné.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Substituez la <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> méthode pour vous assurer que le fait de cliquer sur un élément qui a déjà été sélectionné n’efface pas la sélection.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Pour modifier l’apparence des éléments de bouton d’option

1. Substituez la <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> méthode pour remplacer la coche par défaut par une case d’option à l’aide <xref:System.Windows.Forms.RadioButtonRenderer> de la classe.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Substituez les <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>méthodes <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> ,, et pour suivre l’état de la souris et assurez-vous <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> que la méthode peint l’état correct du bouton d’option. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Pour désactiver les options dans un sous-menu lorsque l’élément parent n’est pas sélectionné

1. Substituez la <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriété afin que l’élément soit désactivé lorsqu’il a un élément parent avec à la <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> fois la `true` valeur et <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> la valeur `false`.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Substituez la <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> méthode pour vous abonner <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> à l’événement de l’élément parent.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. Dans le gestionnaire de l’événement de l' <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> élément parent, invalidez l’élément pour mettre à jour l’affichage avec le nouvel état activé.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Exemples

L’exemple de code suivant fournit la `ToolStripRadioButtonMenuItem` classe complète, et <xref:System.Windows.Forms.Form> une classe `Program` et une classe pour illustrer le comportement de bouton d’option.

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
- [Guide pratique : Implémenter un ToolStripRenderer personnalisé](how-to-implement-a-custom-toolstriprenderer.md)
