---
title: Vue d'ensemble du composant ColorDialog
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736967"
---
# <a name="colordialog-component-overview-windows-forms"></a>Vue d'ensemble du composant ColorDialog (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.ColorDialog> est une boîte de dialogue préconfigurée qui permet à l’utilisateur de sélectionner une couleur dans une palette et d’ajouter des couleurs personnalisées à cette palette. Il s’agit de la même boîte de dialogue que celle que vous voyez dans d’autres applications Windows pour sélectionner des couleurs. Vous pouvez l'utiliser dans votre application Windows comme alternative à la configuration de votre propre boîte de dialogue.  
  
 La couleur sélectionnée dans la boîte de dialogue est retournée dans la propriété <xref:System.Windows.Forms.ColorDialog.Color%2A>. Si la propriété <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `false`, le bouton « définir des couleurs personnalisées » est désactivé et l’utilisateur est limité aux couleurs prédéfinies dans la palette. Si la propriété <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner les couleurs désélectionnées. Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, composant](colordialog-component-windows-forms.md)
- [Contrôles et composants de boîte de dialogue](dialog-box-controls-and-components-windows-forms.md)
- [Guide pratique pour modifier l’apparence du composant ColorDialog Windows Forms](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
