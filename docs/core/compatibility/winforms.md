---
title: Formulaires Windows brisant les changements
description: Répertorie les modifications de rupture dans les formulaires Windows pour .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888116"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="1269a-103">Briser les changements dans les formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="1269a-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="1269a-104">Windows Forms support a été ajouté à .NET Core dans la version 3.0.</span><span class="sxs-lookup"><span data-stu-id="1269a-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1269a-105">Cet article répertorie les modifications de rupture pour les formulaires Windows par la version .NET Core dans laquelle ils ont été introduits.</span><span class="sxs-lookup"><span data-stu-id="1269a-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="1269a-106">Si vous mise à niveau d’une application Windows Forms à partir de .NET Framework ou d’une version précédente de .NET Core (3.0 ou plus tard), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="1269a-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="1269a-107">Les modifications de rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="1269a-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1269a-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="1269a-108">Breaking change</span></span> | <span data-ttu-id="1269a-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1269a-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="1269a-110">WinForms API maintenant jeter ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="1269a-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="1269a-111">5.0</span><span class="sxs-lookup"><span data-stu-id="1269a-111">5.0</span></span> |
| [<span data-ttu-id="1269a-112">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="1269a-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="1269a-113">3.1</span><span class="sxs-lookup"><span data-stu-id="1269a-113">3.1</span></span> |
| [<span data-ttu-id="1269a-114">CellFormatting événement non soulevé si tooltip est montré</span><span class="sxs-lookup"><span data-stu-id="1269a-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="1269a-115">3.1</span><span class="sxs-lookup"><span data-stu-id="1269a-115">3.1</span></span> |
| [<span data-ttu-id="1269a-116">Control.DefaultFont changé en Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="1269a-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="1269a-117">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-117">3.0</span></span> |
| [<span data-ttu-id="1269a-118">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="1269a-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="1269a-119">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-119">3.0</span></span> |
| [<span data-ttu-id="1269a-120">SerializableAttribute supprimé de certains types de formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="1269a-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="1269a-121">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-121">3.0</span></span> |
| [<span data-ttu-id="1269a-122">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="1269a-123">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-123">3.0</span></span> |
| [<span data-ttu-id="1269a-124">DomainUpDown.UseLegacyScrolling commutation compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="1269a-125">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-125">3.0</span></span> |
| [<span data-ttu-id="1269a-126">DoNotLoadLatestRichEditControl commutateur de compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="1269a-127">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-127">3.0</span></span> |
| [<span data-ttu-id="1269a-128">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="1269a-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-129">3.0</span></span> |
| [<span data-ttu-id="1269a-130">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="1269a-131">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-131">3.0</span></span> |
| [<span data-ttu-id="1269a-132">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="1269a-133">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-133">3.0</span></span> |
| [<span data-ttu-id="1269a-134">UtiliserLegacyContextMenuStripSourceControlValue commutateur de compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="1269a-135">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-135">3.0</span></span> |
| [<span data-ttu-id="1269a-136">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1269a-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="1269a-137">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-137">3.0</span></span> |
| [<span data-ttu-id="1269a-138">Changement d’accès pour AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="1269a-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="1269a-139">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-139">3.0</span></span> |
| [<span data-ttu-id="1269a-140">API dupliquée supprimée des formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="1269a-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="1269a-141">3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1269a-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1269a-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="1269a-143">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1269a-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="1269a-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1269a-144">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1269a-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1269a-145">See also</span></span>

- [<span data-ttu-id="1269a-146">Port a Windows Forms app to .NET Core</span><span class="sxs-lookup"><span data-stu-id="1269a-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
