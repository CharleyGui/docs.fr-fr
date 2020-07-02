---
title: Fichiers de ressources, de contenu et de données d’application
description: Découvrez la prise en charge spéciale pour la configuration, l’identification et l’utilisation des fichiers de données d’application dans Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622859"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="699b0-103">Fichiers de ressources, de contenu et de données d'une application WPF</span><span class="sxs-lookup"><span data-stu-id="699b0-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="699b0-104">Les applications Microsoft Windows dépendent souvent de fichiers qui contiennent des données non exécutables, telles que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] des images, des vidéos et de l’audio.</span><span class="sxs-lookup"><span data-stu-id="699b0-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="699b0-105">Windows Presentation Foundation (WPF) offre une prise en charge spéciale pour la configuration, l’identification et l’utilisation de ces types de fichiers de données, appelés fichiers de données d’application.</span><span class="sxs-lookup"><span data-stu-id="699b0-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="699b0-106">Cette prise en charge repose sur un ensemble spécifique de types de fichier de données d’application, notamment :</span><span class="sxs-lookup"><span data-stu-id="699b0-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="699b0-107">**Fichiers de ressources**: fichiers de données compilés dans un assembly WPF exécutable ou bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="699b0-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="699b0-108">**Fichiers de contenu**: fichiers de données autonomes qui ont une association explicite avec un assembly WPF exécutable.</span><span class="sxs-lookup"><span data-stu-id="699b0-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="699b0-109">**Fichiers du site d’origine**: fichiers de données autonomes qui n’ont aucune association avec un assembly WPF exécutable.</span><span class="sxs-lookup"><span data-stu-id="699b0-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="699b0-110">Il existe une distinction importante entre ces trois types de fichier : les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération. En effet, un assembly les connaît explicitement.</span><span class="sxs-lookup"><span data-stu-id="699b0-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="699b0-111">Toutefois, pour les fichiers de site d’origine, un assembly n’a peut-être aucune connaissance du tout ou une connaissance implicite par le biais d’une référence URI (Uniform Resource Identifier) de Pack ; dans ce dernier cas, il n’y a aucune garantie que le fichier de site d’origine référencé existe réellement.</span><span class="sxs-lookup"><span data-stu-id="699b0-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="699b0-112">Pour référencer des fichiers de données d’application, Windows Presentation Foundation (WPF) utilise le schéma d’URI (Uniform Resource Identifier) Pack, qui est décrit en détail dans URI à en- [tête pack dans WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="699b0-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="699b0-113">Cette rubrique décrit comment configurer et utiliser des fichiers de données d’application.</span><span class="sxs-lookup"><span data-stu-id="699b0-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="699b0-114">Fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="699b0-114">Resource Files</span></span>  
 <span data-ttu-id="699b0-115">Si un fichier de données d’application doit toujours être disponible pour une application, le seul moyen de garantir cette disponibilité est de le compiler en un assembly exécutable principal d’une application ou en l’un de ses assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="699b0-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="699b0-116">Ce type de fichier de données d’application est connu sous le nom de *fichier de ressources*.</span><span class="sxs-lookup"><span data-stu-id="699b0-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="699b0-117">Vous devez utiliser des fichiers de ressources dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="699b0-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="699b0-118">Vous n’avez pas besoin de mettre à jour le contenu du fichier de ressources une fois qu’il a été compilé en un assembly.</span><span class="sxs-lookup"><span data-stu-id="699b0-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="699b0-119">Vous souhaitez simplifier la complexité de distribution d’une application en réduisant le nombre des dépendances de fichiers.</span><span class="sxs-lookup"><span data-stu-id="699b0-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="699b0-120">Votre fichier de données d’application doit être localisable (consultez [vue d’ensemble de la globalisation et de la localisation WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="699b0-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="699b0-121">Les fichiers de ressources décrits dans cette section sont différents des fichiers de ressources décrits dans les [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) et différents des ressources incorporées ou liées décrites dans [gérer les ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="699b0-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="699b0-122">Configuration des fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="699b0-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="699b0-123">Dans WPF, un fichier de ressources est un fichier inclus dans un projet Microsoft Build Engine (MSBuild) comme `Resource` élément.</span><span class="sxs-lookup"><span data-stu-id="699b0-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="699b0-124">Dans Visual Studio, vous créez un fichier de ressources en ajoutant un fichier à un projet et en affectant à la valeur `Build Action` `Resource` .</span><span class="sxs-lookup"><span data-stu-id="699b0-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="699b0-125">Lorsque le projet est généré, MSBuild compile la ressource dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="699b0-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="699b0-126">Utilisation des fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="699b0-126">Using Resource Files</span></span>  
 <span data-ttu-id="699b0-127">Pour charger un fichier de ressources, vous pouvez appeler la <xref:System.Windows.Application.GetResourceStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un URI à en-tête pack qui identifie le fichier de ressources souhaité.</span><span class="sxs-lookup"><span data-stu-id="699b0-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="699b0-128"><xref:System.Windows.Application.GetResourceStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de ressources en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="699b0-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="699b0-129">Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetResourceStream%2A> pour charger un fichier de <xref:System.Windows.Controls.Page> ressources et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> ( `pageFrame` ) :</span><span class="sxs-lookup"><span data-stu-id="699b0-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="699b0-130">Lorsque vous appelez <xref:System.Windows.Application.GetResourceStream%2A> vous donne accès au <xref:System.IO.Stream> , vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="699b0-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="699b0-131">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="699b0-132">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> ( `pageFrame` ) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="699b0-133">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="699b0-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="699b0-134">Fichiers de code d’application en tant que fichiers de ressources</span><span class="sxs-lookup"><span data-stu-id="699b0-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="699b0-135">Un ensemble spécial de fichiers de code d’application WPF peut être référencé à l’aide d’URI à en-tête pack, y compris les fenêtres, les pages, les documents dynamiques et les dictionnaires de ressources.</span><span class="sxs-lookup"><span data-stu-id="699b0-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="699b0-136">Par exemple, vous pouvez définir la <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> propriété avec un URI à en-tête pack qui référence la fenêtre ou la page que vous souhaitez charger au démarrage d’une application.</span><span class="sxs-lookup"><span data-stu-id="699b0-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="699b0-137">Vous pouvez le faire lorsqu’un fichier XAML est inclus dans un projet MSBuild en tant qu' `Page` élément.</span><span class="sxs-lookup"><span data-stu-id="699b0-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="699b0-138">Dans Visual Studio, vous ajoutez un nouveau <xref:System.Windows.Window> ,,, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> ou <xref:System.Windows.ResourceDictionary> à un projet ; `Build Action` par défaut, pour le fichier de balisage `Page` .</span><span class="sxs-lookup"><span data-stu-id="699b0-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="699b0-139">Lorsqu’un projet avec des `Page` éléments est compilé, les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments sont convertis au format binaire et compilés dans l’assembly associé.</span><span class="sxs-lookup"><span data-stu-id="699b0-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="699b0-140">Ainsi, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources classiques.</span><span class="sxs-lookup"><span data-stu-id="699b0-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="699b0-141">Si un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est configuré en tant qu' `Resource` élément et n’a pas de fichier code-behind, le brut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilé dans un assembly plutôt que dans une version binaire du brut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="699b0-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="699b0-142">Fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="699b0-142">Content Files</span></span>  
 <span data-ttu-id="699b0-143">Un *fichier de contenu* est distribué en tant que fichier libre avec un assembly exécutable.</span><span class="sxs-lookup"><span data-stu-id="699b0-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="699b0-144">Bien qu’ils ne soient pas compilés en un assembly, les assemblys sont compilés à l’aide de métadonnées qui établissent une association avec chaque fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="699b0-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="699b0-145">Vous devez utiliser des fichiers de contenu quand votre application nécessite un ensemble spécifique de fichiers de données d’application, que vous souhaitez pouvoir mettre à jour sans recompiler l’assembly qui les consomme.</span><span class="sxs-lookup"><span data-stu-id="699b0-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="699b0-146">Configuration des fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="699b0-146">Configuring Content Files</span></span>  
 <span data-ttu-id="699b0-147">Pour ajouter un fichier de contenu à un projet, un fichier de données d’application doit être inclus en tant qu' `Content` élément.</span><span class="sxs-lookup"><span data-stu-id="699b0-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="699b0-148">En outre, étant donné qu’un fichier de contenu n’est pas compilé directement dans l’assembly, vous devez définir l' `CopyToOutputDirectory` élément de métadonnées MSBuild pour spécifier que le fichier de contenu est copié vers un emplacement relatif à l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="699b0-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="699b0-149">Si vous souhaitez que la ressource soit copiée dans le dossier de sortie de génération chaque fois qu’un projet est généré, vous définissez l' `CopyToOutputDirectory` élément de métadonnées avec la `Always` valeur.</span><span class="sxs-lookup"><span data-stu-id="699b0-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="699b0-150">Dans le cas contraire, vous pouvez vous assurer que seule la version la plus récente de la ressource est copiée dans le dossier de sortie de la génération à l’aide de la `PreserveNewest` valeur.</span><span class="sxs-lookup"><span data-stu-id="699b0-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="699b0-151">L’exemple ci-dessous illustre un fichier configuré en tant que fichier de contenu copié dans le dossier de sortie de build uniquement quand une nouvelle version de la ressource est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="699b0-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="699b0-152">Dans Visual Studio, vous créez un fichier de contenu en ajoutant un fichier à un projet et en affectant à la valeur `Build Action` `Content` , et en définissant sa valeur `Copy to Output Directory` sur `Copy always` (identique à `Always` ) et `Copy if newer` (identique à `PreserveNewest` ).</span><span class="sxs-lookup"><span data-stu-id="699b0-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="699b0-153">Lorsque le projet est généré, un <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est compilé dans les métadonnées de l’assembly pour chaque fichier de contenu.</span><span class="sxs-lookup"><span data-stu-id="699b0-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="699b0-154">La valeur de <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implique le chemin d’accès au fichier de contenu par rapport à sa position dans le projet.</span><span class="sxs-lookup"><span data-stu-id="699b0-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="699b0-155">Par exemple, si un fichier de contenu se trouve dans un sous-dossier de projet, les informations supplémentaires relatives au chemin d’accès sont incorporées dans la <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur.</span><span class="sxs-lookup"><span data-stu-id="699b0-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="699b0-156">La <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur est également la valeur du chemin d’accès au fichier de contenu dans le dossier de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="699b0-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="699b0-157">Utilisation des fichiers de contenu</span><span class="sxs-lookup"><span data-stu-id="699b0-157">Using Content Files</span></span>  
 <span data-ttu-id="699b0-158">Pour charger un fichier de contenu, vous pouvez appeler la <xref:System.Windows.Application.GetContentStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un URI à en-tête pack qui identifie le fichier de contenu souhaité.</span><span class="sxs-lookup"><span data-stu-id="699b0-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="699b0-159"><xref:System.Windows.Application.GetContentStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de contenu en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="699b0-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="699b0-160">Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetContentStream%2A> pour charger un fichier de <xref:System.Windows.Controls.Page> contenu et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="699b0-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="699b0-161">Lorsque vous appelez <xref:System.Windows.Application.GetContentStream%2A> vous donne accès au <xref:System.IO.Stream> , vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="699b0-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="699b0-162">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="699b0-163">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> ( `pageFrame` ) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="699b0-164">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="699b0-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="699b0-165">Fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="699b0-165">Site of Origin Files</span></span>  
 <span data-ttu-id="699b0-166">Les fichiers de ressources ont une relation explicite avec les assemblys avec lesquels ils sont distribués, comme défini par le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="699b0-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="699b0-167">Toutefois, vous pouvez être amené à établir une relation implicite ou inexistante entre un assembly et un fichier de données d’application, notamment dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="699b0-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="699b0-168">Un fichier n’existe pas au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="699b0-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="699b0-169">Vous ignorez de quels fichiers votre assembly a besoin jusqu’au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="699b0-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="699b0-170">Vous souhaitez pouvoir mettre à jour des fichiers sans recompiler l’assembly auquel ils sont associés.</span><span class="sxs-lookup"><span data-stu-id="699b0-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="699b0-171">Votre application utilise des fichiers de données volumineux, par exemple des fichiers audio et vidéo, et vous souhaitez que les utilisateurs aient le choix de les télécharger ou non.</span><span class="sxs-lookup"><span data-stu-id="699b0-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="699b0-172">Il est possible de charger ces types de fichiers à l’aide de schémas d’URI traditionnels, tels que les `file:///` `http://` schémas et.</span><span class="sxs-lookup"><span data-stu-id="699b0-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="699b0-173">Toutefois, les `file:///` `http://` schémas et requièrent que votre application ait une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="699b0-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="699b0-174">Si votre application est une application de navigateur XAML (XBAP) lancée à partir d’Internet ou d’un intranet, et qu’elle demande uniquement le jeu d’autorisations autorisé pour les applications lancées à partir de ces emplacements, les fichiers libres peuvent uniquement être chargés à partir du site d’origine de l’application (emplacement de lancement).</span><span class="sxs-lookup"><span data-stu-id="699b0-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="699b0-175">Ces fichiers sont appelés fichiers *de site d’origine* .</span><span class="sxs-lookup"><span data-stu-id="699b0-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="699b0-176">Les fichiers du site d’origine sont la seule option pour les applications partiellement fiables. Toutefois, ils ne se limitent pas à ces applications.</span><span class="sxs-lookup"><span data-stu-id="699b0-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="699b0-177">Les applications entièrement fiables peuvent tout de même avoir besoin de charger des fichiers de données d’application dont ils n’ont pas connaissance au moment de la génération. Bien que les applications entièrement fiables puissent utiliser file:///, les fichiers de données d’application sont probablement installés dans le même dossier ou sous-dossier que l’assembly d’application.</span><span class="sxs-lookup"><span data-stu-id="699b0-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="699b0-178">Dans ce cas, l’utilisation du référencement du site d’origine est plus facile que l’utilisation de file:///, car avec file:/// vous devez résoudre le chemin complet du fichier.</span><span class="sxs-lookup"><span data-stu-id="699b0-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="699b0-179">Les fichiers de site d’origine ne sont pas mis en cache avec une application de navigateur XAML (XBAP) sur un ordinateur client, tandis que les fichiers de contenu sont.</span><span class="sxs-lookup"><span data-stu-id="699b0-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="699b0-180">Ils sont donc téléchargés à la demande.</span><span class="sxs-lookup"><span data-stu-id="699b0-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="699b0-181">Si une application de navigateur XAML (XBAP) contient des fichiers multimédias volumineux, leur configuration en tant que fichiers de site d’origine signifie que le lancement de l’application initiale est beaucoup plus rapide et que les fichiers ne sont téléchargés qu’à la demande.</span><span class="sxs-lookup"><span data-stu-id="699b0-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="699b0-182">Configuration des fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="699b0-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="699b0-183">Si vos fichiers de site d’origine sont inexistants ou inconnus au moment de la compilation, vous devez utiliser des mécanismes de déploiement traditionnels pour vous assurer que les fichiers requis sont disponibles au moment de l’exécution, y compris en utilisant le `XCopy` programme de ligne de commande ou le Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="699b0-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="699b0-184">Si vous savez au moment de la compilation les fichiers que vous souhaitez placer sur le site d’origine, mais que vous souhaitez toujours éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un projet MSBuild en tant qu' `None` élément.</span><span class="sxs-lookup"><span data-stu-id="699b0-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="699b0-185">Comme pour les fichiers de contenu, vous devez définir l' `CopyToOutputDirectory` attribut MSBuild pour spécifier que le fichier du site d’origine est copié vers un emplacement relatif à l’assembly généré, en spécifiant la `Always` valeur ou la `PreserveNewest` valeur.</span><span class="sxs-lookup"><span data-stu-id="699b0-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="699b0-186">Dans Visual Studio, vous créez un fichier de site d’origine en ajoutant un fichier à un projet et en affectant à la valeur `Build Action` `None` .</span><span class="sxs-lookup"><span data-stu-id="699b0-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="699b0-187">Lorsque le projet est généré, MSBuild copie les fichiers spécifiés dans le dossier de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="699b0-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="699b0-188">Utilisation des fichiers du site d’origine</span><span class="sxs-lookup"><span data-stu-id="699b0-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="699b0-189">Pour charger un fichier de site d’origine, vous pouvez appeler la <xref:System.Windows.Application.GetRemoteStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un URI à en-tête pack qui identifie le fichier de site d’origine souhaité.</span><span class="sxs-lookup"><span data-stu-id="699b0-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="699b0-190"><xref:System.Windows.Application.GetRemoteStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de site d’origine en tant que <xref:System.IO.Stream> et décrit son type de contenu.</span><span class="sxs-lookup"><span data-stu-id="699b0-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="699b0-191">Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetRemoteStream%2A> pour charger un <xref:System.Windows.Controls.Page> fichier de site d’origine et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="699b0-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="699b0-192">Lorsque vous appelez <xref:System.Windows.Application.GetRemoteStream%2A> vous donne accès au <xref:System.IO.Stream> , vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir.</span><span class="sxs-lookup"><span data-stu-id="699b0-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="699b0-193">Au lieu de cela, vous pouvez laisser WPF s’occuper de l’ouverture et de la conversion <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="699b0-194">L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> ( `pageFrame` ) à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="699b0-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="699b0-195">L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="699b0-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="699b0-196">Regénération après changement du type de build</span><span class="sxs-lookup"><span data-stu-id="699b0-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="699b0-197">Après avoir changé le type de build d’un fichier de données d’application, vous devez regénérer l’application entière pour vérifier que ces changements sont bien appliqués.</span><span class="sxs-lookup"><span data-stu-id="699b0-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="699b0-198">Si vous générez uniquement l’application, les changements ne sont pas appliqués.</span><span class="sxs-lookup"><span data-stu-id="699b0-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699b0-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="699b0-199">See also</span></span>

- [<span data-ttu-id="699b0-200">URI à en-tête pack dans WPF</span><span class="sxs-lookup"><span data-stu-id="699b0-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
