---
title: Activer ou désactiver les redirections de liaison généré automatiquement
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380100"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="f1e70-102">Procédure : Activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="f1e70-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="f1e70-103">Lorsque vous compilez des applications dans Visual Studio qui ciblent le .NET Framework 4.5.1 et versions ultérieures, les redirections de liaison peuvent être automatiquement ajoutées au fichier de configuration d’application pour remplacer l’unification d’assembly.</span><span class="sxs-lookup"><span data-stu-id="f1e70-103">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="f1e70-104">Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="f1e70-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="f1e70-105">La fonctionnalité de redirection de liaison automatique affecte les applications web et les applications de bureau qui ciblent le .NET Framework 4.5.1 ou version ultérieure, bien que le comportement est légèrement différent pour une application web.</span><span class="sxs-lookup"><span data-stu-id="f1e70-105">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="f1e70-106">Vous pouvez activer la redirection de liaison automatique si vous avez des applications existantes qui ciblent des versions précédentes du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez créer manuellement des redirections de liaison.</span><span class="sxs-lookup"><span data-stu-id="f1e70-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="f1e70-107">Désactiver les redirections de liaison automatiques dans les applications de bureau</span><span class="sxs-lookup"><span data-stu-id="f1e70-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="f1e70-108">Redirections de liaison automatiques sont activées par défaut pour les applications de bureau Windows qui ciblent le .NET Framework 4.5.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f1e70-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="f1e70-109">Les redirections de liaison sont ajoutées à la configuration de sortie (**app.config**) du fichier lorsque l’application est compilée et remplacer l’unification d’assembly qui peut avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="f1e70-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="f1e70-110">La source de **app.config** fichier n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="f1e70-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="f1e70-111">Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet pour l’application ou en désactivant une case à cocher dans les propriétés du projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1e70-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="f1e70-112">Désactivation de via les propriétés du projet</span><span class="sxs-lookup"><span data-stu-id="f1e70-112">Disable through project properties</span></span>

<span data-ttu-id="f1e70-113">Si vous avez Visual Studio 2017 version 15.7 ou version ultérieure, vous pouvez facilement désactiver les redirections de liaison généré automatiquement dans les pages de propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="f1e70-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="f1e70-114">Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1e70-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="f1e70-115">Sur le **Application** page, désactivez le **générer automatiquement des redirections de liaison** option.</span><span class="sxs-lookup"><span data-stu-id="f1e70-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="f1e70-116">Appuyez sur **Ctrl**+**S** pour enregistrer la modification.</span><span class="sxs-lookup"><span data-stu-id="f1e70-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="f1e70-117">Désactiver manuellement dans le fichier projet</span><span class="sxs-lookup"><span data-stu-id="f1e70-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="f1e70-118">Ouvrez le fichier de projet pour la modification à l’aide d’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1e70-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="f1e70-119">Dans Visual Studio, sélectionnez le projet dans **l’Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f1e70-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="f1e70-120">Dans l’Explorateur de fichiers, recherchez le fichier de projet (.csproj ou .vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="f1e70-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="f1e70-121">Dans Visual Studio, dans **l’Explorateur de solutions**, cliquez sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="f1e70-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="f1e70-122">Cliquez de nouveau sur le projet déchargé, puis choisissez **modifier [NomProjet.csproj]** .</span><span class="sxs-lookup"><span data-stu-id="f1e70-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="f1e70-123">Dans le fichier projet, recherchez l'entrée de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="f1e70-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="f1e70-124">Remplacez `true` par `false` :</span><span class="sxs-lookup"><span data-stu-id="f1e70-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="f1e70-125">Activer manuellement des redirections de liaison automatiques</span><span class="sxs-lookup"><span data-stu-id="f1e70-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="f1e70-126">Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions antérieures du .NET Framework, ou dans les cas où vous n’êtes pas automatiquement invité à ajouter une redirection.</span><span class="sxs-lookup"><span data-stu-id="f1e70-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="f1e70-127">Si vous ciblez une version plus récente du framework mais ne pas automatiquement invité à ajouter une redirection, vous obtiendrez probablement un résultat de build qui suggère de que remapper les assemblys.</span><span class="sxs-lookup"><span data-stu-id="f1e70-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="f1e70-128">Ouvrez le fichier de projet pour la modification à l’aide d’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1e70-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="f1e70-129">Dans Visual Studio, sélectionnez le projet dans **l’Explorateur de solutions**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f1e70-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="f1e70-130">Dans l’Explorateur de fichiers, recherchez le fichier de projet (.csproj ou .vbproj) et ouvrez-le dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="f1e70-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="f1e70-131">Dans Visual Studio, dans **l’Explorateur de solutions**, cliquez sur le projet et choisissez **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="f1e70-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="f1e70-132">Cliquez de nouveau sur le projet déchargé, puis choisissez **modifier [NomProjet.csproj]** .</span><span class="sxs-lookup"><span data-stu-id="f1e70-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="f1e70-133">Ajoutez l’élément suivant pour le premier groupe de propriétés de configuration (sous le \<PropertyGroup > balise) :</span><span class="sxs-lookup"><span data-stu-id="f1e70-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="f1e70-134">Voici un exemple de fichier de projet avec l’élément inséré :</span><span class="sxs-lookup"><span data-stu-id="f1e70-134">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="f1e70-135">Compilez votre application.</span><span class="sxs-lookup"><span data-stu-id="f1e70-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="f1e70-136">Activer les redirections de liaison automatiques dans les applications web</span><span class="sxs-lookup"><span data-stu-id="f1e70-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="f1e70-137">Les redirections de liaison automatiques sont implémentées différemment pour les applications web.</span><span class="sxs-lookup"><span data-stu-id="f1e70-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="f1e70-138">Étant donné que la configuration de la source (**web.config**) fichier doit être modifié pour les applications web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f1e70-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="f1e70-139">Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits.</span><span class="sxs-lookup"><span data-stu-id="f1e70-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="f1e70-140">Étant donné que vous êtes toujours invité à ajouter des redirections de liaison, vous n’avez pas besoin de désactiver explicitement cette fonctionnalité pour une application web.</span><span class="sxs-lookup"><span data-stu-id="f1e70-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="f1e70-141">Pour ajouter des redirections de liaison à un **web.config** fichier :</span><span class="sxs-lookup"><span data-stu-id="f1e70-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="f1e70-142">Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.</span><span class="sxs-lookup"><span data-stu-id="f1e70-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="f1e70-143">![Générer l’avertissement pour les conflits de référence d’assembly](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="f1e70-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="f1e70-144">En cas de conflit de liaison d’assembly, un avertissement s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f1e70-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="f1e70-145">Double-cliquez sur l’avertissement, ou sélectionnez l’avertissement et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="f1e70-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="f1e70-146">Une boîte de dialogue qui vous permet d’ajouter automatiquement la liaison nécessaires redirige vers la source **web.config** fichier s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f1e70-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="f1e70-147">![Boîte de dialogue liaison de redirection autorisation](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="f1e70-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="f1e70-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1e70-148">See also</span></span>

- [<span data-ttu-id="f1e70-149">\<bindingRedirect > élément</span><span class="sxs-lookup"><span data-stu-id="f1e70-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="f1e70-150">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="f1e70-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
