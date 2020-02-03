---
title: URI à en-tête pack
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 0fec72bdedbcc2c84d8bc65e72391366e42d82be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739157"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="37d31-102">URI à en-tête pack dans WPF</span><span class="sxs-lookup"><span data-stu-id="37d31-102">Pack URIs in WPF</span></span>

<span data-ttu-id="37d31-103">Dans Windows Presentation Foundation (WPF), les URI (Uniform Resource Identifiers) sont utilisés pour identifier et charger les fichiers de plusieurs façons, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-103">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="37d31-104">Spécification de l' [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à afficher lorsqu’une application démarre pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="37d31-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="37d31-105">En chargeant des images</span><span class="sxs-lookup"><span data-stu-id="37d31-105">Loading images.</span></span>

- <span data-ttu-id="37d31-106">En naviguant vers des pages</span><span class="sxs-lookup"><span data-stu-id="37d31-106">Navigating to pages.</span></span>

- <span data-ttu-id="37d31-107">En chargeant des fichiers de données non exécutables</span><span class="sxs-lookup"><span data-stu-id="37d31-107">Loading non-executable data files.</span></span>

<span data-ttu-id="37d31-108">En outre, les URI peuvent être utilisés pour identifier et charger des fichiers à partir de différents emplacements, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-108">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="37d31-109">L’assembly actuel</span><span class="sxs-lookup"><span data-stu-id="37d31-109">The current assembly.</span></span>

- <span data-ttu-id="37d31-110">Un assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-110">A referenced assembly.</span></span>

- <span data-ttu-id="37d31-111">Un emplacement relatif à un assembly</span><span class="sxs-lookup"><span data-stu-id="37d31-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="37d31-112">Le site d’origine de l’application</span><span class="sxs-lookup"><span data-stu-id="37d31-112">The application's site of origin.</span></span>

<span data-ttu-id="37d31-113">Pour fournir un mécanisme cohérent pour identifier et charger ces types de fichiers à partir de ces emplacements, WPF tire parti de l’extensibilité du schéma d’URI à en- *tête pack*.</span><span class="sxs-lookup"><span data-stu-id="37d31-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, WPF leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="37d31-114">Cette rubrique fournit une vue d’ensemble du schéma, explique comment construire des URI à en-tête pack pour divers scénarios, traite des URI absolus et relatifs et la résolution d’URI, avant d’illustrer l’utilisation des URI à en-tête pack à partir du balisage et du code.</span><span class="sxs-lookup"><span data-stu-id="37d31-114">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="37d31-115">Schéma URI à en-tête pack</span><span class="sxs-lookup"><span data-stu-id="37d31-115">The Pack URI Scheme</span></span>

<span data-ttu-id="37d31-116">Le schéma d’URI à en-tête pack est utilisé par la spécification [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC), qui décrit un modèle d’organisation et d’identification du contenu.</span><span class="sxs-lookup"><span data-stu-id="37d31-116">The pack URI scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="37d31-117">Les éléments clés de ce modèle sont des packages et des parties, où un *package* est un conteneur logique pour une ou plusieurs *parties*logiques.</span><span class="sxs-lookup"><span data-stu-id="37d31-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="37d31-118">La figure suivante illustre ce concept.</span><span class="sxs-lookup"><span data-stu-id="37d31-118">The following figure illustrates this concept.</span></span>

