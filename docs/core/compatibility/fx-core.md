---
title: Breaking changes - .NET Framework to .NET Core
titleSuffix: ''
description: Répertorie les changements de rupture de .NET Framework à .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: ef16132c8dcffbe9bcfbe02834c9a78d6d0c33e4
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021797"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="bce3f-103">Breaking changes for migration from .NET Framework to .NET Core</span><span class="sxs-lookup"><span data-stu-id="bce3f-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="bce3f-104">Si vous migrez une application de .NET Framework à .NET Core, les modifications de rupture énumérées dans cet article peuvent vous affecter.</span><span class="sxs-lookup"><span data-stu-id="bce3f-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="bce3f-105">Les changements de rupture sont regroupés par catégorie, et dans ces catégories, par la version de .NET Core dans lequel ils ont été introduits.</span><span class="sxs-lookup"><span data-stu-id="bce3f-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="bce3f-106">Cet article n’est pas une liste complète des changements de rupture entre .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bce3f-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="bce3f-107">Les changements de rupture les plus importants sont ajoutés ici que nous prenons conscience d’eux.</span><span class="sxs-lookup"><span data-stu-id="bce3f-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="bce3f-108">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="bce3f-108">Core .NET libraries</span></span>

- [<span data-ttu-id="bce3f-109">Variation de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="bce3f-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="bce3f-110">UnauthorizedAccessException jeté par FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="bce3f-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="bce3f-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bce3f-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="bce3f-112">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="bce3f-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="bce3f-113">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="bce3f-113">Cryptography</span></span>

- [<span data-ttu-id="bce3f-114">Boolean paramètre de SignedCms.ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="bce3f-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="bce3f-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bce3f-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="bce3f-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bce3f-116">Windows Forms</span></span>

<span data-ttu-id="bce3f-117">Windows Forms support a été ajouté à .NET Core dans la version 3.0.</span><span class="sxs-lookup"><span data-stu-id="bce3f-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="bce3f-118">Si vous migrez une application Windows Forms de .NET Framework à .NET Core, les modifications de rupture énumérées ici peuvent affecter votre application.</span><span class="sxs-lookup"><span data-stu-id="bce3f-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="bce3f-119">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="bce3f-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="bce3f-120">CellFormatting événement non soulevé si tooltip est montré</span><span class="sxs-lookup"><span data-stu-id="bce3f-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="bce3f-121">Control.DefaultFont changé en Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="bce3f-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="bce3f-122">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="bce3f-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="bce3f-123">SerializableAttribute supprimé de certains types de formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="bce3f-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="bce3f-124">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-125">DomainUpDown.UseLegacyScrolling commutation compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-126">DoNotLoadLatestRichEditControl commutateur de compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-127">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-128">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-129">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-130">UtiliserLegacyContextMenuStripSourceControlValue commutateur de compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-131">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bce3f-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="bce3f-132">Changement d’accès pour AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="bce3f-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="bce3f-133">API dupliquée supprimée des formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="bce3f-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="bce3f-134">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="bce3f-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="bce3f-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bce3f-135">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bce3f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bce3f-136">See also</span></span>

- [<span data-ttu-id="bce3f-137">API qui jettent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="bce3f-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="bce3f-138">Technologies .NET Framework non disponibles sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="bce3f-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
