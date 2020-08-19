---
title: Nouveautés de .NET Core 3.1
description: Découvrez les nouvelles fonctionnalités de .NET Core 3,1.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 42d4f7e8800bf2d13d584084f8a41bad2ada534f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608122"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="220b2-103">Nouveautés de .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="220b2-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="220b2-104">Cet article décrit les nouveautés de .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="220b2-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="220b2-105">Cette version contient des améliorations mineures apportées à .NET Core 3,0, en se concentrant sur les correctifs les plus petits, mais importants.</span><span class="sxs-lookup"><span data-stu-id="220b2-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="220b2-106">La fonctionnalité la plus importante de .NET Core 3,1 est qu’il s’agit d’une version de [prise en charge à long terme (LTS)](#long-term-support) .</span><span class="sxs-lookup"><span data-stu-id="220b2-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="220b2-107">Si vous utilisez Visual Studio 2019, vous devez effectuer la mise à jour vers [Visual studio 2019 version 16,4 ou ultérieure](https://visualstudio.microsoft.com/downloads/) pour travailler avec les projets .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="220b2-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="220b2-108">Pour plus d’informations sur les nouveautés de Visual Studio version 16,4, consultez [Nouveautés de Visual studio 2019 version 16,4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="220b2-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="220b2-109">Visual Studio pour Mac prend également en charge et comprend .NET Core 3,1 dans Visual Studio pour Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="220b2-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="220b2-110">Pour plus d’informations sur la version, consultez l' [annonce de .net Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="220b2-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="220b2-111">[Téléchargez et commencez à utiliser .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) sur Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="220b2-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="220b2-112">Prise en charge à long terme</span><span class="sxs-lookup"><span data-stu-id="220b2-112">Long-term support</span></span>

<span data-ttu-id="220b2-113">.NET Core 3,1 est une version LTS avec prise en charge de Microsoft au cours des trois prochaines années.</span><span class="sxs-lookup"><span data-stu-id="220b2-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="220b2-114">Il est fortement recommandé de déplacer vos applications vers .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="220b2-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="220b2-115">Le cycle de vie actuel des autres versions majeures est le suivant :</span><span class="sxs-lookup"><span data-stu-id="220b2-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="220b2-116">Libérer</span><span class="sxs-lookup"><span data-stu-id="220b2-116">Release</span></span> | <span data-ttu-id="220b2-117">Remarque</span><span class="sxs-lookup"><span data-stu-id="220b2-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="220b2-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="220b2-118">.NET Core 3.0</span></span> | <span data-ttu-id="220b2-119">Fin de vie le 3 mars 2020.</span><span class="sxs-lookup"><span data-stu-id="220b2-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="220b2-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="220b2-120">.NET Core 2.2</span></span> | <span data-ttu-id="220b2-121">Fin de vie le 23 décembre 2019.</span><span class="sxs-lookup"><span data-stu-id="220b2-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="220b2-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="220b2-122">.NET Core 2.1</span></span> | <span data-ttu-id="220b2-123">Fin de vie le 21 août 2021.</span><span class="sxs-lookup"><span data-stu-id="220b2-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="220b2-124">Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="220b2-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="220b2-125">macOS appHost et notaireisation</span><span class="sxs-lookup"><span data-stu-id="220b2-125">macOS appHost and notarization</span></span>

<span data-ttu-id="220b2-126">*macOS uniquement*</span><span class="sxs-lookup"><span data-stu-id="220b2-126">*macOS only*</span></span>

<span data-ttu-id="220b2-127">À partir de la kit SDK .NET Core authentifiée 3,1 pour macOS, le paramètre appHost est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="220b2-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="220b2-128">Pour plus d’informations, voir [la rubrique sur les téléchargements et les projets MacOS Catalina et l’impact sur les téléchargements et les projets .net Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="220b2-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="220b2-129">Lorsque le paramètre appHost est activé, .NET Core génère un exécutable Mach-O natif quand vous générez ou publiez.</span><span class="sxs-lookup"><span data-stu-id="220b2-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="220b2-130">Votre application s’exécute dans le contexte de appHost lorsqu’elle est exécutée à partir du code source avec la `dotnet run` commande, ou en démarrant directement l’exécutable Mach-O.</span><span class="sxs-lookup"><span data-stu-id="220b2-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="220b2-131">Sans appHost, la seule façon dont un utilisateur peut démarrer une application [dépendante du Framework](../deploying/index.md#publish-framework-dependent) est avec la `dotnet <filename.dll>` commande.</span><span class="sxs-lookup"><span data-stu-id="220b2-131">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="220b2-132">Un appHost est toujours créé lorsque vous publiez votre application [autonome](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="220b2-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="220b2-133">Vous pouvez soit configurer appHost au niveau du projet, soit basculer la appHost d’une commande spécifique `dotnet` avec le `-p:UseAppHost` paramètre :</span><span class="sxs-lookup"><span data-stu-id="220b2-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="220b2-134">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="220b2-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="220b2-135">Paramètre de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="220b2-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="220b2-136">Pour plus d’informations sur le `UseAppHost` paramètre, consultez [propriétés MSBuild pour Microsoft. net. SDK](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="220b2-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="220b2-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="220b2-137">Windows Forms</span></span>

<span data-ttu-id="220b2-138">*Windows uniquement*</span><span class="sxs-lookup"><span data-stu-id="220b2-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="220b2-139">Il existe des modifications avec rupture dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="220b2-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="220b2-140">Les contrôles hérités étaient inclus dans Windows Forms qui n’étaient pas disponibles dans la boîte à outils du concepteur Visual Studio pendant un certain temps.</span><span class="sxs-lookup"><span data-stu-id="220b2-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="220b2-141">Ils ont été remplacés par de nouveaux contrôles dans .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="220b2-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="220b2-142">Celles-ci ont été supprimées du kit de développement logiciel (SDK) pour .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="220b2-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="220b2-143">Contrôle supprimé</span><span class="sxs-lookup"><span data-stu-id="220b2-143">Removed control</span></span> | <span data-ttu-id="220b2-144">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="220b2-144">Recommended replacement</span></span> | <span data-ttu-id="220b2-145">API associées supprimées</span><span class="sxs-lookup"><span data-stu-id="220b2-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="220b2-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="220b2-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="220b2-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="220b2-147">DataGridCell</span></span><br/><span data-ttu-id="220b2-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="220b2-148">DataGridRow</span></span><br/><span data-ttu-id="220b2-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="220b2-149">DataGridTableCollection</span></span><br/><span data-ttu-id="220b2-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="220b2-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="220b2-151">MappingName</span><span class="sxs-lookup"><span data-stu-id="220b2-151">DataGridTableStyle</span></span><br/><span data-ttu-id="220b2-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="220b2-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="220b2-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="220b2-153">DataGridLineStyle</span></span><br/><span data-ttu-id="220b2-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="220b2-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="220b2-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="220b2-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="220b2-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="220b2-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="220b2-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="220b2-157">DataGridTextBox</span></span><br/><span data-ttu-id="220b2-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="220b2-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="220b2-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="220b2-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="220b2-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="220b2-160">HitTestType</span></span> |
| <span data-ttu-id="220b2-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="220b2-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="220b2-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="220b2-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="220b2-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="220b2-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="220b2-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="220b2-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="220b2-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="220b2-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="220b2-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="220b2-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="220b2-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="220b2-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="220b2-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="220b2-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="220b2-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="220b2-169">MenuItemCollection</span></span> |
| <span data-ttu-id="220b2-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="220b2-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="220b2-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="220b2-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="220b2-172">Nous vous recommandons de mettre à jour vos applications vers .NET Core 3,1 et de passer aux contrôles de remplacement.</span><span class="sxs-lookup"><span data-stu-id="220b2-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="220b2-173">Le remplacement des contrôles est un processus simple, essentiellement « Rechercher et remplacer » sur le type.</span><span class="sxs-lookup"><span data-stu-id="220b2-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="220b2-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="220b2-174">C++/CLI</span></span>

<span data-ttu-id="220b2-175">*Windows uniquement*</span><span class="sxs-lookup"><span data-stu-id="220b2-175">*Windows only*</span></span>

<span data-ttu-id="220b2-176">Une prise en charge a été ajoutée pour la création de projets C++/CLI (également appelés « C++ managé »).</span><span class="sxs-lookup"><span data-stu-id="220b2-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="220b2-177">Les fichiers binaires générés à partir de ces projets sont compatibles avec .NET Core 3,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="220b2-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="220b2-178">Pour ajouter la prise en charge de C++/CLI dans Visual Studio 2019 version 16,4, installez la [charge de travail développement Desktop en c++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="220b2-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="220b2-179">Cette charge de travail ajoute deux modèles à Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="220b2-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="220b2-180">Bibliothèque de classes CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="220b2-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="220b2-181">Projet CLR vide (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="220b2-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="220b2-182">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="220b2-182">Next steps</span></span>

- [<span data-ttu-id="220b2-183">Passez en revue les modifications avec rupture entre .NET Core 3,0 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="220b2-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="220b2-184">Passez en revue les dernières modifications apportées à .NET Core 3,1 pour les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="220b2-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
