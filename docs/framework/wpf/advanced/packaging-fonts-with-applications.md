---
title: Empaquetage de polices avec des applications
description: Découvrez comment empaqueter des polices avec une application Windows Presentation Foundation, notamment ajouter des polices en tant que contenu et éléments de ressource, et limiter l’utilisation des polices.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166355"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="daed2-103">Empaquetage de polices avec des applications</span><span class="sxs-lookup"><span data-stu-id="daed2-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="daed2-104">Cette rubrique fournit une vue d’ensemble de l’empaquetage des polices avec votre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="daed2-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daed2-105">Comme avec la plupart des types de logiciels, les fichiers de police sont sous licence et ne sont pas vendus.</span><span class="sxs-lookup"><span data-stu-id="daed2-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="daed2-106">Les licences qui régissent l’utilisation des polices varient d’un fournisseur à l’autre, mais en général, la plupart des licences, y compris celles qui couvrent les polices fournies par Microsoft avec les applications et Windows, ne permettent pas d’incorporer les polices dans des applications ou de les redistribuer autrement.</span><span class="sxs-lookup"><span data-stu-id="daed2-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="daed2-107">Par conséquent, en tant que développeur, c’est à vous de vérifier que vous disposez des droits de licence nécessaires pour toute police incorporée dans une application ou redistribuée.</span><span class="sxs-lookup"><span data-stu-id="daed2-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="daed2-108">Présentation de l’empaquetage de polices</span><span class="sxs-lookup"><span data-stu-id="daed2-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="daed2-109">Vous pouvez facilement empaqueter des polices en tant que ressources dans vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications pour afficher le texte de l’interface utilisateur et d’autres types de contenu textuel.</span><span class="sxs-lookup"><span data-stu-id="daed2-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="daed2-110">Les polices peuvent être séparées des fichiers d’assembly de l’application ou y être incorporées.</span><span class="sxs-lookup"><span data-stu-id="daed2-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="daed2-111">Vous pouvez également créer une bibliothèque de polices de ressources uniquement, que votre application peut référencer.</span><span class="sxs-lookup"><span data-stu-id="daed2-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="daed2-112">Les polices OpenType et TrueType® contiennent un indicateur de type, fsType, qui indique les droits de licence d’incorporation de polices pour la police.</span><span class="sxs-lookup"><span data-stu-id="daed2-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="daed2-113">Toutefois, cet indicateur de type concerne uniquement les polices incorporées stockées dans un document. Il ne concerne pas les polices incorporées dans une application.</span><span class="sxs-lookup"><span data-stu-id="daed2-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="daed2-114">Vous pouvez récupérer les droits d’incorporation de police pour une police en créant un <xref:System.Windows.Media.GlyphTypeface> objet et en référençant sa <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="daed2-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="daed2-115">Pour plus d’informations sur l’indicateur fsType, reportez-vous à la section « OS/2 et métriques Windows » de la [spécification OpenType](https://www.microsoft.com/typography/otspec/os2.htm) .</span><span class="sxs-lookup"><span data-stu-id="daed2-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="daed2-116">Le site Web [Microsoft Typography](https://docs.microsoft.com/typography/) comprend des informations de contact qui peuvent vous aider à localiser un fournisseur de polices particulier ou à rechercher un fournisseur de polices pour un travail personnalisé.</span><span class="sxs-lookup"><span data-stu-id="daed2-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="daed2-117">Ajout de polices comme éléments de contenu</span><span class="sxs-lookup"><span data-stu-id="daed2-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="daed2-118">Vous pouvez ajouter des polices à votre application sous forme d’éléments de contenu de projet séparés des fichiers d’assembly de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="daed2-119">Cela signifie que les éléments de contenu ne sont pas incorporés sous forme de ressources dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="daed2-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="daed2-120">L’exemple de fichier projet suivant montre comment définir des éléments de contenu.</span><span class="sxs-lookup"><span data-stu-id="daed2-120">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="daed2-121">Pour vérifier que l’application peut utiliser les polices au moment de l’exécution, ces dernières doivent être accessibles dans le répertoire de déploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="daed2-122">L' `<CopyToOutputDirectory>` élément dans le fichier projet de l’application vous permet de copier automatiquement les polices dans le répertoire de déploiement de l’application pendant le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="daed2-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="daed2-123">L’exemple de fichier projet suivant montre comment copier les polices dans le répertoire de déploiement.</span><span class="sxs-lookup"><span data-stu-id="daed2-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="daed2-124">L’exemple de code suivant montre comment référencer la police de l’application comme élément de contenu. L’élément de contenu référencé doit être dans le même répertoire que les fichiers d’assembly de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="daed2-125">Ajout de polices comme éléments de ressource</span><span class="sxs-lookup"><span data-stu-id="daed2-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="daed2-126">Vous pouvez ajouter des polices à votre application sous forme d’éléments de ressource de projet incorporés dans les fichiers d’assembly de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="daed2-127">L’utilisation d’un sous-répertoire distinct pour les ressources permet d’organiser les fichiers projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="daed2-128">L’exemple de fichier projet suivant montre comment définir des polices comme éléments de ressource dans un sous-répertoire distinct.</span><span class="sxs-lookup"><span data-stu-id="daed2-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="daed2-129">Quand vous ajoutez des polices en tant que ressources à votre application, assurez-vous que vous définissez l' `<Resource>` élément, et non l' `<EmbeddedResource>` élément dans le fichier projet de votre application.</span><span class="sxs-lookup"><span data-stu-id="daed2-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="daed2-130">L' `<EmbeddedResource>` élément pour l’action de génération n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="daed2-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="daed2-131">L’exemple de balisage suivant indique comment référencer les ressources de police de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="daed2-132">Référencement d’éléments de ressource de police à partir du code</span><span class="sxs-lookup"><span data-stu-id="daed2-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="daed2-133">Pour référencer des éléments de ressource de police à partir du code, vous devez fournir une référence de ressource de police en deux parties : l’URI (Uniform Resource Identifier) de base ; et la référence d’emplacement de la police.</span><span class="sxs-lookup"><span data-stu-id="daed2-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="daed2-134">Ces valeurs sont utilisées comme paramètres pour la <xref:System.Windows.Media.FontFamily.%23ctor%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="daed2-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="daed2-135">L’exemple de code suivant montre comment référencer les ressources de police de l’application dans le sous-répertoire de projet appelé `resources` .</span><span class="sxs-lookup"><span data-stu-id="daed2-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="daed2-136">L’URI (Uniform Resource Identifier) de base peut inclure le sous-répertoire d’application où se trouve la ressource de police.</span><span class="sxs-lookup"><span data-stu-id="daed2-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="daed2-137">Dans ce cas, la référence de l’emplacement de la police n’a pas besoin de spécifier un répertoire, mais doit inclure un «» de début `./` , ce qui indique que la ressource de police se trouve dans le même répertoire que celui spécifié par l’URI (Uniform Resource Identifier) de base.</span><span class="sxs-lookup"><span data-stu-id="daed2-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="daed2-138">L’exemple de code suivant montre une autre façon de référencer l’élément de ressource de police. Il est équivalent à l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="daed2-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="daed2-139">Référencement de polices à partir du même sous-répertoire d’application</span><span class="sxs-lookup"><span data-stu-id="daed2-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="daed2-140">Vous pouvez placer le contenu de l’application et les fichiers de ressources dans le même sous-répertoire défini par l’utilisateur de votre projet d’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="daed2-141">L’exemple de fichier projet suivant montre une page de contenu et des ressources de police définies dans le même sous-répertoire.</span><span class="sxs-lookup"><span data-stu-id="daed2-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="daed2-142">Comme le contenu de l’application et la police sont dans le même sous-répertoire, la référence de police est relative au contenu d’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="daed2-143">Les exemples suivants montrent comment référencer les ressources de police de l’application quand la police se trouve dans le même répertoire que l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="daed2-144">Énumération des polices dans une application</span><span class="sxs-lookup"><span data-stu-id="daed2-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="daed2-145">Pour énumérer les polices comme éléments de ressource dans votre application, utilisez <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> la <xref:System.Windows.Media.Fonts.GetTypefaces%2A> méthode ou.</span><span class="sxs-lookup"><span data-stu-id="daed2-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="daed2-146">L’exemple suivant montre comment utiliser la <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> méthode pour retourner la collection d' <xref:System.Windows.Media.FontFamily> objets à partir de l’emplacement de la police de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="daed2-147">Dans cet exemple, l’application contient un sous-répertoire nommé « Resources ».</span><span class="sxs-lookup"><span data-stu-id="daed2-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="daed2-148">L’exemple suivant montre comment utiliser la <xref:System.Windows.Media.Fonts.GetTypefaces%2A> méthode pour retourner la collection d' <xref:System.Windows.Media.Typeface> objets à partir de l’emplacement de la police de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="daed2-149">Dans cet exemple, l’application contient un sous-répertoire nommé « Resources ».</span><span class="sxs-lookup"><span data-stu-id="daed2-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="daed2-150">Création d’une bibliothèque de ressources de police</span><span class="sxs-lookup"><span data-stu-id="daed2-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="daed2-151">Vous pouvez créer une bibliothèque de ressources uniquement qui contient seulement des polices, aucun code ne fait partie de ce type de projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="daed2-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="daed2-152">La création d’une bibliothèque de ressources uniquement est une technique courante pour découpler les ressources du code d’application qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="daed2-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="daed2-153">Cela permet également d’inclure l’assembly de bibliothèque dans plusieurs projets d’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="daed2-154">L’exemple de fichier projet suivant montre les parties clés d’un projet de bibliothèque de ressources uniquement.</span><span class="sxs-lookup"><span data-stu-id="daed2-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="daed2-155">Référencement d’une police dans une bibliothèque de ressources</span><span class="sxs-lookup"><span data-stu-id="daed2-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="daed2-156">Pour référencer une police dans une bibliothèque de ressources à partir de votre application, vous devez faire précéder la référence de police du nom de l’assembly de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="daed2-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="daed2-157">Dans cet exemple, l’assembly de ressource de police est « FontLibrary ».</span><span class="sxs-lookup"><span data-stu-id="daed2-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="daed2-158">Pour séparer le nom de l’assembly de la référence dans l’assembly, utilisez un caractère « ; ».</span><span class="sxs-lookup"><span data-stu-id="daed2-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="daed2-159">L’ajout du mot clé « Component » suivi de la référence au nom de la police complète la référence aux ressources de la bibliothèque de polices.</span><span class="sxs-lookup"><span data-stu-id="daed2-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="daed2-160">L’exemple de code suivant indique comment référencer une police dans un assembly de bibliothèque de ressources.</span><span class="sxs-lookup"><span data-stu-id="daed2-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="daed2-161">Ce kit de développement logiciel (SDK) contient un ensemble d’exemples de polices OpenType que vous pouvez utiliser avec les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="daed2-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="daed2-162">Les polices sont définies dans une bibliothèque de ressources uniquement.</span><span class="sxs-lookup"><span data-stu-id="daed2-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="daed2-163">Pour plus d’informations, consultez [exemple de Pack de polices OpenType](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="daed2-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="daed2-164">Limitations de l’utilisation des polices</span><span class="sxs-lookup"><span data-stu-id="daed2-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="daed2-165">La liste suivante décrit plusieurs limitations sur l’empaquetage et l’utilisation des polices dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications :</span><span class="sxs-lookup"><span data-stu-id="daed2-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="daed2-166">\*\*Bits d’autorisation d’incorporation de police : Les applications \*\* [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne vérifient ni n’appliquent les bits d’autorisation d’incorporation de police.</span><span class="sxs-lookup"><span data-stu-id="daed2-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="daed2-167">Pour plus d’informations, consultez la section [polices Introduction_to_Packing](#introduction_to_packaging_fonts) .</span><span class="sxs-lookup"><span data-stu-id="daed2-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="daed2-168">**Polices du site d’origine :** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications n’autorisent pas de référence de police à un URI (Uniform Resource Identifier) http ou FTP.</span><span class="sxs-lookup"><span data-stu-id="daed2-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="daed2-169">**URI absolu utilisant la notation** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pack : les applications ne vous permettent pas de créer un <xref:System.Windows.Media.FontFamily> objet par programmation en utilisant "Pack :" dans le cadre de la référence URI (Uniform Resource Identifier) absolue à une police.</span><span class="sxs-lookup"><span data-stu-id="daed2-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="daed2-170">Par exemple, `"pack://application:,,,/resources/#Pericles Light"` est une référence de police non valide.</span><span class="sxs-lookup"><span data-stu-id="daed2-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="daed2-171">**Incorporation de police automatique :** Au moment de la conception, il n’est pas possible de rechercher les polices utilisées par une application et de les incorporer automatiquement dans les ressources de l’application.</span><span class="sxs-lookup"><span data-stu-id="daed2-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="daed2-172">\*\*Sous-ensembles de polices : Les applications \*\* [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prennent pas en charge la création de sous-ensembles de polices pour les documents non fixes.</span><span class="sxs-lookup"><span data-stu-id="daed2-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="daed2-173">En cas de référence incorrecte, l’application utilise une police disponible à la place.</span><span class="sxs-lookup"><span data-stu-id="daed2-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daed2-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daed2-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- <span data-ttu-id="daed2-175">[Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/) (Typographie Microsoft : Liens, actualité et contacts)</span><span class="sxs-lookup"><span data-stu-id="daed2-175">[Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/)</span></span>
- <span data-ttu-id="daed2-176">[OpenType Specification](https://www.microsoft.com/typography/otspec/) (Spécification OpenType)</span><span class="sxs-lookup"><span data-stu-id="daed2-176">[OpenType Specification](https://www.microsoft.com/typography/otspec/)</span></span>
- [<span data-ttu-id="daed2-177">Fonctionnalités des polices OpenType</span><span class="sxs-lookup"><span data-stu-id="daed2-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="daed2-178">Exemple de pack de polices OpenType</span><span class="sxs-lookup"><span data-stu-id="daed2-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
