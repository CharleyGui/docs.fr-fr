---
title: Fichiers de ressources, de contenu et de données d’application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: ee636c49da64ad07ec5df2f11171b7f9aed713d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743365"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="50af6-102">Fichiers de ressources, de contenu et de données d'une application WPF</span><span class="sxs-lookup"><span data-stu-id="50af6-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="50af6-103">Les applications Microsoft Windows dépendent souvent de fichiers qui contiennent des données non exécutables, telles que des [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], des images, des vidéos et de l’audio.</span><span class="sxs-lookup"><span data-stu-id="50af6-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="50af6-104">Windows Presentation Foundation (WPF) offre une prise en charge spéciale pour la configuration, l’identification et l’utilisation de ces types de fichiers de données, appelés fichiers de données d’application.</span><span class="sxs-lookup"><span data-stu-id="50af6-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="50af6-105">Cette prise en charge repose sur un ensemble spécifique de types de fichier de données d’application, notamment :</span><span class="sxs-lookup"><span data-stu-id="50af6-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="50af6-106">**Fichiers de ressources**: fichiers de données compilés dans un assembly WPF exécutable ou bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="50af6-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="50af6-107">**Fichiers de contenu**: fichiers de données autonomes qui ont une association explicite avec un assembly WPF exécutable.</span><span class="sxs-lookup"><span data-stu-id="50af6-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="50af6-108">**Fichiers du site d’origine**: fichiers de données autonomes qui n’ont aucune association avec un assembly WPF exécutable.</span><span class="sxs-lookup"><span data-stu-id="50af6-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="50af6-109">Il existe une distinction importante entre ces trois types de fichier : les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération. En effet, un assembly les connaît explicitement.</span><span class="sxs-lookup"><span data-stu-id="50af6-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="50af6-110">Toutefois, pour les fichiers de site d’origine, un assembly n’a peut-être aucune connaissance du tout ou une connaissance implicite par le biais d’une référence URI (Uniform Resource Identifier) de Pack ; dans ce dernier cas, il n’y a aucune garantie que le fichier de site d’origine référencé existe réellement.</span><span class="sxs-lookup"><span data-stu-id="50af6-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="50af6-111">Pour référencer des fichiers de données d’application, Windows Presentation Foundation (WPF) utilise le schéma d’URI (Uniform Resource Identifier) Pack, qui est décrit en détail dans URI à en- [tête pack dans WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="50af6-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="50af6-112">Cette rubrique décrit comment configurer et utiliser des fichiers de données d’application.</span><span class="sxs-lookup"><span data-stu-id="50af6-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="50af6-113">Fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="50af6-113">Resource Files</span></span>  
 <span data-ttu-id="50af6-114">Si un fichier de données d’application doit toujours être disponible pour une application, le seul moyen de garantir cette disponibilité est de le compiler en un assembly exécutable principal d’une application ou en l’un de ses assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="50af6-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="50af6-115">Ce type de fichier de données d’application est connu sous le nom de *fichier de ressources*.</span><span class="sxs-lookup"><span data-stu-id="50af6-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="50af6-116">Vous devez utiliser des fichiers de ressources dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="50af6-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="50af6-117">Vous n’avez pas besoin de mettre à jour le contenu du fichier de ressources une fois qu’il a été compilé en un assembly.</span><span class="sxs-lookup"><span data-stu-id="50af6-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="50af6-118">Vous souhaitez simplifier la complexité de distribution d’une application en réduisant le nombre des dépendances de fichiers.</span><span class="sxs-lookup"><span data-stu-id="50af6-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="50af6-119">Votre fichier de données d’application doit être localisable (consultez [vue d’ensemble de la globalisation et de la localisation WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="50af6-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50af6-120">Les fichiers de ressources décrits dans cette section sont différents des fichiers de ressources décrits dans les [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) et différents des ressources incorporées ou liées décrites dans [gérer les ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="50af6-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="50af6-121">Configuration des fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="50af6-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="50af6-122">Dans WPF, un fichier de ressources est un fichier inclus dans un projet Microsoft Build Engine (MSBuild) en tant qu’élément de `Resource`.</span><span class="sxs-lookup"><span data-stu-id="50af6-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="50af6-123">Dans Visual Studio, vous créez un fichier de ressources en ajoutant un fichier à un projet et en définissant sa `Build Action` sur `Resource`.</span><span class="sxs-lookup"><span data-stu-id="50af6-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="50af6-124">Lorsque le projet est généré, MSBuild compile la ressource dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="50af6-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="50af6-125">Utilisation des fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="50af6-125">Using Resource Files</span></span>  
 <span data-ttu-id="50af6-126">Pour charger un fichier de ressources, vous pouvez appeler la méthode <xref:System.Windows.Application.GetResourceStream%2A> de la classe <xref:System.Windows.Application>, en passant un URI à en-tête pack qui identifie le fichier de ressources souhaité.</span><span class="sxs-lookup"><span data-stu-id="50af6-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="50af6-127"><xref:System.Windows.Application.GetResourceStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier de ressources en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="50af6-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="50af6-128">À titre d’exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetResourceStream%2A> pour charger un fichier de ressources <xref:System.Windows.Controls.Page> et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`) :</span><span class="sxs-lookup"><span data-stu-id="50af6-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="50af6-129">Quand vous appelez <xref:System.Windows.Application.GetResourceStream%2A> vous donne accès au <xref:System.IO.Stream>, vous devez effectuer la tâche supplémentaire de la convertir au type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="50af6-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="50af6-130">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion du <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="50af6-131">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans une <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="50af6-132">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="50af6-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="50af6-133">Fichiers de code d’application en tant que fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="50af6-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="50af6-134">Un ensemble spécial de fichiers de code d’application WPF peut être référencé à l’aide d’URI à en-tête pack, y compris les fenêtres, les pages, les documents dynamiques et les dictionnaires de ressources.</span><span class="sxs-lookup"><span data-stu-id="50af6-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="50af6-135">Par exemple, vous pouvez définir la propriété <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> avec un URI à en-tête pack qui référence la fenêtre ou la page que vous souhaitez charger au démarrage d’une application.</span><span class="sxs-lookup"><span data-stu-id="50af6-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="50af6-136">Vous pouvez effectuer cette opération quand un fichier XAML est inclus dans un projet MSBuild en tant qu’élément `Page`.</span><span class="sxs-lookup"><span data-stu-id="50af6-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="50af6-137">Dans Visual Studio, vous ajoutez une nouvelle <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>ou <xref:System.Windows.ResourceDictionary> à un projet ; par défaut, la `Build Action` du fichier de balisage est `Page`.</span><span class="sxs-lookup"><span data-stu-id="50af6-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="50af6-138">Lorsqu’un projet avec des éléments de `Page` est compilé, les éléments [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont convertis au format binaire et compilés dans l’assembly associé.</span><span class="sxs-lookup"><span data-stu-id="50af6-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="50af6-139">Ainsi, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources classiques.</span><span class="sxs-lookup"><span data-stu-id="50af6-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50af6-140">Si un fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est configuré en tant qu’élément de `Resource` et n’a pas de fichier code-behind, la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] brute est compilée dans un assembly plutôt que dans une version binaire du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]brut.</span><span class="sxs-lookup"><span data-stu-id="50af6-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="50af6-141">Fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="50af6-141">Content Files</span></span>  
 <span data-ttu-id="50af6-142">Un *fichier de contenu* est distribué en tant que fichier libre avec un assembly exécutable.</span><span class="sxs-lookup"><span data-stu-id="50af6-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="50af6-143">Bien qu’ils ne soient pas compilés en un assembly, les assemblys sont compilés à l’aide de métadonnées qui établissent une association avec chaque fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="50af6-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="50af6-144">Vous devez utiliser des fichiers de contenu quand votre application nécessite un ensemble spécifique de fichiers de données d’application, que vous souhaitez pouvoir mettre à jour sans recompiler l’assembly qui les consomme.</span><span class="sxs-lookup"><span data-stu-id="50af6-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="50af6-145">Configuration des fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="50af6-145">Configuring Content Files</span></span>  
 <span data-ttu-id="50af6-146">Pour ajouter un fichier de contenu à un projet, un fichier de données d’application doit être inclus en tant qu’élément de `Content`.</span><span class="sxs-lookup"><span data-stu-id="50af6-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="50af6-147">En outre, étant donné qu’un fichier de contenu n’est pas compilé directement dans l’assembly, vous devez définir l’élément de métadonnées `CopyToOutputDirectory` MSBuild pour spécifier que le fichier de contenu est copié vers un emplacement relatif à l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="50af6-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="50af6-148">Si vous souhaitez que la ressource soit copiée dans le dossier de sortie de la génération chaque fois qu’un projet est généré, vous définissez l’élément de métadonnées `CopyToOutputDirectory` avec la valeur `Always`.</span><span class="sxs-lookup"><span data-stu-id="50af6-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="50af6-149">Dans le cas contraire, vous pouvez vous assurer que seule la version la plus récente de la ressource est copiée dans le dossier de sortie de la génération à l’aide de la valeur `PreserveNewest`.</span><span class="sxs-lookup"><span data-stu-id="50af6-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="50af6-150">L’exemple ci-dessous illustre un fichier configuré en tant que fichier de contenu copié dans le dossier de sortie de build uniquement quand une nouvelle version de la ressource est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="50af6-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="50af6-151">Dans Visual Studio, vous créez un fichier de contenu en ajoutant un fichier à un projet et en définissant sa `Build Action` sur `Content`, et en définissant ses `Copy to Output Directory` sur `Copy always` (identique à `Always`) et `Copy if newer` (identique à `PreserveNewest`).</span><span class="sxs-lookup"><span data-stu-id="50af6-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="50af6-152">Lorsque le projet est généré, un attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est compilé dans les métadonnées de l’assembly pour chaque fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="50af6-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="50af6-153">La valeur de l' <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implique le chemin d’accès au fichier de contenu par rapport à sa position dans le projet.</span><span class="sxs-lookup"><span data-stu-id="50af6-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="50af6-154">Par exemple, si un fichier de contenu se trouve dans un sous-dossier de projet, les informations supplémentaires relatives au chemin d’accès sont incorporées dans la valeur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span><span class="sxs-lookup"><span data-stu-id="50af6-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="50af6-155">La valeur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est également la valeur du chemin d’accès au fichier de contenu dans le dossier de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="50af6-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="50af6-156">Utilisation des fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="50af6-156">Using Content Files</span></span>  
 <span data-ttu-id="50af6-157">Pour charger un fichier de contenu, vous pouvez appeler la méthode <xref:System.Windows.Application.GetContentStream%2A> de la classe <xref:System.Windows.Application>, en passant un URI à en-tête pack qui identifie le fichier de contenu souhaité.</span><span class="sxs-lookup"><span data-stu-id="50af6-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="50af6-158"><xref:System.Windows.Application.GetContentStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier de contenu en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="50af6-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="50af6-159">À titre d’exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetContentStream%2A> pour charger un fichier de contenu <xref:System.Windows.Controls.Page> et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="50af6-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="50af6-160">Quand vous appelez <xref:System.Windows.Application.GetContentStream%2A> vous donne accès au <xref:System.IO.Stream>, vous devez effectuer la tâche supplémentaire de la convertir au type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="50af6-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="50af6-161">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion du <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="50af6-162">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans une <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="50af6-163">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="50af6-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="50af6-164">Fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="50af6-164">Site of Origin Files</span></span>  
 <span data-ttu-id="50af6-165">Les fichiers de ressources ont une relation explicite avec les assemblys avec lesquels ils sont distribués, comme défini par le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span><span class="sxs-lookup"><span data-stu-id="50af6-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="50af6-166">Toutefois, vous pouvez être amené à établir une relation implicite ou inexistante entre un assembly et un fichier de données d’application, notamment dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="50af6-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="50af6-167">Un fichier n’existe pas au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="50af6-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="50af6-168">Vous ignorez de quels fichiers votre assembly a besoin jusqu’au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="50af6-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="50af6-169">Vous souhaitez pouvoir mettre à jour des fichiers sans recompiler l’assembly auquel ils sont associés.</span><span class="sxs-lookup"><span data-stu-id="50af6-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="50af6-170">Votre application utilise des fichiers de données volumineux, par exemple des fichiers audio et vidéo, et vous souhaitez que les utilisateurs aient le choix de les télécharger ou non.</span><span class="sxs-lookup"><span data-stu-id="50af6-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="50af6-171">Il est possible de charger ces types de fichiers à l’aide de schémas d’URI traditionnels, tels que les schémas file:///et http://.</span><span class="sxs-lookup"><span data-stu-id="50af6-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="50af6-172">Toutefois, pour les schémas file:/// et http:// votre application doit bénéficier d’une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="50af6-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="50af6-173">Si votre application est une application de navigateur XAML (XBAP) lancée à partir d’Internet ou d’un intranet, et qu’elle demande uniquement le jeu d’autorisations autorisé pour les applications lancées à partir de ces emplacements, les fichiers libres peuvent uniquement être chargés à partir du site d’origine de l’application (emplacement de lancement).</span><span class="sxs-lookup"><span data-stu-id="50af6-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="50af6-174">Ces fichiers sont appelés fichiers *de site d’origine* .</span><span class="sxs-lookup"><span data-stu-id="50af6-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="50af6-175">Les fichiers du site d’origine sont la seule option pour les applications partiellement fiables. Toutefois, ils ne se limitent pas à ces applications.</span><span class="sxs-lookup"><span data-stu-id="50af6-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="50af6-176">Les applications entièrement fiables peuvent tout de même avoir besoin de charger des fichiers de données d’application dont ils n’ont pas connaissance au moment de la génération. Bien que les applications entièrement fiables puissent utiliser file:///, les fichiers de données d’application sont probablement installés dans le même dossier ou sous-dossier que l’assembly d’application.</span><span class="sxs-lookup"><span data-stu-id="50af6-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="50af6-177">Dans ce cas, l’utilisation du référencement du site d’origine est plus facile que l’utilisation de file:///, car avec file:/// vous devez résoudre le chemin complet du fichier.</span><span class="sxs-lookup"><span data-stu-id="50af6-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50af6-178">Les fichiers de site d’origine ne sont pas mis en cache avec une application de navigateur XAML (XBAP) sur un ordinateur client, tandis que les fichiers de contenu sont.</span><span class="sxs-lookup"><span data-stu-id="50af6-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="50af6-179">Ils sont donc téléchargés à la demande.</span><span class="sxs-lookup"><span data-stu-id="50af6-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="50af6-180">Si une application de navigateur XAML (XBAP) contient des fichiers multimédias volumineux, leur configuration en tant que fichiers de site d’origine signifie que le lancement de l’application initiale est beaucoup plus rapide et que les fichiers ne sont téléchargés qu’à la demande.</span><span class="sxs-lookup"><span data-stu-id="50af6-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="50af6-181">Configuration des fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="50af6-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="50af6-182">Si vos fichiers de site d’origine sont inexistants ou inconnus au moment de la compilation, vous devez utiliser des mécanismes de déploiement traditionnels pour vous assurer que les fichiers requis sont disponibles au moment de l’exécution, y compris en utilisant le programme de ligne de commande `XCopy` ou le Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="50af6-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="50af6-183">Si vous savez au moment de la compilation les fichiers que vous souhaitez placer sur le site d’origine, mais que vous souhaitez toujours éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un projet MSBuild en tant qu’élément `None`.</span><span class="sxs-lookup"><span data-stu-id="50af6-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="50af6-184">Comme pour les fichiers de contenu, vous devez définir l’attribut `CopyToOutputDirectory` MSBuild pour spécifier que le fichier du site d’origine est copié vers un emplacement relatif à l’assembly généré, en spécifiant la valeur `Always` ou la valeur `PreserveNewest`.</span><span class="sxs-lookup"><span data-stu-id="50af6-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="50af6-185">Dans Visual Studio, vous créez un fichier de site d’origine en ajoutant un fichier à un projet et en définissant sa `Build Action` sur `None`.</span><span class="sxs-lookup"><span data-stu-id="50af6-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="50af6-186">Lorsque le projet est généré, MSBuild copie les fichiers spécifiés dans le dossier de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="50af6-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="50af6-187">Utilisation des fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="50af6-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="50af6-188">Pour charger un fichier de site d’origine, vous pouvez appeler la méthode <xref:System.Windows.Application.GetRemoteStream%2A> de la classe <xref:System.Windows.Application>, en passant un URI à en-tête pack qui identifie le fichier de site d’origine souhaité.</span><span class="sxs-lookup"><span data-stu-id="50af6-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="50af6-189"><xref:System.Windows.Application.GetRemoteStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier de site d’origine en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="50af6-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="50af6-190">À titre d’exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetRemoteStream%2A> pour charger un <xref:System.Windows.Controls.Page> site de fichier d’origine et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).</span><span class="sxs-lookup"><span data-stu-id="50af6-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="50af6-191">Quand vous appelez <xref:System.Windows.Application.GetRemoteStream%2A> vous donne accès au <xref:System.IO.Stream>, vous devez effectuer la tâche supplémentaire de la convertir au type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="50af6-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="50af6-192">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion du <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="50af6-193">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans une <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="50af6-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="50af6-194">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="50af6-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="50af6-195">Regénération après changement du type de build</span><span class="sxs-lookup"><span data-stu-id="50af6-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="50af6-196">Après avoir changé le type de build d’un fichier de données d’application, vous devez regénérer l’application entière pour vérifier que ces changements sont bien appliqués.</span><span class="sxs-lookup"><span data-stu-id="50af6-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="50af6-197">Si vous générez uniquement l’application, les changements ne sont pas appliqués.</span><span class="sxs-lookup"><span data-stu-id="50af6-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50af6-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50af6-198">See also</span></span>

- [<span data-ttu-id="50af6-199">URI à en-tête pack dans WPF</span><span class="sxs-lookup"><span data-stu-id="50af6-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
