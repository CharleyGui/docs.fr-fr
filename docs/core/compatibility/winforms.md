---
title: Modifications avec rupture Windows Forms
description: Répertorie les dernières modifications apportées à Windows Forms pour .NET Core 3,0 et 3,1.
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726429"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a><span data-ttu-id="8ffa0-103">Dernières modifications dans Windows Forms pour .NET Core 3,0 et 3,1</span><span class="sxs-lookup"><span data-stu-id="8ffa0-103">Breaking changes in Windows Forms for .NET Core 3.0 and 3.1</span></span>

<span data-ttu-id="8ffa0-104">La prise en charge de Windows Forms a été ajoutée à .NET Core dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ffa0-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="8ffa0-105">Cet article répertorie les dernières modifications apportées à Windows Forms par la version .NET dans laquelle elles ont été introduites.</span><span class="sxs-lookup"><span data-stu-id="8ffa0-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="8ffa0-106">Si vous effectuez la mise à niveau d’une application Windows Forms à partir d' .NET Framework ou d’une version antérieure de .NET Core (3,0 ou version ultérieure), cet article s’applique à vous.</span><span class="sxs-lookup"><span data-stu-id="8ffa0-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="8ffa0-107">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="8ffa0-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8ffa0-108">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="8ffa0-108">Breaking change</span></span> | <span data-ttu-id="8ffa0-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8ffa0-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8ffa0-110">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="8ffa0-110">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="8ffa0-111">3.1</span><span class="sxs-lookup"><span data-stu-id="8ffa0-111">3.1</span></span> |
| [<span data-ttu-id="8ffa0-112">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="8ffa0-112">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="8ffa0-113">3.1</span><span class="sxs-lookup"><span data-stu-id="8ffa0-113">3.1</span></span> |
| [<span data-ttu-id="8ffa0-114">Control. DefaultFont remplacé par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="8ffa0-114">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="8ffa0-115">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-115">3.0</span></span> |
| [<span data-ttu-id="8ffa0-116">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="8ffa0-116">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="8ffa0-117">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-117">3.0</span></span> |
| [<span data-ttu-id="8ffa0-118">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ffa0-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="8ffa0-119">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-119">3.0</span></span> |
| [<span data-ttu-id="8ffa0-120">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-120">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-121">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-121">3.0</span></span> |
| [<span data-ttu-id="8ffa0-122">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-123">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-123">3.0</span></span> |
| [<span data-ttu-id="8ffa0-124">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-124">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-125">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-125">3.0</span></span> |
| [<span data-ttu-id="8ffa0-126">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-126">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-127">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-127">3.0</span></span> |
| [<span data-ttu-id="8ffa0-128">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-129">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-129">3.0</span></span> |
| [<span data-ttu-id="8ffa0-130">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-131">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-131">3.0</span></span> |
| [<span data-ttu-id="8ffa0-132">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-132">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-133">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-133">3.0</span></span> |
| [<span data-ttu-id="8ffa0-134">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8ffa0-134">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="8ffa0-135">3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-135">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="8ffa0-136">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8ffa0-136">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

<span data-ttu-id="8ffa0-137">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8ffa0-137">\*\*_</span></span>

## <a name="net-core-30"></a><span data-ttu-id="8ffa0-138">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8ffa0-138">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

<span data-ttu-id="8ffa0-139">_\*\*</span><span class="sxs-lookup"><span data-stu-id="8ffa0-139">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="8ffa0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ffa0-140">See also</span></span>

- [<span data-ttu-id="8ffa0-141">Portage d’une application Windows Forms vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ffa0-141">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