![Diagramme Package et pièces](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="37d31-120">Pour identifier les parties, la spécification OPC tire parti de l’extensibilité de la norme RFC 2396 (Uniform Resource Identifiers (URI) : syntaxe générique) pour définir le modèle d’URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="37d31-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="37d31-121">Le schéma spécifié par un URI est défini par son préfixe ; http, FTP et file sont des exemples connus.</span><span class="sxs-lookup"><span data-stu-id="37d31-121">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="37d31-122">Le modèle d’URI à en-tête pack utilise « Pack » comme modèle et contient deux composants : autorité et chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="37d31-122">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="37d31-123">Voici le format d’un URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="37d31-123">The following is the format for a pack URI.</span></span>

<span data-ttu-id="37d31-124">*chemin d’accès*/de l'*autorité* Pack://</span><span class="sxs-lookup"><span data-stu-id="37d31-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="37d31-125">L' *autorité* spécifie le type de package qui contient un composant, tandis que le *chemin d’accès* spécifie l’emplacement d’une partie au sein d’un package.</span><span class="sxs-lookup"><span data-stu-id="37d31-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="37d31-126">Ce concept est illustré par le figure suivante :</span><span class="sxs-lookup"><span data-stu-id="37d31-126">This concept is illustrated by the following figure:</span></span>

![Relation entre package, autorité et chemin d'accès](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="37d31-128">Les packages et les parties s’apparentent à des applications et des fichiers, où une application (package) peut inclure un ou plusieurs fichiers (parties), notamment :</span><span class="sxs-lookup"><span data-stu-id="37d31-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="37d31-129">Des fichiers de ressources compilés dans l’assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="37d31-130">Des fichiers de ressources compilés dans un assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="37d31-131">Des fichiers de ressources compilés dans un assembly de référence</span><span class="sxs-lookup"><span data-stu-id="37d31-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="37d31-132">Des fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-132">Content files.</span></span>

- <span data-ttu-id="37d31-133">Des fichiers de site d’origine</span><span class="sxs-lookup"><span data-stu-id="37d31-133">Site of origin files.</span></span>

<span data-ttu-id="37d31-134">Pour accéder à ces types de fichiers, WPF prend en charge deux autorités : application:///et siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-134">To access these types of files, WPF supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="37d31-135">L’autorité application:/// identifie les fichiers de données d’application qui sont connus au moment de la compilation, notamment les fichiers de ressources et de contenu.</span><span class="sxs-lookup"><span data-stu-id="37d31-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="37d31-136">L’autorité siteoforigin:/// identifie les fichiers de site d’origine.</span><span class="sxs-lookup"><span data-stu-id="37d31-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="37d31-137">La portée de chaque autorité est indiquée dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="37d31-137">The scope of each authority is shown in the following figure.</span></span>

![Diagramme URI à en-tête pack](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="37d31-139">Le composant d’autorité d’un URI à en-tête pack est un URI incorporé qui pointe vers un package et doit être conforme à la norme RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="37d31-139">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="37d31-140">De plus, le caractère « / » doit être remplacé par le caractère « , » et les caractères réservés tels que « % » et « ? » doivent être échappés.</span><span class="sxs-lookup"><span data-stu-id="37d31-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="37d31-141">Pour plus d’informations, consultez l’OPC.</span><span class="sxs-lookup"><span data-stu-id="37d31-141">See the OPC for details.</span></span>

<span data-ttu-id="37d31-142">Les sections suivantes expliquent comment construire des URI à en-tête pack à l’aide de ces deux autorités conjointement avec les chemins d’accès appropriés pour identifier les fichiers de ressources, de contenu et de site d’origine.</span><span class="sxs-lookup"><span data-stu-id="37d31-142">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="37d31-143">URI à en-tête pack de fichier de ressources</span><span class="sxs-lookup"><span data-stu-id="37d31-143">Resource File Pack URIs</span></span>

<span data-ttu-id="37d31-144">Les fichiers de ressources sont configurés en tant qu’éléments `Resource` MSBuild et sont compilés dans des assemblys.</span><span class="sxs-lookup"><span data-stu-id="37d31-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="37d31-145">WPF prend en charge la construction d’URI à en-tête pack qui peuvent être utilisés pour identifier des fichiers de ressources qui sont compilés dans l’assembly local ou compilés dans un assembly qui est référencé à partir de l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="37d31-146">Fichier de ressources d’assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-146">Local Assembly Resource File</span></span>

<span data-ttu-id="37d31-147">L’URI à en-tête pack pour un fichier de ressources compilé dans l’assembly local utilise l’autorité et le chemin d’accès suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-147">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="37d31-148">**Autorité** : application:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="37d31-149">**Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="37d31-150">L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve à la racine du dossier du projet de l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-150">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="37d31-151">L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous-dossier du dossier du projet de l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="37d31-152">Fichier de ressources d’assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="37d31-153">L’URI à en-tête pack pour un fichier de ressources compilé dans un assembly référencé utilise l’autorité et le chemin d’accès suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-153">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="37d31-154">**Autorité** : application:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="37d31-155">**Chemin** : nom d’un fichier de ressources compilé dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="37d31-156">Le chemin doit respecter le format suivant :</span><span class="sxs-lookup"><span data-stu-id="37d31-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="37d31-157">*NomCourtAssembly*{ *; Version*] { *; PublicKey*]; composant/*chemin d’accès*</span><span class="sxs-lookup"><span data-stu-id="37d31-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="37d31-158">**NomCourtAssembly** : nom court de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="37d31-159">**;Version** [facultatif] : version de l’assembly référencé qui contient le fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="37d31-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="37d31-160">Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.</span><span class="sxs-lookup"><span data-stu-id="37d31-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="37d31-161">**;CléPublique** [facultatif] : clé publique utilisée pour signer l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="37d31-162">Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.</span><span class="sxs-lookup"><span data-stu-id="37d31-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="37d31-163">**;component** : indique que l’assembly désigné est référencé à partir de l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="37d31-164">**/Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="37d31-165">L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve à la racine du dossier du projet de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-165">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="37d31-166">L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous-dossier du dossier du projet de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="37d31-167">L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans le dossier racine d’un dossier de projet d’assembly spécifique à la version référencé.</span><span class="sxs-lookup"><span data-stu-id="37d31-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="37d31-168">Notez que la syntaxe d’URI à en-tête pack pour les fichiers de ressources d’assembly référencés peut être utilisée uniquement avec l’autorité application:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-168">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="37d31-169">Par exemple, le code suivant n’est pas pris en charge dans WPF.</span><span class="sxs-lookup"><span data-stu-id="37d31-169">For example, the following is not supported in WPF.</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="37d31-170">URI à en-tête pack de fichier de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-170">Content File Pack URIs</span></span>

<span data-ttu-id="37d31-171">L’URI à en-tête pack pour un fichier de contenu utilise l’autorité et le chemin d’accès suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-171">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="37d31-172">**Autorité** : application:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="37d31-173">**Chemin** : nom du fichier de contenu, y compris son chemin relatif à l’emplacement, dans le système de fichiers, de l’assembly exécutable principal de l’application.</span><span class="sxs-lookup"><span data-stu-id="37d31-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="37d31-174">L’exemple suivant montre l’URI à en-tête pack pour un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], situé dans le même dossier que l’assembly exécutable.</span><span class="sxs-lookup"><span data-stu-id="37d31-174">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="37d31-175">L’exemple suivant montre l’URI à en-tête pack pour un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], situé dans un sous-dossier relatif à l’assembly exécutable de l’application.</span><span class="sxs-lookup"><span data-stu-id="37d31-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="37d31-176">Impossible d’accéder aux fichiers de contenu HTML.</span><span class="sxs-lookup"><span data-stu-id="37d31-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="37d31-177">Le modèle d’URI prend uniquement en charge la navigation vers les fichiers HTML qui se trouvent sur le site d’origine.</span><span class="sxs-lookup"><span data-stu-id="37d31-177">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="37d31-178">URI à en-tête pack de site d’origine</span><span class="sxs-lookup"><span data-stu-id="37d31-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="37d31-179">L’URI à en-tête pack pour un fichier de site d’origine utilise l’autorité et le chemin d’accès suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-179">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="37d31-180">**Autorité** : siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="37d31-181">**Chemin** : nom du fichier de site d’origine, y compris son chemin relatif à l’emplacement à partir duquel l’assembly exécutable a été lancé.</span><span class="sxs-lookup"><span data-stu-id="37d31-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="37d31-182">L’exemple suivant montre l’URI à en-tête pack pour un fichier de site d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stocké à l’emplacement à partir duquel l’assembly exécutable est lancé.</span><span class="sxs-lookup"><span data-stu-id="37d31-182">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="37d31-183">L’exemple suivant montre l’URI à en-tête pack pour un fichier de site d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stocké dans un sous-dossier relatif à l’emplacement à partir duquel l’assembly exécutable de l’application est lancé.</span><span class="sxs-lookup"><span data-stu-id="37d31-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="37d31-184">Fichiers d’échange</span><span class="sxs-lookup"><span data-stu-id="37d31-184">Page Files</span></span>

<span data-ttu-id="37d31-185">Les fichiers XAML qui sont configurés en tant qu’éléments `Page` MSBuild sont compilés dans des assemblys de la même façon que les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="37d31-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="37d31-186">Par conséquent, les éléments de `Page` MSBuild peuvent être identifiés à l’aide d’URI à en-tête pack pour les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="37d31-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="37d31-187">Les types de fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] couramment configurés en tant qu’éléments de`Page` MSBuild ont l’un des éléments suivants comme élément racine :</span><span class="sxs-lookup"><span data-stu-id="37d31-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="37d31-188">URI à en-tête pack absolus et relatifs</span><span class="sxs-lookup"><span data-stu-id="37d31-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="37d31-189">Un URI à en-tête pack complet comprend le schéma, l’autorité et le chemin d’accès, et il est considéré comme un URI à en-tête pack absolu.</span><span class="sxs-lookup"><span data-stu-id="37d31-189">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="37d31-190">En guise de simplification pour les développeurs, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments vous permettent généralement de définir des attributs appropriés avec un URI à en-tête pack relatif, qui comprend uniquement le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="37d31-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="37d31-191">Par exemple, considérez l’URI à en-tête pack absolu suivant pour un fichier de ressources dans l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-191">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="37d31-192">L’URI à en-tête pack relatif qui fait référence à ce fichier de ressources est le suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-192">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="37d31-193">Étant donné que les fichiers de site d’origine ne sont pas associés à des assemblys, ils ne peuvent être référencés qu’avec des URI à en-tête pack absolus.</span><span class="sxs-lookup"><span data-stu-id="37d31-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="37d31-194">Par défaut, un URI à en-tête pack relatif est considéré comme relatif à l’emplacement du balisage ou du code qui contient la référence.</span><span class="sxs-lookup"><span data-stu-id="37d31-194">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="37d31-195">Toutefois, si une barre oblique inverse de début est utilisée, la référence URI à en-tête pack relative est alors considérée comme relative à la racine de l’application.</span><span class="sxs-lookup"><span data-stu-id="37d31-195">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="37d31-196">Par exemple, considérez la structure de projet suivante.</span><span class="sxs-lookup"><span data-stu-id="37d31-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="37d31-197">Si Page1. xaml contient un URI qui fait référence à la *racine*\SubFolder\Page2.xaml, la référence peut utiliser l’URI à en-tête pack relatif suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-197">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="37d31-198">Si Page1. xaml contient un URI qui fait référence à la *racine*\Page2.xaml, la référence peut utiliser l’URI à en-tête pack relatif suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-198">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="37d31-199">Résolution des URI à en-tête pack</span><span class="sxs-lookup"><span data-stu-id="37d31-199">Pack URI Resolution</span></span>

