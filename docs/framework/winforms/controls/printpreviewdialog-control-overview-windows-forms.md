---
title: Vue d'ensemble du contrôle PrintPreviewDialog (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce6bf9cb9872183e60e6ccdf7eaf79b6630db51
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053695"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Vue d’ensemble du contrôle PrintPreviewDialog (Windows Forms)

Les formulaires Windows <xref:System.Windows.Forms.PrintPreviewDialog> contrôle est une boîte de dialogue préconfigurée permettant d’afficher comment un [PrintDocument](printdocument-component-windows-forms.md) apparaîtra une fois imprimé. Utilisez-la dans votre application Windows comme une solution simple au lieu de configurer votre propre boîte de dialogue. Le contrôle contient des boutons pour l'impression, le zoom avant, l'affichage d'une ou plusieurs pages et la fermeture de la boîte de dialogue.

## <a name="key-properties-and-methods"></a>Méthodes et propriétés de clé

Propriété de clé du contrôle est <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, qui définit le document à afficher. Le document doit être un <xref:System.Drawing.Printing.PrintDocument> objet. Pour afficher la boîte de dialogue, vous devez appeler son <xref:System.Windows.Forms.Form.ShowDialog%2A> (méthode). L’anticrénelage peut lisser le texte, mais il peut également apporter de ralentir l’affichage ; pour l’utiliser, définissez la <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriété `true`.

Certaines propriétés sont disponibles via le <xref:System.Windows.Forms.PrintPreviewControl> qui le <xref:System.Windows.Forms.PrintPreviewDialog> contient. (Vous n’avez pas à l’ajouter <xref:System.Windows.Forms.PrintPreviewControl> au formulaire ; il est automatiquement contenu dans le <xref:System.Windows.Forms.PrintPreviewDialog> lorsque vous ajoutez la boîte de dialogue à votre formulaire.) Les propriétés disponibles via le <xref:System.Windows.Forms.PrintPreviewControl> sont le <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> qui déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle. Vous pouvez accéder à la <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> propriété en tant que `PrintPreviewDialog1.PrintPreviewControl.Columns` en Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` dans Visual C#, ou `printPreviewDialog1->PrintPreviewControl->Columns` dans Visual C++.

## <a name="printpreviewdialog-performance"></a>Performances de PrintPreviewDialog

Dans les conditions suivantes, le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle initialise très lentement :

- Une imprimante réseau est utilisée.
- Préférences utilisateur pour cette imprimante, tels que les paramètres duplex, sont modifiées.

Pour les applications qui s’exécutent sur le .NET Framework 4.5.2, vous pouvez ajouter la clé suivante à la \<appSettings > section de votre fichier de configuration pour améliorer les performances de <xref:System.Windows.Forms.PrintPreviewDialog> contrôlent l’initialisation :

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Si le `EnablePrintPreviewOptimization` clé est définie pour toute autre valeur, ou si la clé n’est pas présente, l’optimisation n’est pas appliquée.

Pour les applications qui s’exécutent sur le .NET Framework 4.6 ou versions ultérieures, vous pouvez ajouter le commutateur suivant à la [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) section de votre fichier de configuration d’application :

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Si le commutateur n’est pas présent ou si elle est définie sur une autre valeur, l’optimisation n’est pas appliquée.

Si vous utilisez le <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> événement pour modifier les paramètres d’imprimante, les performances de la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle n’améliorera pas même si un commutateur de configuration de l’optimisation est défini.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Vue d’ensemble du contrôle PrintPreviewControl](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog, contrôle](printpreviewdialog-control-windows-forms.md)
- [Contrôles et composants de boîte de dialogue](dialog-box-controls-and-components-windows-forms.md)
