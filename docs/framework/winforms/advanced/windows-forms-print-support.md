---
title: Prise en charge de l’impression
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732494"
---
# <a name="windows-forms-print-support"></a>Prise en charge de l'impression dans les Windows Forms
L’impression dans Windows Forms se compose principalement de l’utilisation du composant de [composant PrintDocument](../controls/printdocument-component-windows-forms.md) pour permettre à l’utilisateur d’imprimer, et du contrôle de [contrôle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md) , du [composant PrintDialog](../controls/printdialog-component-windows-forms.md) et des composants du [composant PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) pour fournir une interface graphique familière aux utilisateurs habitués au système d’exploitation Windows.  
  
 En général, vous créez une nouvelle instance du composant <xref:System.Drawing.Printing.PrintDocument>, définissez les propriétés qui décrivent les éléments à imprimer à l’aide des classes <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings>, puis appelez la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour imprimer le document.  
  
 Au cours de l’impression à partir d’une application Windows, le composant <xref:System.Drawing.Printing.PrintDocument> affiche une boîte de dialogue annuler l’impression pour avertir les utilisateurs du fait que l’impression est en cours et pour autoriser l’annulation du travail d’impression.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer des travaux d’impression Windows Forms standard](how-to-create-standard-windows-forms-print-jobs.md)  
 Explique comment utiliser le composant <xref:System.Drawing.Printing.PrintDocument> pour imprimer à partir d’un Windows Form.  
  
 [Guide pratique pour capturer une entrée d’utilisateur à partir d’un composant PrintDialog au moment de l’exécution](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explique comment modifier les options d’impression sélectionnées par programme à l’aide du composant <xref:System.Windows.Forms.PrintDialog>.  
  
 [Guide pratique pour choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans les Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Décrit la modification de l’imprimante à utiliser pour l’impression à l’aide du composant <xref:System.Windows.Forms.PrintDialog> au moment de l’exécution.  
  
 [Comment : imprimer des graphiques dans Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Décrit l’envoi de graphiques à l’imprimante.  
  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Décrit l’envoi de texte à l’imprimante.  
  
 [Guide pratique pour terminer des travaux d'impression Windows Forms](how-to-complete-windows-forms-print-jobs.md)  
 Explique comment avertir les utilisateurs de l’achèvement d’un travail d’impression.  
  
 [Guide pratique pour imprimer un Windows Form](how-to-print-a-windows-form.md)  
 Montre comment imprimer une copie du formulaire actif.  
  
 [Guide pratique pour imprimer dans les Windows Forms en utilisant l'aperçu avant impression](how-to-print-in-windows-forms-using-print-preview.md)  
 Montre comment utiliser une <xref:System.Windows.Forms.PrintPreviewDialog> pour l’impression d’un document.  
  
## <a name="related-sections"></a>Sections connexes  
 [PrintDocument, composant](../controls/printdocument-component-windows-forms.md)  
 Explique l’utilisation du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
 [PrintDialog, composant](../controls/printdialog-component-windows-forms.md)  
 Explique l’utilisation du composant <xref:System.Windows.Forms.PrintDialog>.  
  
 [PrintPreviewDialog, contrôle](../controls/printpreviewdialog-control-windows-forms.md)  
 Explique l’utilisation du contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
 [PageSetupDialog, composant](../controls/pagesetupdialog-component-windows-forms.md)  
 Explique l’utilisation du composant <xref:System.Windows.Forms.PageSetupDialog>.  
  
 <xref:System.Drawing.Printing>  
 Décrit les classes de l’espace de noms <xref:System.Drawing.Printing>.
