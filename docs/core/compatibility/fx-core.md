---
title: Dernières modifications-.NET Framework à .NET Core
titleSuffix: ''
description: Répertorie les modifications avec rupture d' .NET Framework à .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 613c4e41e12be57d5631b347055140a4418e7207
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206460"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="d0a1d-103">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="d0a1d-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="d0a1d-104">Si vous migrez une application à partir de .NET Framework vers .NET Core, les modifications avec rupture mentionnées dans cet article peuvent vous affecter.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="d0a1d-105">Les modifications avec rupture sont regroupées par catégorie et au sein de ces catégories, par la version de .NET Core dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="d0a1d-106">Cet article n’est pas une liste complète des modifications avec rupture entre .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="d0a1d-107">Les modifications critiques les plus importantes sont ajoutées ici, car nous en avons conscience.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="d0a1d-108">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="d0a1d-108">Core .NET libraries</span></span>

- [<span data-ttu-id="d0a1d-109">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="d0a1d-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="d0a1d-110">UnauthorizedAccessException levée par FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="d0a1d-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="d0a1d-111">La gestion des exceptions d’état de processus endommagées n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)
- [<span data-ttu-id="d0a1d-112">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="d0a1d-112">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters)

### <a name="net-core-21"></a><span data-ttu-id="d0a1d-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d0a1d-113">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="d0a1d-114">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="d0a1d-114">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

## <a name="cryptography"></a><span data-ttu-id="d0a1d-115">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="d0a1d-115">Cryptography</span></span>

- [<span data-ttu-id="d0a1d-116">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="d0a1d-116">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="d0a1d-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d0a1d-117">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a><span data-ttu-id="d0a1d-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d0a1d-118">MSBuild</span></span>

- [<span data-ttu-id="d0a1d-119">Changement de nom de fichier manifeste de ressource</span><span class="sxs-lookup"><span data-stu-id="d0a1d-119">Resource manifest file name change</span></span>](#resource-manifest-file-name-change)

### <a name="net-core-30"></a><span data-ttu-id="d0a1d-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d0a1d-120">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a><span data-ttu-id="d0a1d-121">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="d0a1d-121">Networking</span></span>

- [<span data-ttu-id="d0a1d-122">WebClient. CancelAsync n’est pas toujours annulé immédiatement</span><span class="sxs-lookup"><span data-stu-id="d0a1d-122">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a><span data-ttu-id="d0a1d-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d0a1d-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="d0a1d-124">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0a1d-124">Windows Forms</span></span>

<span data-ttu-id="d0a1d-125">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-125">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="d0a1d-126">Si vous effectuez la migration d’une application Windows Forms à partir de .NET Framework vers .NET Core, les modifications avec rupture répertoriées ici peuvent affecter votre application.</span><span class="sxs-lookup"><span data-stu-id="d0a1d-126">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="d0a1d-127">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="d0a1d-127">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="d0a1d-128">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="d0a1d-128">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="d0a1d-129">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="d0a1d-129">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="d0a1d-130">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="d0a1d-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="d0a1d-131">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0a1d-131">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="d0a1d-132">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-133">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-133">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-134">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-134">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-135">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-135">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-136">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-137">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-137">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-138">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-139">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0a1d-139">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="d0a1d-140">Changement d’accès pour AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="d0a1d-140">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="d0a1d-141">API dupliquées supprimées de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0a1d-141">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="d0a1d-142">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d0a1d-142">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="d0a1d-143">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d0a1d-143">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d0a1d-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0a1d-144">See also</span></span>

- [<span data-ttu-id="d0a1d-145">API qui lèvent toujours des exceptions sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="d0a1d-145">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="d0a1d-146">Technologies .NET Framework non disponibles sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="d0a1d-146">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
