---
title: "Comment : afficher des cases d'option dans un MenuStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735527"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Comment : afficher des cases d'option dans un MenuStrip (Windows Forms)

Les cases d’option, également appelées cases d’option, sont similaires aux cases à cocher, à ceci près que les utilisateurs ne peuvent sélectionner qu’un seul à la fois. Bien que la classe <xref:System.Windows.Forms.ToolStripMenuItem> ne fournisse pas par défaut le comportement de bouton d’option, la classe fournit un comportement de case à cocher que vous pouvez personnaliser pour implémenter le comportement de bouton d’option pour les éléments de menu dans un contrôle <xref:System.Windows.Forms.MenuStrip>.

Lorsque la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> d’un élément de menu est `true`, les utilisateurs peuvent cliquer sur l’élément pour basculer l’affichage d’une coche. La propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> indique l’état actuel de l’élément. Pour implémenter un comportement de bouton d’option de base, vous devez vous assurer que lorsqu’un élément est sélectionné, vous affectez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de l’élément sélectionné précédemment la valeur `false`.

Les procédures suivantes décrivent comment implémenter cette fonctionnalité et d’autres fonctionnalités dans une classe qui hérite de la classe <xref:System.Windows.Forms.ToolStripMenuItem>. La classe `ToolStripRadioButtonMenuItem` remplace des membres tels que <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour fournir le comportement de sélection et l’apparence des cases d’option. En outre, cette classe remplace la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que les options d’un sous-menu soient désactivées, sauf si l’élément parent est sélectionné.

## <a name="to-implement-option-button-selection-behavior"></a>Pour implémenter le comportement de sélection d’un bouton d’option

1. Initialisez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> sur `true` pour activer la sélection de l’élément.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> pour effacer la sélection de l’élément sélectionné précédemment lorsqu’un nouvel élément est sélectionné.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Remplacez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> pour vous assurer que le fait de cliquer sur un élément qui a déjà été sélectionné n’efface pas la sélection.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Pour modifier l’apparence des éléments de bouton d’option

1. Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour remplacer la coche par défaut par une case d’option à l’aide de la classe <xref:System.Windows.Forms.RadioButtonRenderer>.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Substituez les méthodes <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>et <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> pour suivre l’état de la souris et vous assurer que la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> peint l’état de bouton d’option correct.

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Pour désactiver les options dans un sous-menu lorsque l’élément parent n’est pas sélectionné

1. Substituez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que l’élément soit désactivé lorsqu’il a un élément parent avec une valeur <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de `true` et une valeur <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de `false`.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> pour vous abonner au <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> événement de l’élément parent.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. Dans le gestionnaire de l’événement de <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> parent-élément, invalidez l’élément pour mettre à jour l’affichage avec le nouvel état activé.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Exemple

L’exemple de code suivant fournit la classe `ToolStripRadioButtonMenuItem` complète, ainsi qu’une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le comportement de la case d’option.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

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
- [Guide pratique pour implémenter un ToolStripRenderer personnalisé](how-to-implement-a-custom-toolstriprenderer.md)
