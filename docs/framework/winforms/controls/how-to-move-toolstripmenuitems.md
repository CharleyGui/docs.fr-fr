---
title: 'Procédure : déplacer des ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039797"
---
# <a name="how-to-move-toolstripmenuitems"></a>Procédure : déplacer des ToolStripMenuItems
Au moment du design, vous pouvez déplacer l’intégralité des menus de niveau supérieur et leurs éléments de menu vers un <xref:System.Windows.Forms.MenuStrip>autre emplacement sur le. Vous pouvez également déplacer des éléments de menu individuels entre des menus de niveau supérieur ou modifier la position des éléments de menu dans un menu.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Pour déplacer un menu du plus haut niveau et ses éléments de menu vers un autre emplacement de niveau supérieur

1. Cliquez et maintenez le bouton gauche de la souris enfoncé sur le menu que vous souhaitez déplacer.

2. Faites glisser le point d’insertion vers le menu du plus haut niveau qui se trouve avant le nouvel emplacement prévu et relâchez le bouton gauche de la souris.

     Le menu sélectionné se déplace à droite du point d’insertion.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Pour déplacer un menu du plus haut niveau et ses éléments de menu vers un emplacement déroulant

1. Cliquez avec le bouton gauche sur le menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou cliquez avec le bouton droit sur le menu et sélectionnez **couper** dans le menu contextuel.

2. Dans le menu du plus haut niveau de destination, cliquez sur l’élément de menu situé au-dessus du nouvel emplacement prévu et appuyez sur CTRL + V, ou cliquez avec le bouton droit sur l’élément de menu situé au-dessus du nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.

     Le menu que vous coupez est inséré après l’élément de menu sélectionné.

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Pour déplacer un élément de menu dans un menu à l’aide de l’éditeur de collections Items

1. Cliquez avec le bouton droit sur le menu qui contient l’élément de menu que vous souhaitez déplacer.

2. Dans le menu contextuel, choisissez **modifier DropDownItems**.

3. Dans l **'éditeur de collections Items**, cliquez sur l’élément de menu que vous souhaitez déplacer.

4. Cliquez sur les flèches vers le haut et vers le bas pour déplacer l’élément de menu dans le menu.

5. Cliquez sur **OK**.

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Pour déplacer un élément de menu dans un menu à l’aide du clavier

1. Maintenez la touche ALT enfoncée.

2. Cliquez et maintenez enfoncé le bouton gauche de la souris sur l’élément de menu que vous souhaitez déplacer.

3. Faites glisser l’élément de menu vers le nouvel emplacement, puis relâchez le bouton gauche de la souris.

## <a name="to-move-a-menu-item-to-another-menu"></a>Pour déplacer un élément de menu vers un autre menu

1. Cliquez sur l’élément de menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou cliquez avec le bouton droit sur l’élément de menu et choisissez **couper** dans le menu contextuel.

2. Cliquez sur le menu qui contiendra l’élément de menu que vous avez coupé.

3. Cliquez sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et appuyez sur CTRL + V, ou cliquez avec le bouton droit sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.

     L’élément de menu que vous coupez est inséré après l’élément de menu sélectionné.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