<span data-ttu-id="37d31-200">Le format des URI à en-tête pack permet aux URI à en-tête pack pour les différents types de fichiers de se présenter de la même façon.</span><span class="sxs-lookup"><span data-stu-id="37d31-200">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="37d31-201">Par exemple, considérez l’URI à en-tête pack absolu suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-201">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="37d31-202">Cet URI à en-tête pack absolu peut faire référence à un fichier de ressources dans l’assembly local ou à un fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="37d31-202">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="37d31-203">Il en va de même pour l’URI relatif suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-203">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="37d31-204">Pour déterminer le type de fichier auquel un URI à en-tête pack fait référence, WPF résout les URI des fichiers de ressources dans les assemblys locaux et les fichiers de contenu à l’aide de l’heuristique suivante :</span><span class="sxs-lookup"><span data-stu-id="37d31-204">In order to determine the type of file that a pack URI refers to, WPF resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="37d31-205">Sondez les métadonnées de l’assembly pour un attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> qui correspond à l’URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="37d31-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="37d31-206">Si l’attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est trouvé, le chemin d’accès de l’URI à en-tête pack fait référence à un fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="37d31-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="37d31-207">Si l’attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est introuvable, Sondez les fichiers de ressources définis qui sont compilés dans l’assembly local.</span><span class="sxs-lookup"><span data-stu-id="37d31-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="37d31-208">Si un fichier de ressources qui correspond au chemin d’accès de l’URI à en-tête pack est trouvé, le chemin d’accès de l’URI à en-tête pack fait référence à un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="37d31-208">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="37d31-209">Si la ressource est introuvable, la <xref:System.Uri> créée en interne n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="37d31-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="37d31-210">La résolution d’URI ne s’applique pas aux URI qui font référence aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="37d31-210">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="37d31-211">Fichiers de contenu dans les assemblys référencés : ces types de fichiers ne sont pas pris en charge par WPF.</span><span class="sxs-lookup"><span data-stu-id="37d31-211">Content files in referenced assemblies: these file types are not supported by WPF.</span></span>

