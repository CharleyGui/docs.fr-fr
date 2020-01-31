---
title: Vue d'ensemble du contrôle PrintPreviewDialog
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 6fb971493336cda1e04c720dd09147e650918c3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741411"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Vue d’ensemble du contrôle PrintPreviewDialog (Windows Forms)

Le contrôle Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> est une boîte de dialogue préconfigurée qui permet d’afficher la manière dont un [PrintDocument](printdocument-component-windows-forms.md) apparaîtra une fois imprimé. Utilisez-le au sein de votre application Windows comme une solution simple au lieu de configurer votre propre boîte de dialogue. Le contrôle contient des boutons pour l'impression, le zoom avant, l'affichage d'une ou plusieurs pages et la fermeture de la boîte de dialogue.

## <a name="key-properties-and-methods"></a>Propriétés et méthodes de clé

La propriété de clé du contrôle est <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, qui définit le document à afficher en aperçu. Le document doit être un objet <xref:System.Drawing.Printing.PrintDocument>. Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.Form.ShowDialog%2A>. L’anticrénelage peut rendre le texte plus lisse, mais peut également rendre l’affichage plus lent ; pour l’utiliser, affectez à la propriété <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> la valeur `true`.

Certaines propriétés sont disponibles par le biais de la <xref:System.Windows.Forms.PrintPreviewControl> que la <xref:System.Windows.Forms.PrintPreviewDialog> contient. (Vous n’avez pas à ajouter ce <xref:System.Windows.Forms.PrintPreviewControl> au formulaire ; il est automatiquement contenu dans le <xref:System.Windows.Forms.PrintPreviewDialog> lorsque vous ajoutez la boîte de dialogue à votre formulaire.) Les propriétés <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, qui déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle, sont des exemples de propriétés disponibles par le biais du <xref:System.Windows.Forms.PrintPreviewControl>. Vous pouvez accéder à la propriété <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> en tant que `PrintPreviewDialog1.PrintPreviewControl.Columns` dans Visual Basic, C#`printPreviewDialog1.PrintPreviewControl.Columns` en Visual, ou C++`printPreviewDialog1->PrintPreviewControl->Columns` en Visual.

## <a name="printpreviewdialog-performance"></a>Performances de PrintPreviewDialog

Dans les conditions suivantes, le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> Initialise très lentement :

- Une imprimante réseau est utilisée.
- Les préférences de l’utilisateur pour cette imprimante, telles que les paramètres duplex, sont modifiées.

Pour les applications qui s’exécutent sur le .NET Framework 4.5.2, vous pouvez ajouter la clé suivante à la section \<appSettings > de votre fichier de configuration pour améliorer les performances de l’initialisation de contrôle <xref:System.Windows.Forms.PrintPreviewDialog> :

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Si la clé de `EnablePrintPreviewOptimization` est définie sur une autre valeur, ou si la clé n’est pas présente, l’optimisation n’est pas appliquée.

Pour les applications qui s’exécutent sur le .NET Framework 4,6 ou versions ultérieures, vous pouvez ajouter le commutateur suivant à l’élément [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [\<Runtime >](../../configure-apps/file-schema/runtime/index.md) de votre fichier de configuration d’application :

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Si le commutateur n’est pas présent ou s’il est défini sur une autre valeur, l’optimisation n’est pas appliquée.

Si vous utilisez l’événement <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> pour modifier les paramètres de l’imprimante, les performances du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ne s’améliorent pas même si un commutateur de configuration d’optimisation est défini.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Vue d’ensemble du contrôle PrintPreviewControl](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog, contrôle](printpreviewdialog-control-windows-forms.md)
- [Contrôles et composants de boîte de dialogue](dialog-box-controls-and-components-windows-forms.md)
