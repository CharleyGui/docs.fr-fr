---
title: Modifications avec rupture, .NET Framework à .NET Core 3,0-.NET Core
description: Répertorie les modifications avec rupture de .NET Framework à .NET Core 3,0 pour Windows Forms et Windows Presentation Foundation.
ms.date: 09/10/2019
ms.openlocfilehash: a374e35192c7aad07e986e0e0b75039642744edc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089575"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a><span data-ttu-id="613c5-103">Dernières modifications pour la migration de .NET Framework vers .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="613c5-103">Breaking changes for migration from .NET Framework to .NET Core 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="613c5-104">Cet article est en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="613c5-104">This article is under construction.</span></span> <span data-ttu-id="613c5-105">Il ne s’agit pas d’une liste complète des modifications avec rupture de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="613c5-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="613c5-106">Pour plus d’informations sur les modifications avec rupture de .NET Core, vous pouvez examiner les [problèmes liés](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) à l’évolution de la rupture dans le référentiel dotnet/docs sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="613c5-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="613c5-107">Si vous migrez une application Windows Forms ou Windows Presentation Foundation à partir de .NET Framework vers .NET Core 3,0, consultez les rubriques suivantes pour connaître les dernières modifications susceptibles d’affecter votre application :</span><span class="sxs-lookup"><span data-stu-id="613c5-107">If you are migrating a Windows Forms or Windows Presentation Foundation application from .NET Framework to .NET Core 3.0, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="windows-forms"></a><span data-ttu-id="613c5-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="613c5-108">Windows Forms</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]