- <span data-ttu-id="37d31-212">Fichiers incorporés dans les assemblys référencés : les URI qui les identifient sont uniques, car ils incluent à la fois le nom de l’assembly référencé et le suffixe `;component`.</span><span class="sxs-lookup"><span data-stu-id="37d31-212">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="37d31-213">Fichiers du site d’origine : les URI qui les identifient sont uniques car ce sont les seuls fichiers qui peuvent être identifiés par des URI à en-tête pack qui contiennent l’autorité siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="37d31-213">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="37d31-214">Une simplification de la résolution des URI à en-tête pack permet au code d’être quelque peu indépendant des emplacements des fichiers de ressources et de contenu.</span><span class="sxs-lookup"><span data-stu-id="37d31-214">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="37d31-215">Par exemple, si vous avez un fichier de ressources dans l’assembly local qui est reconfiguré pour être un fichier de contenu, l’URI à en-tête pack pour la ressource reste le même, tout comme le code qui utilise l’URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="37d31-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="37d31-216">Programmation avec des URI à en-tête pack</span><span class="sxs-lookup"><span data-stu-id="37d31-216">Programming with Pack URIs</span></span>

<span data-ttu-id="37d31-217">De nombreuses classes WPF implémentent des propriétés qui peuvent être définies avec des URI à en-tête pack, notamment :</span><span class="sxs-lookup"><span data-stu-id="37d31-217">Many WPF classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="37d31-218">Ces propriétés peuvent être définies à partir du balisage et du code.</span><span class="sxs-lookup"><span data-stu-id="37d31-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="37d31-219">Cette section décrit les constructions de base pour les deux, et fournit des exemples de scénarios courants.</span><span class="sxs-lookup"><span data-stu-id="37d31-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="37d31-220">Utilisation d’URI à en-tête pack dans le balisage</span><span class="sxs-lookup"><span data-stu-id="37d31-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="37d31-221">Un URI à en-tête pack est spécifié dans le balisage en définissant l’élément d’un attribut avec l’URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="37d31-221">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="37d31-222">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="37d31-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="37d31-223">Le tableau 1 illustre les différents URI à en-tête pack absolus que vous pouvez spécifier dans le balisage.</span><span class="sxs-lookup"><span data-stu-id="37d31-223">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="37d31-224">Tableau 1 : URI à en-tête pack absolus dans le balisage</span><span class="sxs-lookup"><span data-stu-id="37d31-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="37d31-225">Fichier</span><span class="sxs-lookup"><span data-stu-id="37d31-225">File</span></span>|<span data-ttu-id="37d31-226">URI à en-tête pack absolu</span><span class="sxs-lookup"><span data-stu-id="37d31-226">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="37d31-227">Fichier de ressources - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-228">Fichier de ressources dans un sous-dossier - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-229">Fichier de ressources - assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-230">Fichier de ressources dans un sous-dossier de l’assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-231">Fichier de ressources dans un assembly référencé avec version</span><span class="sxs-lookup"><span data-stu-id="37d31-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-232">Fichier de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="37d31-233">Fichier contenu dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="37d31-234">Fichier de site d’origine</span><span class="sxs-lookup"><span data-stu-id="37d31-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="37d31-235">Fichier de site d’origine dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="37d31-236">Le tableau 2 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le balisage.</span><span class="sxs-lookup"><span data-stu-id="37d31-236">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="37d31-237">Tableau 2 : URI à en-tête pack relatifs dans le balisage</span><span class="sxs-lookup"><span data-stu-id="37d31-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="37d31-238">Fichier</span><span class="sxs-lookup"><span data-stu-id="37d31-238">File</span></span>|<span data-ttu-id="37d31-239">URI à en-tête pack relatif</span><span class="sxs-lookup"><span data-stu-id="37d31-239">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="37d31-240">Fichier de ressources dans un assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-241">Fichier de ressources dans un sous-dossier de l’assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-242">Fichier de ressources dans l’assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-243">Fichier de ressources dans un sous-dossier de l’assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="37d31-244">Fichier de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="37d31-245">Fichier contenu dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="37d31-246">Utilisation d’URI à en-tête pack dans le code</span><span class="sxs-lookup"><span data-stu-id="37d31-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="37d31-247">Vous spécifiez un URI à en-tête pack dans le code en instanciant la classe <xref:System.Uri> et en passant l’URI à en-tête pack en tant que paramètre au constructeur.</span><span class="sxs-lookup"><span data-stu-id="37d31-247">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="37d31-248">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="37d31-249">Par défaut, la classe <xref:System.Uri> considère que les URI à en-tête pack sont absolus.</span><span class="sxs-lookup"><span data-stu-id="37d31-249">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="37d31-250">Par conséquent, une exception est levée lorsqu’une instance de la classe <xref:System.Uri> est créée avec un URI à en-tête pack relatif.</span><span class="sxs-lookup"><span data-stu-id="37d31-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="37d31-251">Heureusement, la surcharge <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> du constructeur de classe <xref:System.Uri> accepte un paramètre de type <xref:System.UriKind> pour vous permettre de spécifier si un URI à en-tête pack est absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="37d31-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="37d31-252">Vous devez spécifier uniquement <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> lorsque vous êtes certain que l’URI à en-tête pack fourni est l’un ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="37d31-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="37d31-253">Si vous ne connaissez pas le type d’URI à en-tête pack utilisé, par exemple quand un utilisateur entre un URI à en-tête pack au moment de l’exécution, utilisez <xref:System.UriKind.RelativeOrAbsolute> à la place.</span><span class="sxs-lookup"><span data-stu-id="37d31-253">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="37d31-254">Le tableau 3 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le code à l’aide de <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="37d31-254">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="37d31-255">Tableau 3 : URI à en-tête pack absolus dans le code</span><span class="sxs-lookup"><span data-stu-id="37d31-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="37d31-256">Fichier</span><span class="sxs-lookup"><span data-stu-id="37d31-256">File</span></span>|<span data-ttu-id="37d31-257">URI à en-tête pack absolu</span><span class="sxs-lookup"><span data-stu-id="37d31-257">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="37d31-258">Fichier de ressources - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-259">Fichier de ressources dans un sous-dossier - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-260">Fichier de ressources - assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-261">Fichier de ressources dans un sous-dossier de l’assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-262">Fichier de ressources dans un assembly référencé avec version</span><span class="sxs-lookup"><span data-stu-id="37d31-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-263">Fichier de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-264">Fichier contenu dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-265">Fichier de site d’origine</span><span class="sxs-lookup"><span data-stu-id="37d31-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="37d31-266">Fichier de site d’origine dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="37d31-267">Le tableau 4 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le code à l’aide de <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="37d31-267">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="37d31-268">Tableau 4 : URI à en-tête pack relatifs dans le code</span><span class="sxs-lookup"><span data-stu-id="37d31-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="37d31-269">Fichier</span><span class="sxs-lookup"><span data-stu-id="37d31-269">File</span></span>|<span data-ttu-id="37d31-270">URI à en-tête pack relatif</span><span class="sxs-lookup"><span data-stu-id="37d31-270">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="37d31-271">Fichier de ressources - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="37d31-272">Fichier de ressources dans un sous-dossier - assembly local</span><span class="sxs-lookup"><span data-stu-id="37d31-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="37d31-273">Fichier de ressources - assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="37d31-274">Fichier de ressources dans un sous-dossier - assembly référencé</span><span class="sxs-lookup"><span data-stu-id="37d31-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="37d31-275">Fichier de contenu</span><span class="sxs-lookup"><span data-stu-id="37d31-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="37d31-276">Fichier contenu dans un sous-dossier</span><span class="sxs-lookup"><span data-stu-id="37d31-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="37d31-277">Scénarios courants d’URI à en-tête pack</span><span class="sxs-lookup"><span data-stu-id="37d31-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="37d31-278">Les sections précédentes ont expliqué comment construire des URI à en-tête pack pour identifier les fichiers de ressources, de contenu et de site d’origine.</span><span class="sxs-lookup"><span data-stu-id="37d31-278">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="37d31-279">Dans WPF, ces constructions sont utilisées de différentes façons, et les sections suivantes couvrent plusieurs utilisations courantes.</span><span class="sxs-lookup"><span data-stu-id="37d31-279">In WPF, these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="37d31-280">Spécification de l’interface utilisateur à afficher au démarrage d’une application</span><span class="sxs-lookup"><span data-stu-id="37d31-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="37d31-281"><xref:System.Windows.Application.StartupUri%2A> spécifie le premier [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à afficher lorsqu’une application WPF est lancée.</span><span class="sxs-lookup"><span data-stu-id="37d31-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a WPF application is launched.</span></span> <span data-ttu-id="37d31-282">Pour les applications autonomes, la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut être une fenêtre, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="37d31-283">Les applications autonomes et les applications de navigateur XAML (XBAP) peuvent également spécifier une page comme interface utilisateur initiale, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-283">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="37d31-284">Si l’application est une application autonome et qu’une page est spécifiée avec <xref:System.Windows.Application.StartupUri%2A>, WPF ouvre un <xref:System.Windows.Navigation.NavigationWindow> pour héberger la page.</span><span class="sxs-lookup"><span data-stu-id="37d31-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, WPF opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="37d31-285">Pour les applications XBAP, la page est affichée dans le navigateur hôte.</span><span class="sxs-lookup"><span data-stu-id="37d31-285">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="37d31-286">Navigation vers une page</span><span class="sxs-lookup"><span data-stu-id="37d31-286">Navigating to a Page</span></span>

