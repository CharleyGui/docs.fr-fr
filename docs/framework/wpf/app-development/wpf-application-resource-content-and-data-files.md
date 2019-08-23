---
title: Fichiers de ressources, de contenu et de données d'une application WPF
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
ms.openlocfilehash: 57eae5067a72777db2c19331029b6df679a9fdce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956194"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Fichiers de ressources, de contenu et de données d'une application WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]les applications dépendent souvent de fichiers qui contiennent des données non exécutables, telles [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]que des images, des vidéos et de l’audio. Windows Presentation Foundation (WPF) offre une prise en charge spéciale pour la configuration, l’identification et l’utilisation de ces types de fichiers de données, appelés fichiers de données d’application. Cette prise en charge repose sur un ensemble spécifique de types de fichier de données d’application, notamment :  
  
- **Fichiers de ressources**: Fichiers de données compilés dans un fichier exécutable ou un assembly de bibliothèque [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] .  
  
- **Fichiers de contenu**: Fichiers de données autonomes qui ont une association explicite avec un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly exécutable.  
  
- **Fichiers du site d’origine**: Fichiers de données autonomes qui n’ont aucune association avec [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] un assembly exécutable.  
  
 Il existe une distinction importante entre ces trois types de fichier : les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération. En effet, un assembly les connaît explicitement. Toutefois, pour les fichiers de site d’origine, un assembly ne peut pas en avoir connaissance du tout, ou des connaissances [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] implicites à l’aide d’une référence à en-tête pack; le cas de ce dernier, il n’y a aucune garantie que le fichier de site d’origine référencé existe réellement.  
  
 Pour référencer des fichiers de données d’application, Windows Presentation Foundation (WPF [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ) utilise le schéma de Pack, qui est décrit en détail dans URI à en- [tête pack dans WPF](pack-uris-in-wpf.md)).  
  
 Cette rubrique décrit comment configurer et utiliser des fichiers de données d’application.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Fichiers de ressources  
 Si un fichier de données d’application doit toujours être disponible pour une application, le seul moyen de garantir cette disponibilité est de le compiler en un assembly exécutable principal d’une application ou en l’un de ses assemblys référencés. Ce type de fichier de données d’application est connu sous le nom de *fichier de ressources*.  
  
 Vous devez utiliser des fichiers de ressources dans les situations suivantes :  
  
- Vous n’avez pas besoin de mettre à jour le contenu du fichier de ressources une fois qu’il a été compilé en un assembly.  
  
- Vous souhaitez simplifier la complexité de distribution d’une application en réduisant le nombre des dépendances de fichiers.  
  
