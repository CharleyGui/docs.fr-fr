---
title: Vue d’ensemble du contrôle PrintPreviewControl
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741438"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>Vue d'ensemble du contrôle PrintPreviewControl (Windows Forms)
Le <xref:System.Windows.Forms.PrintPreviewControl> Windows Forms est utilisé pour afficher un [PrintDocument](printdocument-component-windows-forms.md) tel qu’il apparaîtra une fois imprimé. Ce contrôle n'ayant aucun bouton ni élément d'interface utilisateur, vous utilisez généralement <xref:System.Windows.Forms.PrintPreviewControl> uniquement si vous souhaitez écrire votre propre interface utilisateur d'aperçu avant impression. Si vous souhaitez l’interface utilisateur standard, utilisez un contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ; pour une vue d’ensemble, consultez [vue d’ensemble du contrôle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md) .  
  
## <a name="key-properties"></a>Propriétés de clé  
 La propriété de clé du contrôle est <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, qui définit le document à afficher en aperçu. Le document doit être un objet <xref:System.Drawing.Printing.PrintDocument>. Pour obtenir une vue d’ensemble de la création de documents pour l’impression, consultez [vue d’ensemble du composant PrintDocument](printdocument-component-overview-windows-forms.md) et [Windows Forms prise en charge](../advanced/windows-forms-print-support.md)de l’impression. Les propriétés <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle. L’anticrénelage peut rendre le texte plus lisse, mais peut également rendre l’affichage plus lent ; pour l’utiliser, affectez à la propriété <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> la valeur `true`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PrintPreviewControl>
- [Vue d’ensemble du contrôle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl, contrôle](printpreviewcontrol-control-windows-forms.md)
- [Contrôles et composants de boîte de dialogue](dialog-box-controls-and-components-windows-forms.md)
