---
title: Modifications avec rupture Windows Forms
description: Répertorie les dernières modifications apportées à Windows Forms pour .NET Core et .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: 2311faab026bf1dfde348e231937eff73ec46172
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804857"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="3064c-103">Modifications avec rupture dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3064c-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="3064c-104">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="3064c-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="3064c-105">Cet article répertorie les dernières modifications apportées à Windows Forms par la version .NET dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="3064c-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="3064c-106">Si vous effectuez la mise à niveau d’une application Windows Forms à partir d' .NET Framework ou d’une version antérieure de .NET Core (3,0 ou version ultérieure), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="3064c-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="3064c-107">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="3064c-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3064c-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="3064c-108">Breaking change</span></span> | <span data-ttu-id="3064c-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3064c-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3064c-110">DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés</span><span class="sxs-lookup"><span data-stu-id="3064c-110">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="3064c-111">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-111">5.0</span></span> |
| [<span data-ttu-id="3064c-112">OutputType défini sur WinExe pour les applications WPF et WinForms</span><span class="sxs-lookup"><span data-stu-id="3064c-112">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="3064c-113">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-113">5.0</span></span> |
| [<span data-ttu-id="3064c-114">Les API liées à DataGridView lèvent désormais InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="3064c-114">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="3064c-115">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-115">5.0</span></span> |
| [<span data-ttu-id="3064c-116">WinForms et les applications WPF utilisent Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="3064c-116">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="3064c-117">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-117">5.0</span></span> |
| [<span data-ttu-id="3064c-118">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="3064c-118">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="3064c-119">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-119">5.0</span></span> |
| [<span data-ttu-id="3064c-120">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="3064c-120">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="3064c-121">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-121">5.0</span></span> |
| [<span data-ttu-id="3064c-122">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="3064c-122">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="3064c-123">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-123">5.0</span></span> |
| [<span data-ttu-id="3064c-124">Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="3064c-124">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="3064c-125">5.0</span><span class="sxs-lookup"><span data-stu-id="3064c-125">5.0</span></span> |
| [<span data-ttu-id="3064c-126">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="3064c-126">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="3064c-127">3.1</span><span class="sxs-lookup"><span data-stu-id="3064c-127">3.1</span></span> |
| [<span data-ttu-id="3064c-128">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="3064c-128">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="3064c-129">3.1</span><span class="sxs-lookup"><span data-stu-id="3064c-129">3.1</span></span> |
| [<span data-ttu-id="3064c-130">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="3064c-130">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="3064c-131">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-131">3.0</span></span> |
| [<span data-ttu-id="3064c-132">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="3064c-132">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="3064c-133">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-133">3.0</span></span> |
| [<span data-ttu-id="3064c-134">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3064c-134">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="3064c-135">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-135">3.0</span></span> |
| [<span data-ttu-id="3064c-136">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-136">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="3064c-137">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-137">3.0</span></span> |
| [<span data-ttu-id="3064c-138">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-138">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="3064c-139">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-139">3.0</span></span> |
| [<span data-ttu-id="3064c-140">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-140">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="3064c-141">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-141">3.0</span></span> |
| [<span data-ttu-id="3064c-142">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-142">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="3064c-143">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-143">3.0</span></span> |
| [<span data-ttu-id="3064c-144">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-144">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="3064c-145">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-145">3.0</span></span> |
| [<span data-ttu-id="3064c-146">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-146">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="3064c-147">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-147">3.0</span></span> |
| [<span data-ttu-id="3064c-148">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-148">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="3064c-149">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-149">3.0</span></span> |
| [<span data-ttu-id="3064c-150">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3064c-150">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="3064c-151">3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-151">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="3064c-152">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3064c-152">.NET 5.0</span></span>

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

***

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

## <a name="net-core-31"></a><span data-ttu-id="3064c-153">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3064c-153">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="3064c-154">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3064c-154">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3064c-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3064c-155">See also</span></span>

- [<span data-ttu-id="3064c-156">Portage d’une application Windows Forms vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="3064c-156">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