- Votre fichier de données d’application doit être localisable (consultez [vue d’ensemble de la globalisation et de la localisation WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Les fichiers de ressources décrits dans cette section sont différents des fichiers de ressources décrits dans les [ressources XAML](../advanced/xaml-resources.md) et différents des ressources incorporées ou liées décrites dans [gérer les ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Configuration des fichiers de ressources  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un fichier de ressources est un fichier inclus dans un projet Microsoft Build Engine (MSBuild) `Resource` en tant qu’élément.  
  
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
> Dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vous créez un fichier de ressources en ajoutant un fichier à un projet et en `Build Action` affectant à `Resource`la valeur.  
  
 Lorsque le projet est généré, MSBuild compile la ressource dans l’assembly.  
  
### <a name="using-resource-files"></a>Utilisation des fichiers de ressources  
 Pour charger un fichier de ressources, vous pouvez appeler <xref:System.Windows.Application.GetResourceStream%2A> la méthode de <xref:System.Windows.Application> la classe, en passant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] un à en-tête pack qui identifie le fichier de ressources souhaité. <xref:System.Windows.Application.GetResourceStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de ressources <xref:System.IO.Stream> en tant que et décrit son type de contenu.  
  
 Par exemple, le code <xref:System.Windows.Application.GetResourceStream%2A> suivant montre comment utiliser pour charger un <xref:System.Windows.Controls.Page> fichier de ressources et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Lorsque vous <xref:System.Windows.Application.GetResourceStream%2A> appelez vous donne accès <xref:System.IO.Stream>au, vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir. Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous pouvez vous permettre d’ouvrir et <xref:System.IO.Stream> de convertir en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Fichiers de code d’application en tant que fichiers de ressources  
 Un ensemble spécial de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fichiers de code d’application peut être référencé à [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]l’aide de Pack, y compris les fenêtres, les pages, les documents de Flow et les dictionnaires de ressources. Par exemple, vous pouvez définir la <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> propriété avec un à [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] en-tête pack qui référence la fenêtre ou la page que vous souhaitez charger au démarrage d’une application.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Vous pouvez le faire lorsqu’un fichier XAML est inclus dans un projet MSBuild en tant `Page` qu’élément.  
  
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
> Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous ajoutez un nouveau <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> `Page` `Build Action` ,,, ou <xref:System.Windows.ResourceDictionary> à un projet; par défaut, pour le fichier de balisage. <xref:System.Windows.Documents.FlowDocument>  
  
 Lorsqu’un projet avec `Page` des éléments est compilé, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les éléments sont convertis au format binaire et compilés dans l’assembly associé. Ainsi, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources classiques.  
  
> [!NOTE]
> Si un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est configuré `Resource` en tant qu’élément et n’a pas de fichier code-behind, le brut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilé dans un assembly plutôt que dans une version binaire du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]brut.  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Fichiers de contenu  
 Un *fichier de contenu* est distribué en tant que fichier libre avec un assembly exécutable. Bien qu’ils ne soient pas compilés en un assembly, les assemblys sont compilés à l’aide de métadonnées qui établissent une association avec chaque fichier de contenu.  
  
 Vous devez utiliser des fichiers de contenu quand votre application nécessite un ensemble spécifique de fichiers de données d’application, que vous souhaitez pouvoir mettre à jour sans recompiler l’assembly qui les consomme.  
  
### <a name="configuring-content-files"></a>Configuration des fichiers de contenu  
 Pour ajouter un fichier de contenu à un projet, un fichier de données d’application doit être `Content` inclus en tant qu’élément. En outre, étant donné qu’un fichier de contenu n’est pas compilé directement dans l’assembly, `CopyToOutputDirectory` vous devez définir l’élément de métadonnées MSBuild pour spécifier que le fichier de contenu est copié vers un emplacement relatif à l’assembly généré. Si vous souhaitez que la ressource soit copiée dans le dossier de sortie de génération chaque fois qu’un projet est généré `CopyToOutputDirectory` , vous définissez l' `Always` élément de métadonnées avec la valeur. Dans le cas contraire, vous pouvez vous assurer que seule la version la plus récente de la ressource est copiée dans `PreserveNewest` le dossier de sortie de la génération à l’aide de la valeur.  
  
 L’exemple ci-dessous illustre un fichier configuré en tant que fichier de contenu copié dans le dossier de sortie de build uniquement quand une nouvelle version de la ressource est ajoutée au projet.  
  
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
> Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier de contenu en ajoutant un fichier à un projet et en `Build Action` affectant à `Content`la valeur `Copy to Output Directory` `Always`, `Copy always` et en définissant sa `Copy if newer` valeur sur ( `PreserveNewest`identique à) et (identique à).  
  
 Lorsque le projet est généré, un <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est compilé dans les métadonnées de l’assembly pour chaque fichier de contenu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 La valeur de <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implique le chemin d’accès au fichier de contenu par rapport à sa position dans le projet. Par exemple, si un fichier de contenu se trouve dans un sous-dossier de projet, les informations supplémentaires relatives au chemin <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> d’accès sont incorporées dans la valeur.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 La <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur est également la valeur du chemin d’accès au fichier de contenu dans le dossier de sortie de la génération.  
  
### <a name="using-content-files"></a>Utilisation des fichiers de contenu  
 Pour charger un fichier de contenu, vous pouvez appeler <xref:System.Windows.Application.GetContentStream%2A> la méthode de <xref:System.Windows.Application> la classe, en passant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] un à en-tête pack qui identifie le fichier de contenu souhaité. <xref:System.Windows.Application.GetContentStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de contenu <xref:System.IO.Stream> en tant que et décrit son type de contenu.  
  
 Par exemple, le code <xref:System.Windows.Application.GetContentStream%2A> suivant montre comment utiliser pour charger un <xref:System.Windows.Controls.Page> fichier de contenu et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Lorsque vous <xref:System.Windows.Application.GetContentStream%2A> appelez vous donne accès <xref:System.IO.Stream>au, vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir. Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous pouvez vous permettre d’ouvrir et <xref:System.IO.Stream> de convertir en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Fichiers du site d’origine  
 Les fichiers de ressources ont une relation explicite avec les assemblys avec lesquels ils sont distribués, comme défini <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>par le. Toutefois, vous pouvez être amené à établir une relation implicite ou inexistante entre un assembly et un fichier de données d’application, notamment dans les situations suivantes :  
  
- Un fichier n’existe pas au moment de la compilation.  
  
- Vous ignorez de quels fichiers votre assembly a besoin jusqu’au moment de l’exécution.  
  
