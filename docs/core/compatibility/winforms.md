---
title: Modifications avec rupture Windows Forms
description: Répertorie les dernières modifications apportées à Windows Forms pour .NET Core et .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678996"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="8ea40-103">Modifications avec rupture dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ea40-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="8ea40-104">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ea40-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="8ea40-105">Cet article répertorie les dernières modifications apportées à Windows Forms par la version .NET dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="8ea40-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="8ea40-106">Si vous effectuez la mise à niveau d’une application Windows Forms à partir d' .NET Framework ou d’une version antérieure de .NET Core (3,0 ou version ultérieure), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="8ea40-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="8ea40-107">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="8ea40-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8ea40-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="8ea40-108">Breaking change</span></span> | <span data-ttu-id="8ea40-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8ea40-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8ea40-110">OutputType défini sur WinExe pour les applications WPF et WinForms</span><span class="sxs-lookup"><span data-stu-id="8ea40-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="8ea40-111">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-111">5.0</span></span> |
| [<span data-ttu-id="8ea40-112">Les API liées à DataGridView lèvent désormais InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="8ea40-112">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="8ea40-113">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-113">5.0</span></span> |
| [<span data-ttu-id="8ea40-114">WinForms et les applications WPF utilisent Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="8ea40-114">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="8ea40-115">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-115">5.0</span></span> |
| [<span data-ttu-id="8ea40-116">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="8ea40-116">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="8ea40-117">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-117">5.0</span></span> |
| [<span data-ttu-id="8ea40-118">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="8ea40-118">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="8ea40-119">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-119">5.0</span></span> |
| [<span data-ttu-id="8ea40-120">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="8ea40-120">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="8ea40-121">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-121">5.0</span></span> |
| [<span data-ttu-id="8ea40-122">Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="8ea40-122">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="8ea40-123">5.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-123">5.0</span></span> |
| [<span data-ttu-id="8ea40-124">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="8ea40-124">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="8ea40-125">3.1</span><span class="sxs-lookup"><span data-stu-id="8ea40-125">3.1</span></span> |
| [<span data-ttu-id="8ea40-126">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="8ea40-126">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="8ea40-127">3.1</span><span class="sxs-lookup"><span data-stu-id="8ea40-127">3.1</span></span> |
| [<span data-ttu-id="8ea40-128">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="8ea40-128">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="8ea40-129">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-129">3.0</span></span> |
| [<span data-ttu-id="8ea40-130">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="8ea40-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="8ea40-131">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-131">3.0</span></span> |
| [<span data-ttu-id="8ea40-132">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ea40-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="8ea40-133">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-133">3.0</span></span> |
| [<span data-ttu-id="8ea40-134">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-134">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-135">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-135">3.0</span></span> |
| [<span data-ttu-id="8ea40-136">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-137">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-137">3.0</span></span> |
| [<span data-ttu-id="8ea40-138">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-138">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-139">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-139">3.0</span></span> |
| [<span data-ttu-id="8ea40-140">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-140">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-141">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-141">3.0</span></span> |
| [<span data-ttu-id="8ea40-142">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-142">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-143">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-143">3.0</span></span> |
| [<span data-ttu-id="8ea40-144">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-144">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-145">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-145">3.0</span></span> |
| [<span data-ttu-id="8ea40-146">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-146">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-147">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-147">3.0</span></span> |
| [<span data-ttu-id="8ea40-148">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ea40-148">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="8ea40-149">3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-149">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="8ea40-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8ea40-150">.NET 5.0</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="8ea40-151">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8ea40-151">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="8ea40-152">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8ea40-152">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ea40-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ea40-153">See also</span></span>

- [<span data-ttu-id="8ea40-154">Portage d’une application Windows Forms vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ea40-154">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
