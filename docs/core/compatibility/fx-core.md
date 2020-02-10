---
title: Dernières modifications-.NET Framework à .NET Core
titleSuffix: ''
description: Répertorie les modifications avec rupture d' .NET Framework à .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 407f99adf5d400fce659ef71cda32ceac1e54491
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093056"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Dernières modifications pour la migration de .NET Framework vers .NET Core

Si vous migrez une application à partir de .NET Framework vers .NET Core, les modifications avec rupture mentionnées dans cet article peuvent vous affecter. Les modifications avec rupture sont regroupées par catégorie et, dans ces catégories, par la version de .NET Core dans laquelle elles ont été introduites.

> [!NOTE]
> Cet article n’est pas une liste complète des modifications avec rupture entre .NET Framework et .NET Core. Les modifications critiques les plus importantes sont ajoutées ici, car nous en avons conscience.

## <a name="corefx"></a>CoreFx

- [Modification de la valeur par défaut de UseShellExecute](#change-in-default-value-of-useshellexecute)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a>Windows Forms

La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0. Si vous effectuez la migration d’une application Windows Forms à partir de .NET Framework vers .NET Core, les modifications avec rupture répertoriées ici peuvent affecter votre application.

- [Contrôles supprimés](#removed-controls)
- [Événement CellFormatting non déclenché si l’info-bulle est affichée](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control. DefaultFont remplacé par Segoe UI 9 PT](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernisation du FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute supprimé de certains types de Windows Forms](#serializableattribute-removed-from-some-windows-forms-types)
- [Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Commutateur de compatibilité EnableVisualStyleValidation non pris en charge](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Commutateur de compatibilité UseLegacyImages non pris en charge](#uselegacyimages-compatibility-switch-not-supported)
- [Changement d’accès pour AccessibleObject. RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [API dupliquées supprimées de Windows Forms](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Voir aussi

- [API qui lèvent toujours des exceptions sur .NET Core](unsupported-apis.md)
- [Technologies de .NET Framework indisponibles sur .NET Core](../porting/net-framework-tech-unavailable.md)