- Vous souhaitez pouvoir mettre à jour des fichiers sans recompiler l’assembly auquel ils sont associés.  
  
- Votre application utilise des fichiers de données volumineux, par exemple des fichiers audio et vidéo, et vous souhaitez que les utilisateurs aient le choix de les télécharger ou non.  
  
 Il est possible de charger ces types de fichiers à l’aide [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de schémas traditionnels, tels que les schémas file:///et http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Toutefois, pour les schémas file:/// et http:// votre application doit bénéficier d’une confiance totale. Si votre application est un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] qui a été lancé à partir d’Internet ou de l’intranet et qu’elle demande uniquement le jeu d’autorisations autorisé pour les applications lancées à partir de ces emplacements, les fichiers libres peuvent uniquement être chargés à partir du site d’origine de l’application ( emplacement de lancement). Ces fichiers sont appelés fichiers *de site d’origine* .  
  
 Les fichiers du site d’origine sont la seule option pour les applications partiellement fiables. Toutefois, ils ne se limitent pas à ces applications. Les applications entièrement fiables peuvent tout de même avoir besoin de charger des fichiers de données d’application dont ils n’ont pas connaissance au moment de la génération. Bien que les applications entièrement fiables puissent utiliser file:///, les fichiers de données d’application sont probablement installés dans le même dossier ou sous-dossier que l’assembly d’application. Dans ce cas, l’utilisation du référencement du site d’origine est plus facile que l’utilisation de file:///, car avec file:/// vous devez résoudre le chemin complet du fichier.  
  
> [!NOTE]
> Les fichiers de site d’origine ne sont pas mis [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] en cache avec un sur un ordinateur client, alors que les fichiers de contenu sont. Ils sont donc téléchargés à la demande. Si une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] application possède des fichiers multimédias volumineux, leur configuration en tant que fichiers de site d’origine signifie que le lancement de l’application initiale est beaucoup plus rapide et que les fichiers sont téléchargés uniquement à la demande.  
  
### <a name="configuring-site-of-origin-files"></a>Configuration des fichiers du site d’origine  
 Si vos fichiers de site d’origine sont inexistants ou inconnus au moment de la compilation, vous devez utiliser des mécanismes de déploiement traditionnels pour vous assurer que les fichiers requis sont disponibles `XCopy` au moment de l’exécution, y compris en utilisant le programme de ligne de commande ou le [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Si vous savez au moment de la compilation les fichiers que vous souhaitez placer sur le site d’origine, mais que vous souhaitez toujours éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un projet MSBuild en tant `None` qu’élément. Comme pour les fichiers de contenu, vous devez définir l' `CopyToOutputDirectory` attribut MSBuild pour spécifier que le fichier du site d’origine est copié vers un emplacement relatif à l’assembly généré, en spécifiant `Always` la valeur ou `PreserveNewest` la valeur.  
  
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
> Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier de site d’origine en ajoutant un fichier à un projet et en `Build Action` affectant à `None`la valeur.  
  
 Lorsque le projet est généré, MSBuild copie les fichiers spécifiés dans le dossier de sortie de la génération.  
  
### <a name="using-site-of-origin-files"></a>Utilisation des fichiers du site d’origine  
 Pour charger un fichier de site d’origine, vous pouvez appeler <xref:System.Windows.Application.GetRemoteStream%2A> la méthode de <xref:System.Windows.Application> la classe, en passant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] un à en-tête pack qui identifie le fichier de site d’origine souhaité. <xref:System.Windows.Application.GetRemoteStream%2A>retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet qui expose le fichier de site d’origine <xref:System.IO.Stream> en tant que et décrit son type de contenu.  
  
 Par exemple, le code <xref:System.Windows.Application.GetRemoteStream%2A> suivant montre comment utiliser pour charger un <xref:System.Windows.Controls.Page> fichier de site d’origine et le définir en tant que contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Lorsque vous <xref:System.Windows.Application.GetRemoteStream%2A> appelez vous donne accès <xref:System.IO.Stream>au, vous devez effectuer le travail supplémentaire de la conversion en type de la propriété avec laquelle vous allez le définir. Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vous pouvez vous permettre d’ouvrir et <xref:System.IO.Stream> de convertir en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide du code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Regénération après changement du type de build  
 Après avoir changé le type de build d’un fichier de données d’application, vous devez regénérer l’application entière pour vérifier que ces changements sont bien appliqués. Si vous générez uniquement l’application, les changements ne sont pas appliqués.  
  
## <a name="see-also"></a>Voir aussi

- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
