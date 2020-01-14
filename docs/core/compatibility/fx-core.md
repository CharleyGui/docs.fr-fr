---
title: Dernières modifications-.NET Framework à .NET Core
description: Répertorie les modifications avec rupture d' .NET Framework à .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 9f4ecc8a9de7279bb4b222b3df77e1eb17b33f0a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937392"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="2b28f-103">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b28f-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="2b28f-104">Si vous migrez une application à partir de .NET Framework vers .NET Core, les modifications avec rupture mentionnées dans cet article peuvent vous affecter.</span><span class="sxs-lookup"><span data-stu-id="2b28f-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="2b28f-105">Les modifications avec rupture sont regroupées par catégorie et, dans ces catégories, par la version de .NET Core dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="2b28f-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="2b28f-106">Cet article n’est pas une liste complète des modifications avec rupture entre .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b28f-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="2b28f-107">Les modifications critiques les plus importantes sont ajoutées ici, car nous en avons conscience.</span><span class="sxs-lookup"><span data-stu-id="2b28f-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="2b28f-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="2b28f-108">CoreFx</span></span>

<span data-ttu-id="2b28f-109">Changements cassants :</span><span class="sxs-lookup"><span data-stu-id="2b28f-109">Breaking changes:</span></span>

- [<span data-ttu-id="2b28f-110">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="2b28f-110">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

***

### <a name="net-core-21"></a><span data-ttu-id="2b28f-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2b28f-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="2b28f-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b28f-112">Windows Forms</span></span>

<span data-ttu-id="2b28f-113">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="2b28f-113">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="2b28f-114">Si vous effectuez la migration d’une application Windows Forms à partir de .NET Framework vers .NET Core, les modifications avec rupture répertoriées ici peuvent affecter votre application.</span><span class="sxs-lookup"><span data-stu-id="2b28f-114">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

<span data-ttu-id="2b28f-115">Changements cassants :</span><span class="sxs-lookup"><span data-stu-id="2b28f-115">Breaking changes:</span></span>

- [<span data-ttu-id="2b28f-116">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="2b28f-116">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="2b28f-117">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="2b28f-117">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="2b28f-118">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="2b28f-118">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="2b28f-119">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="2b28f-119">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="2b28f-120">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b28f-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="2b28f-121">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-121">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-122">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-123">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-123">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-124">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-124">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-125">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-125">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-126">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-126">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-127">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-127">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-128">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2b28f-128">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="2b28f-129">Changement d’accès pour AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="2b28f-129">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="2b28f-130">API dupliquées supprimées de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b28f-130">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="2b28f-131">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2b28f-131">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="2b28f-132">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2b28f-132">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2b28f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b28f-133">See also</span></span>

- [<span data-ttu-id="2b28f-134">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b28f-134">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="2b28f-135">Technologies de .NET Framework indisponibles sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b28f-135">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
