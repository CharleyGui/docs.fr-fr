---
title: Modifications avec rupture Windows Forms
description: Répertorie les dernières modifications apportées à Windows Forms pour .NET Core et .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: c3d2d23601d6a2d9d44761c4371fe34d3d5ed1f3
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656333"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="041af-103">Modifications avec rupture dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="041af-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="041af-104">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="041af-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="041af-105">Cet article répertorie les dernières modifications apportées à Windows Forms par la version .NET dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="041af-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="041af-106">Si vous effectuez la mise à niveau d’une application Windows Forms à partir d' .NET Framework ou d’une version antérieure de .NET Core (3,0 ou version ultérieure), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="041af-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="041af-107">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="041af-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="041af-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="041af-108">Breaking change</span></span> | <span data-ttu-id="041af-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="041af-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="041af-110">Les API liées à DataGridView lèvent désormais InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="041af-110">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="041af-111">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-111">5.0</span></span> |
| [<span data-ttu-id="041af-112">WinForms et les applications WPF utilisent Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="041af-112">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="041af-113">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-113">5.0</span></span> |
| [<span data-ttu-id="041af-114">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="041af-114">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="041af-115">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-115">5.0</span></span> |
| [<span data-ttu-id="041af-116">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="041af-116">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="041af-117">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-117">5.0</span></span> |
| [<span data-ttu-id="041af-118">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="041af-118">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="041af-119">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-119">5.0</span></span> |
| [<span data-ttu-id="041af-120">Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="041af-120">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="041af-121">5.0</span><span class="sxs-lookup"><span data-stu-id="041af-121">5.0</span></span> |
| [<span data-ttu-id="041af-122">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="041af-122">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="041af-123">3.1</span><span class="sxs-lookup"><span data-stu-id="041af-123">3.1</span></span> |
| [<span data-ttu-id="041af-124">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="041af-124">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="041af-125">3.1</span><span class="sxs-lookup"><span data-stu-id="041af-125">3.1</span></span> |
| [<span data-ttu-id="041af-126">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="041af-126">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="041af-127">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-127">3.0</span></span> |
| [<span data-ttu-id="041af-128">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="041af-128">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="041af-129">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-129">3.0</span></span> |
| [<span data-ttu-id="041af-130">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="041af-130">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="041af-131">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-131">3.0</span></span> |
| [<span data-ttu-id="041af-132">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="041af-133">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-133">3.0</span></span> |
| [<span data-ttu-id="041af-134">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-134">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="041af-135">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-135">3.0</span></span> |
| [<span data-ttu-id="041af-136">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-136">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="041af-137">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-137">3.0</span></span> |
| [<span data-ttu-id="041af-138">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-138">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="041af-139">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-139">3.0</span></span> |
| [<span data-ttu-id="041af-140">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-140">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="041af-141">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-141">3.0</span></span> |
| [<span data-ttu-id="041af-142">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-142">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="041af-143">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-143">3.0</span></span> |
| [<span data-ttu-id="041af-144">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-144">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="041af-145">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-145">3.0</span></span> |
| [<span data-ttu-id="041af-146">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="041af-146">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="041af-147">3.0</span><span class="sxs-lookup"><span data-stu-id="041af-147">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="041af-148">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="041af-148">.NET 5.0</span></span>

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

## <a name="net-core-31"></a><span data-ttu-id="041af-149">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="041af-149">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="041af-150">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="041af-150">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="041af-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="041af-151">See also</span></span>

- [<span data-ttu-id="041af-152">Portage d’une application Windows Forms vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="041af-152">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
