---
title: Nouveautés de .NET Core 3.1
description: Découvrez les nouvelles fonctionnalités trouvées dans .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b52615a3fb288a6ca0622deb83f4db3c8e3587fb
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607904"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="ec881-103">Nouveautés de .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ec881-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="ec881-104">Cet article décrit ce qui est nouveau dans .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ec881-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="ec881-105">Cette version contient des améliorations mineures à .NET Core 3.0, en se concentrant sur les petites, mais importantes, correctifs.</span><span class="sxs-lookup"><span data-stu-id="ec881-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="ec881-106">La caractéristique la plus importante sur .NET Core 3.1 est qu’il s’agit d’une [version de support à long terme (LTS).](#long-term-support)</span><span class="sxs-lookup"><span data-stu-id="ec881-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="ec881-107">Si vous utilisez Visual Studio 2019, vous devez mettre à jour sur [Visual Studio 2019 version 16.4 ou plus tard](https://visualstudio.microsoft.com/downloads/) pour travailler avec des projets .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ec881-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="ec881-108">Pour plus d’informations sur ce qui est nouveau dans Visual Studio version 16.4, voir [What’s New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="ec881-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="ec881-109">Visual Studio for Mac prend également en charge et inclut .NET Core 3.1 dans Visual Studio pour Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="ec881-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="ec881-110">Pour plus d’informations sur la version, voir [l’annonce .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="ec881-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="ec881-111">[Téléchargez et lancez-vous avec .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) sur Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="ec881-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="ec881-112">Prise en charge à long terme</span><span class="sxs-lookup"><span data-stu-id="ec881-112">Long-term support</span></span>

<span data-ttu-id="ec881-113">.NET Core 3.1 est une version LTS avec le soutien de Microsoft pour les trois prochaines années.</span><span class="sxs-lookup"><span data-stu-id="ec881-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="ec881-114">Il est fortement recommandé de déplacer vos applications vers .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ec881-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="ec881-115">Le cycle de vie actuel d’autres versions majeures est le suivant :</span><span class="sxs-lookup"><span data-stu-id="ec881-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="ec881-116">Libérer</span><span class="sxs-lookup"><span data-stu-id="ec881-116">Release</span></span> | <span data-ttu-id="ec881-117">Remarque</span><span class="sxs-lookup"><span data-stu-id="ec881-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="ec881-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ec881-118">.NET Core 3.0</span></span> | <span data-ttu-id="ec881-119">Fin de vie le 3 mars 2020.</span><span class="sxs-lookup"><span data-stu-id="ec881-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="ec881-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ec881-120">.NET Core 2.2</span></span> | <span data-ttu-id="ec881-121">Fin de vie le 23 décembre 2019.</span><span class="sxs-lookup"><span data-stu-id="ec881-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="ec881-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ec881-122">.NET Core 2.1</span></span> | <span data-ttu-id="ec881-123">Fin de vie le 21 août 2021.</span><span class="sxs-lookup"><span data-stu-id="ec881-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="ec881-124">Pour plus d’informations, voir la [politique de soutien .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="ec881-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="ec881-125">macOS appHost et notarisation</span><span class="sxs-lookup"><span data-stu-id="ec881-125">macOS appHost and notarization</span></span>

<span data-ttu-id="ec881-126">*macOS seulement*</span><span class="sxs-lookup"><span data-stu-id="ec881-126">*macOS only*</span></span>

<span data-ttu-id="ec881-127">En commençant par le .NET Core SDK 3.1 notarié pour macOS, le paramètre appHost est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec881-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="ec881-128">Pour plus d’informations, voir [macOS Catalina Notarization et l’impact sur les téléchargements et les projets .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="ec881-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="ec881-129">Lorsque le paramètre appHost est activé, .NET Core génère un Mach-O natif exécutable lorsque vous construisez ou publiez.</span><span class="sxs-lookup"><span data-stu-id="ec881-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="ec881-130">Votre application s’exécute dans le cadre de l’appHost lorsqu’elle est exécutée à partir du code source avec la `dotnet run` commande, ou en commençant le Mach-O exécutable directement.</span><span class="sxs-lookup"><span data-stu-id="ec881-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="ec881-131">Sans l’appHost, la seule façon pour un utilisateur de `dotnet <filename.dll>` démarrer une application dépendante du temps [d’exécution](../deploying/index.md#publish-runtime-dependent) est la commande.</span><span class="sxs-lookup"><span data-stu-id="ec881-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="ec881-132">Un appHost est toujours créé lorsque vous publiez votre application [autonome](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="ec881-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="ec881-133">Vous pouvez configurer l’appHost au niveau du projet, soit `dotnet` basculer `-p:UseAppHost` l’appHost pour une commande spécifique avec le paramètre :</span><span class="sxs-lookup"><span data-stu-id="ec881-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="ec881-134">Fichier projet</span><span class="sxs-lookup"><span data-stu-id="ec881-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="ec881-135">Paramètre de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="ec881-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="ec881-136">Pour plus d’informations sur le `UseAppHost` paramètre, voir [propriétés MSBuild pour Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="ec881-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="ec881-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec881-137">Windows Forms</span></span>

<span data-ttu-id="ec881-138">*Windows seulement*</span><span class="sxs-lookup"><span data-stu-id="ec881-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="ec881-139">Il y a des changements de rupture dans les formulaires Windows.</span><span class="sxs-lookup"><span data-stu-id="ec881-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="ec881-140">Les contrôles hérités ont été inclus dans les formulaires Windows qui n’ont pas été disponibles dans la boîte à outils Visual Studio Designer pendant un certain temps.</span><span class="sxs-lookup"><span data-stu-id="ec881-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="ec881-141">Ceux-ci ont été remplacés par de nouveaux contrôles de retour dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ec881-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="ec881-142">Ceux-ci ont été supprimés du bureau SDK pour .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ec881-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="ec881-143">Contrôle supprimé</span><span class="sxs-lookup"><span data-stu-id="ec881-143">Removed control</span></span> | <span data-ttu-id="ec881-144">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="ec881-144">Recommended replacement</span></span> | <span data-ttu-id="ec881-145">API associées supprimées</span><span class="sxs-lookup"><span data-stu-id="ec881-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="ec881-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ec881-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="ec881-147">DataGridCell (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-147">DataGridCell</span></span><br/><span data-ttu-id="ec881-148">DataGridRow (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-148">DataGridRow</span></span><br/><span data-ttu-id="ec881-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="ec881-149">DataGridTableCollection</span></span><br/><span data-ttu-id="ec881-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="ec881-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="ec881-151">Datagridtablestyle</span><span class="sxs-lookup"><span data-stu-id="ec881-151">DataGridTableStyle</span></span><br/><span data-ttu-id="ec881-152">Datagridcolumnstyle</span><span class="sxs-lookup"><span data-stu-id="ec881-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="ec881-153">DataGridLineStyle (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-153">DataGridLineStyle</span></span><br/><span data-ttu-id="ec881-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="ec881-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="ec881-155">DataGridParentsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="ec881-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="ec881-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="ec881-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="ec881-157">DataGridTextBox (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-157">DataGridTextBox</span></span><br/><span data-ttu-id="ec881-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="ec881-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="ec881-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="ec881-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="ec881-160">HitTestType HitTestType HitTestType HitTest</span><span class="sxs-lookup"><span data-stu-id="ec881-160">HitTestType</span></span> |
| <span data-ttu-id="ec881-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="ec881-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="ec881-162">ToolBarAppearance (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="ec881-163">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="ec881-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="ec881-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="ec881-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="ec881-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="ec881-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="ec881-166">ToolBarButtonStyle (en)</span><span class="sxs-lookup"><span data-stu-id="ec881-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="ec881-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="ec881-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="ec881-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="ec881-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="ec881-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="ec881-169">MenuItemCollection</span></span> |
| <span data-ttu-id="ec881-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="ec881-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="ec881-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ec881-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="ec881-172">Nous vous recommandons de mettre à jour vos applications à .NET Core 3.1 et de passer aux contrôles de remplacement.</span><span class="sxs-lookup"><span data-stu-id="ec881-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="ec881-173">Le remplacement des contrôles est un processus simple, essentiellement «trouver et remplacer» sur le type.</span><span class="sxs-lookup"><span data-stu-id="ec881-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="ec881-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="ec881-174">C++/CLI</span></span>

<span data-ttu-id="ec881-175">*Windows seulement*</span><span class="sxs-lookup"><span data-stu-id="ec881-175">*Windows only*</span></span>

<span data-ttu-id="ec881-176">Un soutien a été ajouté pour la création de projets CMD/CLI (également connus sous le nom de « C «géré ».).</span><span class="sxs-lookup"><span data-stu-id="ec881-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="ec881-177">Les binaires produits à partir de ces projets sont compatibles avec .NET Core 3.0 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ec881-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="ec881-178">Pour ajouter de la prise en charge de la version 16.4 de Visual Studio 2019, installez le [développement de bureau avec une charge de travail .](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)</span><span class="sxs-lookup"><span data-stu-id="ec881-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="ec881-179">Cette charge de travail ajoute deux modèles à Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="ec881-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="ec881-180">Bibliothèque de classe CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="ec881-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="ec881-181">Projet vide CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="ec881-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec881-182">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ec881-182">Next steps</span></span>

- [<span data-ttu-id="ec881-183">Passez en revue les changements de rupture entre .NET Core 3.0 et 3.1.</span><span class="sxs-lookup"><span data-stu-id="ec881-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="ec881-184">Passez en revue les changements de rupture dans .NET Core 3.1 pour les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ec881-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
