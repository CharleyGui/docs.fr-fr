---
title: Activer ou désactiver les redirections de liaison générées automatiquement
description: Lisez comment activer ou désactiver la redirection de liaison automatique. Cette fonctionnalité affecte les applications de bureau et les applications Web ciblant .NET Framework 4.5.1 ou version ultérieure.
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b099ab4958b1cf41b76884243e252e19a7a951b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698830"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="597ca-104">Procédure : Activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="597ca-104">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="597ca-105">Quand vous compilez des applications dans Visual Studio qui ciblent le .NET Framework 4.5.1 et versions ultérieures, les redirections de liaison peuvent être ajoutées automatiquement au fichier de configuration d’application pour remplacer l’unification d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="597ca-105">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="597ca-106">Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="597ca-106">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="597ca-107">La fonctionnalité de redirection de liaison automatique affecte les applications de bureau et les applications Web qui ciblent le .NET Framework 4.5.1 ou une version ultérieure, même si le comportement est légèrement différent pour une application Web.</span><span class="sxs-lookup"><span data-stu-id="597ca-107">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="597ca-108">Vous pouvez activer la redirection de liaison automatique si vous avez des applications existantes qui ciblent des versions antérieures du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez créer manuellement des redirections de liaison.</span><span class="sxs-lookup"><span data-stu-id="597ca-108">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="597ca-109">Désactiver les redirections de liaison automatiques dans les applications de bureau</span><span class="sxs-lookup"><span data-stu-id="597ca-109">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="597ca-110">Les redirections de liaison automatiques sont activées par défaut pour les applications de bureau Windows qui ciblent le .NET Framework 4.5.1 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="597ca-110">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="597ca-111">Les redirections de liaison sont ajoutées au fichier de configuration de sortie (**app.config**) lorsque l’application est compilée et remplacent l’unification de l’assembly qui, sinon, peut avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="597ca-111">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="597ca-112">Le fichier **app.config** source n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="597ca-112">The source **app.config** file is not modified.</span></span> <span data-ttu-id="597ca-113">Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet de l’application ou en désélectionnant une case à cocher dans les propriétés du projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="597ca-113">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="597ca-114">Désactiver via les propriétés du projet</span><span class="sxs-lookup"><span data-stu-id="597ca-114">Disable through project properties</span></span>

<span data-ttu-id="597ca-115">Si vous disposez de Visual Studio 2017 version 15,7 ou ultérieure, vous pouvez facilement désactiver les redirections de liaison générées automatiquement dans les pages de propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="597ca-115">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="597ca-116">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="597ca-116">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="597ca-117">Sur la page **application** , décochez l’option **générer automatiquement les redirections de liaison** .</span><span class="sxs-lookup"><span data-stu-id="597ca-117">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="597ca-118">Appuyez sur **CTRL** + **S** pour enregistrer la modification.</span><span class="sxs-lookup"><span data-stu-id="597ca-118">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="597ca-119">Désactiver manuellement dans le fichier projet</span><span class="sxs-lookup"><span data-stu-id="597ca-119">Disable manually in the project file</span></span>

1. <span data-ttu-id="597ca-120">Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="597ca-120">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="597ca-121">Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="597ca-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="597ca-122">Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="597ca-122">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="597ca-123">Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="597ca-123">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="597ca-124">Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="597ca-124">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="597ca-125">Dans le fichier projet, recherchez l'entrée de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="597ca-125">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="597ca-126">Remplacez `true` par `false` :</span><span class="sxs-lookup"><span data-stu-id="597ca-126">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="597ca-127">Activer les redirections de liaison automatiques manuellement</span><span class="sxs-lookup"><span data-stu-id="597ca-127">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="597ca-128">Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions antérieures du .NET Framework ou dans les cas où vous n’êtes pas automatiquement invité à ajouter une redirection.</span><span class="sxs-lookup"><span data-stu-id="597ca-128">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="597ca-129">Si vous ciblez une version plus récente du Framework, mais que vous n’êtes pas invité automatiquement à ajouter une redirection, vous obtiendrez probablement une sortie de génération qui vous suggère de remapper les assemblys.</span><span class="sxs-lookup"><span data-stu-id="597ca-129">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="597ca-130">Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="597ca-130">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="597ca-131">Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="597ca-131">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="597ca-132">Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="597ca-132">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="597ca-133">Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="597ca-133">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="597ca-134">Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="597ca-134">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="597ca-135">Ajoutez l’élément suivant au premier groupe de propriétés de configuration (sous la \<PropertyGroup> balise) :</span><span class="sxs-lookup"><span data-stu-id="597ca-135">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="597ca-136">L’exemple suivant montre un exemple de fichier projet avec l’élément inséré :</span><span class="sxs-lookup"><span data-stu-id="597ca-136">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="597ca-137">Compilez votre application.</span><span class="sxs-lookup"><span data-stu-id="597ca-137">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="597ca-138">Activer les redirections de liaison automatiques dans les applications Web</span><span class="sxs-lookup"><span data-stu-id="597ca-138">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="597ca-139">Les redirections de liaison automatiques sont implémentées différemment pour les applications web.</span><span class="sxs-lookup"><span data-stu-id="597ca-139">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="597ca-140">Étant donné que le fichier de configuration source (**web.config**) doit être modifié pour les applications Web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="597ca-140">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="597ca-141">Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits.</span><span class="sxs-lookup"><span data-stu-id="597ca-141">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="597ca-142">Étant donné que vous êtes toujours invité à ajouter des redirections de liaison, vous n’avez pas besoin de désactiver explicitement cette fonctionnalité pour une application Web.</span><span class="sxs-lookup"><span data-stu-id="597ca-142">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="597ca-143">Pour ajouter des redirections de liaison à un fichier de **web.config** :</span><span class="sxs-lookup"><span data-stu-id="597ca-143">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="597ca-144">Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.</span><span class="sxs-lookup"><span data-stu-id="597ca-144">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="597ca-145">![Avertissement sur la génération des conflits de la référence d'assembly](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="597ca-145">![Build warning for assembly reference conflicts](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="597ca-146">En cas de conflit de liaison d’assembly, un avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="597ca-146">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="597ca-147">Double-cliquez sur l’avertissement ou sélectionnez l’avertissement et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="597ca-147">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="597ca-148">Une boîte de dialogue qui vous permet d’ajouter automatiquement les redirections de liaison nécessaires vers le fichier **web.config** source s’affiche.</span><span class="sxs-lookup"><span data-stu-id="597ca-148">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="597ca-149">![Boîte de dialogue des autorisations de redirection de liaison](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="597ca-149">![Binding redirect permission dialog](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="597ca-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="597ca-150">See also</span></span>

- [<span data-ttu-id="597ca-151">\<bindingRedirect> Appartient</span><span class="sxs-lookup"><span data-stu-id="597ca-151">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="597ca-152">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="597ca-152">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
