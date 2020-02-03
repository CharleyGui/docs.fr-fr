---
title: ancrer des contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747184"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Comment : ancrer des contrôles sur Windows Forms

Si vous concevez un formulaire que l’utilisateur peut redimensionner au moment de l’exécution, les contrôles de votre formulaire doivent être redimensionnés et repositionnés correctement. Pour redimensionner des contrôles de manière dynamique avec le formulaire, vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> de Windows Forms contrôles. La propriété <xref:System.Windows.Forms.Control.Anchor%2A> définit une position d’ancrage pour le contrôle. Lorsqu’un contrôle est ancré à un formulaire et que le formulaire est redimensionné, le contrôle maintient la distance entre le contrôle et les positions d’ancrage. Par exemple, si vous avez un contrôle <xref:System.Windows.Forms.TextBox> qui est ancré aux bords gauche, droit et inférieur du formulaire, au fur et à mesure que le formulaire est redimensionné, le contrôle <xref:System.Windows.Forms.TextBox> se redimensionne horizontalement afin qu’il conserve la même distance à partir des côtés droit et gauche du formulaire. En outre, le contrôle se positionne verticalement afin que son emplacement soit toujours la même distance que le bord inférieur du formulaire. Si un contrôle n’est pas ancré et que le formulaire est redimensionné, la position du contrôle par rapport aux bords du formulaire est modifiée.

La propriété <xref:System.Windows.Forms.Control.Anchor%2A> interagit avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Ancrer un contrôle dans un formulaire

1. Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.

    > [!NOTE]
    > Vous pouvez ancrer plusieurs contrôles simultanément en appuyant sur la touche CTRL, en cliquant sur chaque contrôle pour le sélectionner, puis en suivant le reste de cette procédure.

2. Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.

     Un éditeur affiche une croix.

3. Pour définir une ancre, cliquez sur la section en haut, à gauche, à droite ou en bas de la Croix.

     Les contrôles sont ancrés par défaut en haut et à gauche.

4. Pour effacer un côté du contrôle qui a été ancré, cliquez sur ce bras de la Croix.

5. Pour fermer l’éditeur de propriétés <xref:System.Windows.Forms.Control.Anchor%2A>, cliquez à nouveau sur le nom de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.

Lorsque votre formulaire s’affiche au moment de l’exécution, le contrôle est redimensionné pour rester positionné à la même distance que le bord du formulaire. La distance à partir du bord ancré reste toujours la même que la distance définie lorsque le contrôle est positionné dans le Concepteur Windows Forms.

> [!NOTE]
> Certains contrôles, tels que le contrôle <xref:System.Windows.Forms.ComboBox>, ont une limite à leur hauteur. L’ancrage du contrôle au bas de son formulaire ou conteneur ne peut pas forcer le contrôle à dépasser sa limite de hauteur.

Les contrôles hérités doivent être `Protected` pour pouvoir être ancrés. Pour modifier le niveau d’accès d’un contrôle, définissez sa propriété `Modifiers` dans la fenêtre **Propriétés** .

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Guide pratique pour fixer des contrôles sur des Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](windows-forms-controls-padding-autosize.md)
