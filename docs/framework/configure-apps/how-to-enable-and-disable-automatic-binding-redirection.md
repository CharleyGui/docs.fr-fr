---
title: Activer ou désactiver les redirections de liaison générées automatiquement
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: 178d5070dd7018bbc0fce474cdd0b31ba3d17f77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913032"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="e5e54-102">Procédure : Activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="e5e54-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="e5e54-103">Quand vous compilez des applications dans Visual Studio qui ciblent le .NET Framework 4.5.1 et versions ultérieures, les redirections de liaison peuvent être ajoutées automatiquement au fichier de configuration d’application pour remplacer l’unification d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="e5e54-103">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="e5e54-104">Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="e5e54-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="e5e54-105">La fonctionnalité de redirection de liaison automatique affecte les applications de bureau et les applications Web qui ciblent le .NET Framework 4.5.1 ou une version ultérieure, même si le comportement est légèrement différent pour une application Web.</span><span class="sxs-lookup"><span data-stu-id="e5e54-105">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="e5e54-106">Vous pouvez activer la redirection de liaison automatique si vous avez des applications existantes qui ciblent des versions antérieures du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez créer manuellement des redirections de liaison.</span><span class="sxs-lookup"><span data-stu-id="e5e54-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="e5e54-107">Désactiver les redirections de liaison automatiques dans les applications de bureau</span><span class="sxs-lookup"><span data-stu-id="e5e54-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="e5e54-108">Les redirections de liaison automatiques sont activées par défaut pour les applications de bureau Windows qui ciblent le .NET Framework 4.5.1 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e5e54-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="e5e54-109">Les redirections de liaison sont ajoutées au fichier de configuration de sortie (**app. config**) lorsque l’application est compilée et remplacent l’unification d’assemblys qui pourrait autrement se produire.</span><span class="sxs-lookup"><span data-stu-id="e5e54-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="e5e54-110">Le fichier **app. config** source n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="e5e54-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="e5e54-111">Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet de l’application ou en désélectionnant une case à cocher dans les propriétés du projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5e54-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="e5e54-112">Désactiver via les propriétés du projet</span><span class="sxs-lookup"><span data-stu-id="e5e54-112">Disable through project properties</span></span>

<span data-ttu-id="e5e54-113">Si vous disposez de Visual Studio 2017 version 15,7 ou ultérieure, vous pouvez facilement désactiver les redirections de liaison générées automatiquement dans les pages de propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="e5e54-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="e5e54-114">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="e5e54-115">Sur la page **application** , décochez l’option **générer automatiquement les redirections de liaison** .</span><span class="sxs-lookup"><span data-stu-id="e5e54-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="e5e54-116">Appuyez sur **CTRL** + **S** pour enregistrer la modification.</span><span class="sxs-lookup"><span data-stu-id="e5e54-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="e5e54-117">Désactiver manuellement dans le fichier projet</span><span class="sxs-lookup"><span data-stu-id="e5e54-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="e5e54-118">Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5e54-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="e5e54-119">Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="e5e54-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="e5e54-120">Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="e5e54-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="e5e54-121">Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="e5e54-122">Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="e5e54-123">Dans le fichier projet, recherchez l'entrée de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="e5e54-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="e5e54-124">Remplacez `true` par `false` :</span><span class="sxs-lookup"><span data-stu-id="e5e54-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="e5e54-125">Activer les redirections de liaison automatiques manuellement</span><span class="sxs-lookup"><span data-stu-id="e5e54-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="e5e54-126">Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions antérieures du .NET Framework ou dans les cas où vous n’êtes pas automatiquement invité à ajouter une redirection.</span><span class="sxs-lookup"><span data-stu-id="e5e54-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="e5e54-127">Si vous ciblez une version plus récente du Framework, mais que vous n’êtes pas invité automatiquement à ajouter une redirection, vous obtiendrez probablement une sortie de génération qui vous suggère de remapper les assemblys.</span><span class="sxs-lookup"><span data-stu-id="e5e54-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="e5e54-128">Ouvrez le fichier projet pour le modifier à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5e54-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="e5e54-129">Dans Visual Studio, sélectionnez le projet dans **Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="e5e54-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="e5e54-130">Dans l’Explorateur de fichiers, recherchez le fichier projet (. csproj ou. vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="e5e54-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="e5e54-131">Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="e5e54-132">Cliquez à nouveau avec le bouton droit sur le projet déchargé, puis choisissez **modifier [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="e5e54-133">Ajoutez l’élément suivant au premier groupe de propriétés de configuration (sous la \<PropertyGroup> balise) :</span><span class="sxs-lookup"><span data-stu-id="e5e54-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="e5e54-134">L’exemple suivant montre un exemple de fichier projet avec l’élément inséré :</span><span class="sxs-lookup"><span data-stu-id="e5e54-134">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="e5e54-135">Compilez votre application.</span><span class="sxs-lookup"><span data-stu-id="e5e54-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="e5e54-136">Activer les redirections de liaison automatiques dans les applications Web</span><span class="sxs-lookup"><span data-stu-id="e5e54-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="e5e54-137">Les redirections de liaison automatiques sont implémentées différemment pour les applications web.</span><span class="sxs-lookup"><span data-stu-id="e5e54-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="e5e54-138">Étant donné que le fichier de configuration source (**Web. config**) doit être modifié pour les applications Web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e5e54-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="e5e54-139">Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits.</span><span class="sxs-lookup"><span data-stu-id="e5e54-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="e5e54-140">Étant donné que vous êtes toujours invité à ajouter des redirections de liaison, vous n’avez pas besoin de désactiver explicitement cette fonctionnalité pour une application Web.</span><span class="sxs-lookup"><span data-stu-id="e5e54-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="e5e54-141">Pour ajouter des redirections de liaison à un fichier **Web. config** :</span><span class="sxs-lookup"><span data-stu-id="e5e54-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="e5e54-142">Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.</span><span class="sxs-lookup"><span data-stu-id="e5e54-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="e5e54-143">![Avertissement sur la génération des conflits de la référence d'assembly](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="e5e54-143">![Build warning for assembly reference conflicts](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="e5e54-144">En cas de conflit de liaison d’assembly, un avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e5e54-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="e5e54-145">Double-cliquez sur l’avertissement ou sélectionnez l’avertissement et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e5e54-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="e5e54-146">Une boîte de dialogue qui vous permet d’ajouter automatiquement les redirections de liaison nécessaires vers le fichier **Web. config** source s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e5e54-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="e5e54-147">![Boîte de dialogue des autorisations de redirection de liaison](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="e5e54-147">![Binding redirect permission dialog](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e54-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5e54-148">See also</span></span>

- [<span data-ttu-id="e5e54-149">\<bindingRedirect>Appartient</span><span class="sxs-lookup"><span data-stu-id="e5e54-149">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="e5e54-150">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="e5e54-150">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
