---
title: Modifications avec rupture Windows Forms
description: Répertorie les dernières modifications apportées à Windows Forms pour .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 75d369c7fb999da81a50fe46716e125c3840eb7a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158435"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="deac5-103">Modifications avec rupture dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="deac5-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="deac5-104">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="deac5-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="deac5-105">Cet article répertorie les modifications avec rupture pour Windows Forms par la version de .NET Core dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="deac5-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="deac5-106">Si vous effectuez la mise à niveau d’une application Windows Forms à partir d' .NET Framework ou d’une version antérieure de .NET Core (3,0 ou version ultérieure), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="deac5-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="deac5-107">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="deac5-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="deac5-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="deac5-108">Breaking change</span></span> | <span data-ttu-id="deac5-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="deac5-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="deac5-110">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="deac5-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="deac5-111">5.0</span><span class="sxs-lookup"><span data-stu-id="deac5-111">5.0</span></span> |
| [<span data-ttu-id="deac5-112">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="deac5-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="deac5-113">5.0</span><span class="sxs-lookup"><span data-stu-id="deac5-113">5.0</span></span> |
| [<span data-ttu-id="deac5-114">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="deac5-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="deac5-115">5.0</span><span class="sxs-lookup"><span data-stu-id="deac5-115">5.0</span></span> |
| [<span data-ttu-id="deac5-116">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="deac5-116">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="deac5-117">3.1</span><span class="sxs-lookup"><span data-stu-id="deac5-117">3.1</span></span> |
| [<span data-ttu-id="deac5-118">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="deac5-118">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="deac5-119">3.1</span><span class="sxs-lookup"><span data-stu-id="deac5-119">3.1</span></span> |
| [<span data-ttu-id="deac5-120">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="deac5-120">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="deac5-121">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-121">3.0</span></span> |
| [<span data-ttu-id="deac5-122">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="deac5-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="deac5-123">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-123">3.0</span></span> |
| [<span data-ttu-id="deac5-124">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="deac5-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="deac5-125">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-125">3.0</span></span> |
| [<span data-ttu-id="deac5-126">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-126">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="deac5-127">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-127">3.0</span></span> |
| [<span data-ttu-id="deac5-128">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-128">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="deac5-129">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-129">3.0</span></span> |
| [<span data-ttu-id="deac5-130">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-130">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="deac5-131">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-131">3.0</span></span> |
| [<span data-ttu-id="deac5-132">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-132">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="deac5-133">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-133">3.0</span></span> |
| [<span data-ttu-id="deac5-134">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-134">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="deac5-135">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-135">3.0</span></span> |
| [<span data-ttu-id="deac5-136">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-136">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="deac5-137">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-137">3.0</span></span> |
| [<span data-ttu-id="deac5-138">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="deac5-139">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-139">3.0</span></span> |
| [<span data-ttu-id="deac5-140">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="deac5-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="deac5-141">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-141">3.0</span></span> |
| [<span data-ttu-id="deac5-142">Changement d’accès pour AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="deac5-142">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="deac5-143">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-143">3.0</span></span> |
| [<span data-ttu-id="deac5-144">API dupliquées supprimées de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="deac5-144">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="deac5-145">3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-145">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="deac5-146">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="deac5-146">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="deac5-147">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="deac5-147">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="deac5-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="deac5-148">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="deac5-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deac5-149">See also</span></span>

- [<span data-ttu-id="deac5-150">Portage d’une application Windows Forms vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="deac5-150">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
