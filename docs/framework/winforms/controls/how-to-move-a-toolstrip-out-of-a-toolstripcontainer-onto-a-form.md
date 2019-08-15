---
title: 'Procédure : déplacer un ToolStrip hors d’un ToolStripContainer dans un formulaire'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: c6519add6789485d41146633abb5e11f80913649
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039827"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Procédure : déplacer un ToolStrip hors d’un ToolStripContainer dans un formulaire
Utilisez la procédure suivante pour déplacer un <xref:System.Windows.Forms.ToolStrip> en dehors <xref:System.Windows.Forms.ToolStripContainer> de sur un formulaire.

## <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Pour déplacer un ToolStrip hors d’un ToolStripContainer dans un formulaire

1. Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStrip>.

2. Coupez le <xref:System.Windows.Forms.ToolStrip> en appuyant sur CTRL + X, ou cliquez avec <xref:System.Windows.Forms.ToolStrip> le bouton droit sur le et choisissez **couper** dans le menu contextuel.

3. Sélectionnez le formulaire.

4. Collez <xref:System.Windows.Forms.ToolStrip> le en appuyant sur Ctrl + V ou choisissez **coller** dans le menu **Edition** .

5. Affectez <xref:System.Windows.Forms.ToolStrip.Dock%2A> à la propriété <xref:System.Windows.Forms.ToolStrip> de la valeur **Top**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