<span data-ttu-id="37d31-287">L’exemple suivant montre comment naviguer vers une page.</span><span class="sxs-lookup"><span data-stu-id="37d31-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="37d31-288">Pour plus d’informations sur les différentes façons de naviguer dans WPF, consultez [vue d’ensemble](navigation-overview.md)de la navigation.</span><span class="sxs-lookup"><span data-stu-id="37d31-288">For more information on the various ways to navigate in WPF, see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="37d31-289">Spécification d’une icône de fenêtre</span><span class="sxs-lookup"><span data-stu-id="37d31-289">Specifying a Window Icon</span></span>

<span data-ttu-id="37d31-290">L’exemple suivant montre comment utiliser un URI pour spécifier l’icône d’une fenêtre.</span><span class="sxs-lookup"><span data-stu-id="37d31-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="37d31-291">Pour plus d'informations, consultez <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="37d31-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="37d31-292">Chargement de fichiers vidéo, audio et image</span><span class="sxs-lookup"><span data-stu-id="37d31-292">Loading Image, Audio, and Video Files</span></span>

<span data-ttu-id="37d31-293">WPF permet aux applications d’utiliser un large éventail de types de médias, qui peuvent tous être identifiés et chargés avec des URI à en-tête pack, comme illustré dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="37d31-293">WPF allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="37d31-294">Pour plus d’informations sur l’utilisation du contenu multimédia, consultez [Graphics and Multimedia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="37d31-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="37d31-295">Chargement d’un dictionnaire de ressources à partir du site d’origine</span><span class="sxs-lookup"><span data-stu-id="37d31-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="37d31-296">Les dictionnaires de ressources (<xref:System.Windows.ResourceDictionary>) peuvent être utilisés pour prendre en charge les thèmes d’application.</span><span class="sxs-lookup"><span data-stu-id="37d31-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="37d31-297">L’une des façons de créer et de gérer des thèmes consiste à créer plusieurs thèmes en tant que dictionnaires de ressources situés dans le site d’origine d’une application.</span><span class="sxs-lookup"><span data-stu-id="37d31-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="37d31-298">Ainsi, les thèmes peuvent être ajoutés et mis à jour sans qu’il soit nécessaire de recompiler et de redéployer une application.</span><span class="sxs-lookup"><span data-stu-id="37d31-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="37d31-299">Ces dictionnaires de ressources peuvent être identifiés et chargés à l’aide d’URI à en-tête pack, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="37d31-299">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="37d31-300">Pour obtenir une vue d’ensemble des thèmes dans WPF, consultez [styles et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="37d31-300">For an overview of themes in WPF, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37d31-301">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37d31-301">See also</span></span>

- [<span data-ttu-id="37d31-302">Fichiers de ressources, de contenu et de données d’une application WPF</span><span class="sxs-lookup"><span data-stu-id="37d31-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
