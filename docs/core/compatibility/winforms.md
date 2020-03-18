---
title: Formulaires Windows brisant les changements
description: Répertorie les modifications de rupture dans les formulaires Windows pour .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399097"
---
# <a name="breaking-changes-in-windows-forms"></a>Briser les changements dans les formulaires Windows

Windows Forms support a été ajouté à .NET Core dans la version 3.0. Cet article répertorie les modifications de rupture pour les formulaires Windows par la version .NET Core dans laquelle ils ont été introduits. Si vous mise à niveau d’une application Windows Forms à partir de .NET Framework ou d’une version précédente de .NET Core (3.0 ou plus tard), cet article s’applique à vous.

Les modifications de rupture suivantes sont documentées sur cette page :

- [Contrôles supprimés](#removed-controls)
- [CellFormatting événement non soulevé si tooltip est montré](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont changé en Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernisation du FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute supprimé de certains types de formulaires Windows](#serializableattribute-removed-from-some-windows-forms-types)
- [Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [DomainUpDown.UseLegacyScrolling commutation compatibilité non pris en charge](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [DoNotLoadLatestRichEditControl commutateur de compatibilité non pris en charge](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Commutateur de compatibilité EnableVisualStyleValidation non pris en charge](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UtiliserLegacyContextMenuStripSourceControlValue commutateur de compatibilité non pris en charge](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Commutateur de compatibilité UseLegacyImages non pris en charge](#uselegacyimages-compatibility-switch-not-supported)
- [Changement d’accès pour AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [API dupliquée supprimée des formulaires Windows](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Voir aussi

- [Port a Windows Forms app to .NET Core](../porting/winforms.md)
