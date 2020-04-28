---
title: Installer et gérer des modèles de kit de développement logiciel (SDK) .NET Core
description: Découvrez comment installer des modèles .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 0a3c8655d55bf63de1e91337ce3a2ac399b07d0f
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200614"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="ccdfe-103">Gérer les modèles de projet et d’élément .NET</span><span class="sxs-lookup"><span data-stu-id="ccdfe-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="ccdfe-104">.NET Core fournit un système de modèles qui permet aux utilisateurs d’installer ou de désinstaller des modèles à partir de NuGet, d’un fichier de package NuGet ou d’un répertoire de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="ccdfe-105">Cet article explique comment gérer les modèles .NET Core par le biais de l’interface de commande kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="ccdfe-106">Pour plus d’informations sur la création de modèles, consultez [Didacticiel : créer des modèles](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="ccdfe-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="ccdfe-107">Installer le modèle</span><span class="sxs-lookup"><span data-stu-id="ccdfe-107">Install template</span></span>

<span data-ttu-id="ccdfe-108">Les modèles sont installés à l’aide de la commande [dotnet New](../tools/dotnet-new.md) SDK avec le `-i` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="ccdfe-109">Vous pouvez soit fournir l’identificateur de package NuGet d’un modèle, soit un dossier qui contient les fichiers modèles.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="ccdfe-110">Package hébergé par NuGet</span><span class="sxs-lookup"><span data-stu-id="ccdfe-110">NuGet hosted package</span></span>

<span data-ttu-id="ccdfe-111">Les modèles CLI .NET sont téléchargés vers [NuGet](https://www.nuget.org/) pour une distribution étendue.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="ccdfe-112">Les modèles peuvent également être installés à partir d’un flux privé.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="ccdfe-113">Au lieu de télécharger un modèle dans un flux NuGet, les fichiers de modèle *nupkg* peuvent être distribués et installés manuellement, comme décrit dans la section [package NuGet local](#local-nuget-package) .</span><span class="sxs-lookup"><span data-stu-id="ccdfe-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="ccdfe-114">Pour plus d’informations sur la configuration des flux NuGet, consultez [dotnet NuGet Add source](../tools/dotnet-nuget-add-source.md).</span><span class="sxs-lookup"><span data-stu-id="ccdfe-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="ccdfe-115">Pour installer un package de modèles à partir du flux NuGet par défaut `dotnet new -i {package-id}` , utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="ccdfe-116">Pour installer un package de modèles à partir du flux NuGet par défaut avec une version spécifique `dotnet new -i {package-id}::{version}` , utilisez la commande :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="ccdfe-117">Package NuGet local</span><span class="sxs-lookup"><span data-stu-id="ccdfe-117">Local NuGet package</span></span>

<span data-ttu-id="ccdfe-118">Quand un pack de modèles est créé, un fichier *nupkg* est généré.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="ccdfe-119">Si vous avez un fichier *nupkg* contenant des modèles, vous pouvez l’installer à `dotnet new -i {path-to-package}` l’aide de la commande :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="ccdfe-120">Dossier</span><span class="sxs-lookup"><span data-stu-id="ccdfe-120">Folder</span></span>

<span data-ttu-id="ccdfe-121">Au lieu d’installer le modèle à partir d’un fichier *nupkg* , vous pouvez également installer des modèles à partir d' `dotnet new -i {folder-path}` un dossier directement avec la commande.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="ccdfe-122">Le dossier spécifié est considéré comme l’identificateur de package de modèle pour tout modèle trouvé.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="ccdfe-123">Tout modèle trouvé dans la hiérarchie du dossier spécifié est installé.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="ccdfe-124">Le `{folder-path}` spécifié sur la commande devient l’identificateur de modèle de package pour tous les modèles trouvés.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="ccdfe-125">Comme indiqué dans la section [modèles de liste](#list-templates) , vous pouvez obtenir la liste des modèles installés à `dotnet new -u` l’aide de la commande.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="ccdfe-126">Dans cet exemple, l’identificateur template Pack est indiqué comme dossier utilisé pour l’installation :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="ccdfe-127">Désinstaller le modèle</span><span class="sxs-lookup"><span data-stu-id="ccdfe-127">Uninstall template</span></span>

<span data-ttu-id="ccdfe-128">Les modèles sont désinstallés via la commande [dotnet New](../tools/dotnet-new.md) SDK avec `-u` le paramètre.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="ccdfe-129">Vous pouvez soit fournir l’identificateur de package NuGet d’un modèle, soit un dossier qui contient les fichiers modèles.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="ccdfe-130">Package NuGet</span><span class="sxs-lookup"><span data-stu-id="ccdfe-130">NuGet package</span></span>

<span data-ttu-id="ccdfe-131">Après l’installation d’un pack de modèles NuGet à partir d’un flux NuGet ou d’un fichier *nupkg* , vous pouvez le désinstaller en référençant l’identificateur de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="ccdfe-132">Pour désinstaller un pack de modèles, `dotnet new -u {package-id}` utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="ccdfe-133">Dossier</span><span class="sxs-lookup"><span data-stu-id="ccdfe-133">Folder</span></span>

<span data-ttu-id="ccdfe-134">Lorsque des modèles sont installés par le biais [d’un chemin d’accès au dossier](#folder), le chemin d’accès au dossier devient l’identificateur du Pack de modèles.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="ccdfe-135">Pour désinstaller un pack de modèles, `dotnet new -u {package-folder-path}` utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ccdfe-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="ccdfe-136">Liste des modèles</span><span class="sxs-lookup"><span data-stu-id="ccdfe-136">List templates</span></span>

<span data-ttu-id="ccdfe-137">En utilisant la commande de désinstallation standard sans identificateur de package, vous pouvez voir la liste des modèles installés avec la commande qui désinstalle chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="ccdfe-138">Installer des modèles à partir d’autres SDK</span><span class="sxs-lookup"><span data-stu-id="ccdfe-138">Install templates from other SDKs</span></span>

<span data-ttu-id="ccdfe-139">Si vous avez installé chaque version du kit de développement logiciel (SDK) de manière séquentielle, par exemple si vous avez installé le kit de développement logiciel 2,0, le kit de développement logiciel (SDK) 2,1, etc., tous les modèles du SDK sont installés.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="ccdfe-140">Toutefois, si vous démarrez avec une version ultérieure du kit de développement logiciel (SDK), comme 3,1, seuls les modèles pour [LTS (support à long terme)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sont inclus, qui au moment de la publication du kit de développement logiciel (sdk) 3,1 est SDK 2,1 et SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="ccdfe-141">Les modèles pour toute autre version ne sont pas inclus.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="ccdfe-142">Les modèles .NET Core sont disponibles sur NuGet et vous pouvez les installer comme n’importe quel autre modèle.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="ccdfe-143">Pour plus d’informations, consultez [install NuGet Hosted package](#nuget-hosted-package).</span><span class="sxs-lookup"><span data-stu-id="ccdfe-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="ccdfe-144">Kit SDK</span><span class="sxs-lookup"><span data-stu-id="ccdfe-144">SDK</span></span>              | <span data-ttu-id="ccdfe-145">Identificateur du package NuGet</span><span class="sxs-lookup"><span data-stu-id="ccdfe-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ccdfe-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ccdfe-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="ccdfe-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ccdfe-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="ccdfe-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ccdfe-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="ccdfe-149">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ccdfe-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="ccdfe-150">ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ccdfe-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="ccdfe-151">ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ccdfe-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="ccdfe-152">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="ccdfe-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="ccdfe-153">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ccdfe-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="ccdfe-154">Par exemple, le kit SDK .NET Core contient des modèles pour une application console ciblant .NET Core 2,1 et .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="ccdfe-155">Si vous souhaitez cibler .NET Core 3,0, vous devez installer les modèles 3,0.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="ccdfe-156">Essayez de créer une application qui cible .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="ccdfe-157">Si un message d’erreur s’affiche, vous devez installer les modèles.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="ccdfe-158">Impossible de trouver un modèle installé qui correspond à l’entrée, recherche en ligne d’un modèle qui fait...</span><span class="sxs-lookup"><span data-stu-id="ccdfe-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="ccdfe-159">Installez les modèles de projet .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="ccdfe-160">Essayez de créer l’application une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="ccdfe-161">Et un message indiquant que le projet a été créé doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="ccdfe-162">Le modèle « application console » a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="ccdfe-163">Traitement des actions après création... Exécution de « dotnet restore » sur Path-to-Project-file. csproj... Détermination des projets à restaurer... Restauration terminée dans 1,05 s pour Path-to-Project-file. csproj.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="ccdfe-164">Restauration réussie.</span><span class="sxs-lookup"><span data-stu-id="ccdfe-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccdfe-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccdfe-165">See also</span></span>

- [<span data-ttu-id="ccdfe-166">Didacticiel : créer un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="ccdfe-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
