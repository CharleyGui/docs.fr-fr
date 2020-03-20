---
title: Ressources d’application, contenu et fichiers de données
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186199"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Fichiers de ressources, de contenu et de données d'une application WPF
Les applications Microsoft Windows dépendent souvent de fichiers qui [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]contiennent des données non exécutables, telles que , images, vidéo et audio. Windows Presentation Foundation (WPF) offre une assistance spéciale pour configurer, identifier et utiliser ces types de fichiers de données, qui sont appelés fichiers de données d’application. Cette prise en charge repose sur un ensemble spécifique de types de fichier de données d’application, notamment :  
  
- **Fichiers de ressources**: Fichiers de données qui sont compilés dans un assemblage exécutable ou de bibliothèque WPF.  
  
- **Fichiers de contenu**: Fichiers de données autonomes qui ont une association explicite avec un assemblage WPF exécutable.  
  
- **Site des fichiers d’origine**: Fichiers de données autonomes qui n’ont aucune association avec un assemblage WPF exécutable.  
  
 Il existe une distinction importante entre ces trois types de fichier : les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération. En effet, un assembly les connaît explicitement. Pour les dossiers de site d’origine, cependant, une assemblée peut n’avoir aucune connaissance de ces dossiers, ou des connaissances implicites grâce à une référence d’identification de ressources uniformes de meute (URI); le cas de ce dernier, il n’y a aucune garantie que le fichier du site d’origine référencé existe réellement.  
  
 Pour référencer les fichiers de données d’application, Windows Presentation Foundation (WPF) utilise le pack uniforme d’identification des ressources (URI), qui est décrit en détail dans [Pack URIs dans WPF](pack-uris-in-wpf.md)).  
  
 Cette rubrique décrit comment configurer et utiliser des fichiers de données d’application.  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>Fichiers de ressources  
 Si un fichier de données d’application doit toujours être disponible pour une application, le seul moyen de garantir cette disponibilité est de le compiler en un assembly exécutable principal d’une application ou en l’un de ses assemblys référencés. Ce type de fichier de données d’application est connu sous le nom *de fichier de ressources*.  
  
 Vous devez utiliser des fichiers de ressources dans les situations suivantes :  
  
- Vous n’avez pas besoin de mettre à jour le contenu du fichier de ressources une fois qu’il a été compilé en un assembly.  
  
- Vous souhaitez simplifier la complexité de distribution d’une application en réduisant le nombre des dépendances de fichiers.  
  
- Votre fichier de données d’application doit être localisable (voir [WPF Globalisation and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Les dossiers de ressources décrits dans cette section sont différents des dossiers de ressources décrits dans [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) et des ressources intégrées ou liées décrites dans [Manage Application Resources (.NET).](/visualstudio/ide/managing-application-resources-dotnet)  
  
### <a name="configuring-resource-files"></a>Configuration des fichiers de ressources  
 Dans WPF, un fichier de ressources est un fichier qui est inclus dans `Resource` un projet de moteur de construction Microsoft (MSBuild) comme élément.  
  
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
> Dans Visual Studio, vous créez un fichier de ressources `Build Action` en `Resource`ajoutant un fichier à un projet et en le fixant à .  
  
 Lorsque le projet est construit, MSBuild compile la ressource dans l’assemblage.  
  
### <a name="using-resource-files"></a>Utilisation des fichiers de ressources  
 Pour charger un fichier de <xref:System.Windows.Application.GetResourceStream%2A> ressources, <xref:System.Windows.Application> vous pouvez appeler la méthode de la classe, en passant un pack URI qui identifie le fichier de ressources souhaité. <xref:System.Windows.Application.GetResourceStream%2A>retourne <xref:System.Windows.Resources.StreamResourceInfo> un objet, qui expose le <xref:System.IO.Stream> fichier de ressources comme un et décrit son type de contenu.  
  
 À titre d’exemple, le <xref:System.Windows.Application.GetResourceStream%2A> code suivant <xref:System.Windows.Controls.Page> montre comment utiliser pour charger <xref:System.Windows.Controls.Frame> `pageFrame`un fichier de ressources et le définir comme le contenu d’un (  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Tout <xref:System.Windows.Application.GetResourceStream%2A> en appelant vous <xref:System.IO.Stream>donne accès à la , vous devez effectuer le travail supplémentaire de le convertir au type de la propriété que vous allez le définir avec. Au lieu de cela, vous pouvez laisser <xref:System.IO.Stream> WPF prendre soin d’ouvrir et de convertir le en chargeant un fichier de ressources directement dans la propriété d’un type en utilisant le code.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Page> comment charger <xref:System.Windows.Controls.Frame> `pageFrame`un directement dans un ( ) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Fichiers de code d’application en tant que fichiers de ressources  
 Un ensemble spécial de fichiers de code d’application WPF peut être référencé à l’aide d’ITI pack, y compris les fenêtres, les pages, les documents de flux et les dictionnaires de ressources. Par exemple, vous <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> pouvez définir la propriété avec un pack URI qui fait référence à la fenêtre ou à la page que vous souhaitez charger lorsque une application démarre.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Vous pouvez le faire lorsqu’un fichier XAML est inclus `Page` dans un projet MSBuild comme élément.  
  
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
> Dans Visual Studio, vous <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>ajoutez <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>un <xref:System.Windows.ResourceDictionary> nouveau , , `Build Action` , ou à un `Page`projet, le fichier de balisage sera par défaut à .  
  
 Lorsqu’un `Page` projet avec des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments est compilé, les éléments sont convertis en format binaire et compilés dans l’assemblage associé. Ainsi, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources classiques.  
  
> [!NOTE]
> Si [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] un fichier est `Resource` configuré comme un élément, et n’a pas de fichier de code-derrière, le brut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilé dans un assemblage plutôt que d’une version binaire de la crue [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>Fichiers de contenu  
 Un *fichier de contenu* est distribué sous forme de fichier lâche à côté d’un assemblage exécutable. Bien qu’ils ne soient pas compilés en un assembly, les assemblys sont compilés à l’aide de métadonnées qui établissent une association avec chaque fichier de contenu.  
  
 Vous devez utiliser des fichiers de contenu quand votre application nécessite un ensemble spécifique de fichiers de données d’application, que vous souhaitez pouvoir mettre à jour sans recompiler l’assembly qui les consomme.  
  
### <a name="configuring-content-files"></a>Configuration des fichiers de contenu  
 Pour ajouter un fichier de contenu à un projet, `Content` un fichier de données d’application doit être inclus comme élément. En outre, comme un fichier de contenu n’est pas compilé `CopyToOutputDirectory` directement dans l’assemblage, vous devez définir l’élément métadonnées MSBuild pour spécifier que le fichier de contenu est copié à un endroit qui est relatif à l’assemblage construit. Si vous voulez que la ressource soit copiée sur le dossier de `CopyToOutputDirectory` sortie de construction `Always` chaque fois qu’un projet est construit, vous définissez l’élément métadonnée avec la valeur. Sinon, vous pouvez vous assurer que seule la version la plus récente de `PreserveNewest` la ressource est copiée sur le dossier de sortie de construction en utilisant la valeur.  
  
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
> Dans Visual Studio, vous créez un fichier de contenu `Build Action` en `Content`ajoutant un `Copy to Output Directory` `Copy always` fichier à `Always`un `Copy if newer` projet `PreserveNewest`et en le définissant, et le définissez (même que ) et (même que ).  
  
 Lorsque le projet est <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> construit, un attribut est compilé dans les métadonnées de l’assemblage pour chaque fichier de contenu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 La valeur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> de la implique le chemin vers le fichier de contenu par rapport à sa position dans le projet. Par exemple, si un fichier de contenu était situé dans un sous-pliage de projet, les renseignements supplémentaires sur le chemin seraient incorporés dans la <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 La <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur est également la valeur du chemin vers le fichier de contenu dans le dossier de sortie de construction.  
  
### <a name="using-content-files"></a>Utilisation des fichiers de contenu  
 Pour charger un fichier de <xref:System.Windows.Application.GetContentStream%2A> contenu, <xref:System.Windows.Application> vous pouvez appeler la méthode de la classe, en passant un pack URI qui identifie le fichier de contenu souhaité. <xref:System.Windows.Application.GetContentStream%2A>retourne <xref:System.Windows.Resources.StreamResourceInfo> un objet, qui expose le <xref:System.IO.Stream> fichier de contenu comme un et décrit son type de contenu.  
  
 À titre d’exemple, le <xref:System.Windows.Application.GetContentStream%2A> code suivant <xref:System.Windows.Controls.Page> montre comment utiliser pour charger <xref:System.Windows.Controls.Frame> `pageFrame`un fichier de contenu et le définir comme le contenu d’un ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Tout <xref:System.Windows.Application.GetContentStream%2A> en appelant vous <xref:System.IO.Stream>donne accès à la , vous devez effectuer le travail supplémentaire de le convertir au type de la propriété que vous allez le définir avec. Au lieu de cela, vous pouvez laisser <xref:System.IO.Stream> WPF prendre soin d’ouvrir et de convertir le en chargeant un fichier de ressources directement dans la propriété d’un type en utilisant le code.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Page> comment charger <xref:System.Windows.Controls.Frame> `pageFrame`un directement dans un ( ) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>Fichiers du site d’origine  
 Les fichiers de ressources ont une relation explicite avec les assemblées qu’ils sont distribués à côté, tel que défini par le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Toutefois, vous pouvez être amené à établir une relation implicite ou inexistante entre un assembly et un fichier de données d’application, notamment dans les situations suivantes :  
  
- Un fichier n’existe pas au moment de la compilation.  
  
- Vous ignorez de quels fichiers votre assembly a besoin jusqu’au moment de l’exécution.  
  
- Vous souhaitez pouvoir mettre à jour des fichiers sans recompiler l’assembly auquel ils sont associés.  
  
- Votre application utilise des fichiers de données volumineux, par exemple des fichiers audio et vidéo, et vous souhaitez que les utilisateurs aient le choix de les télécharger ou non.  
  
 Il est possible de charger ces types de fichiers en utilisant des systèmes d’URI traditionnels, tels que les systèmes de file:/// et de http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Toutefois, pour les schémas file:/// et http:// votre application doit bénéficier d’une confiance totale. Si votre application est une application de navigateur XAML (XBAP) qui a été lancée à partir d’Internet ou intranet, et qu’elle ne demande que l’ensemble des autorisations qui sont autorisées pour les applications lancées à partir de ces emplacements, les fichiers en vrac ne peuvent être chargés à partir de la site d’origine de l’application (emplacement de lancement). Ces fichiers sont connus sous le nom de fichiers *de site d’origine.*  
  
 Les fichiers du site d’origine sont la seule option pour les applications partiellement fiables. Toutefois, ils ne se limitent pas à ces applications. Les applications entièrement fiables peuvent tout de même avoir besoin de charger des fichiers de données d’application dont ils n’ont pas connaissance au moment de la génération. Bien que les applications entièrement fiables puissent utiliser file:///, les fichiers de données d’application sont probablement installés dans le même dossier ou sous-dossier que l’assembly d’application. Dans ce cas, l’utilisation du référencement du site d’origine est plus facile que l’utilisation de file:///, car avec file:/// vous devez résoudre le chemin complet du fichier.  
  
> [!NOTE]
> Les fichiers du site d’origine ne sont pas mis en cache avec une application de navigateur XAML (XBAP) sur une machine cliente, tandis que les fichiers de contenu le sont. Ils sont donc téléchargés à la demande. Si une application de navigateur XAML (XBAP) application a de grands fichiers multimédias, les configurer comme des fichiers de site d’origine signifie que le lancement initial de l’application est beaucoup plus rapide, et les fichiers ne sont téléchargés sur demande.  
  
### <a name="configuring-site-of-origin-files"></a>Configuration des fichiers du site d’origine  
 Si vos fichiers de site d’origine sont inexistants ou inconnus au moment de la compilation, vous devez utiliser `XCopy` des mécanismes de déploiement traditionnels pour vous assurer que les fichiers requis sont disponibles au moment de l’exécution, y compris en utilisant le programme de ligne de commande ou l’installateur Windows Microsoft.  
  
 Si vous connaissez au moment de la compilation les fichiers que vous souhaitez être situé sur le site d’origine, mais que vous `None` voulez toujours éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un projet MSBuild comme élément. Comme pour les fichiers de contenu, vous `CopyToOutputDirectory` devez définir l’attribut MSBuild pour spécifier que le fichier du `Always` site `PreserveNewest` d’origine est copié à un endroit relatif à l’assemblage construit, en spécifiant soit la valeur ou la valeur.  
  
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
> Dans Visual Studio, vous créez un fichier de site d’origine en ajoutant un fichier à un projet et en le fixant `Build Action` à `None`.  
  
 Lorsque le projet est construit, MSBuild copie les fichiers spécifiés au dossier de sortie de construction.  
  
### <a name="using-site-of-origin-files"></a>Utilisation des fichiers du site d’origine  
 Pour charger un fichier de site <xref:System.Windows.Application.GetRemoteStream%2A> d’origine, vous pouvez appeler la méthode de la <xref:System.Windows.Application> classe, en passant un pack URI qui identifie le fichier de site d’origine souhaité. <xref:System.Windows.Application.GetRemoteStream%2A>retourne <xref:System.Windows.Resources.StreamResourceInfo> un objet, qui expose le fichier <xref:System.IO.Stream> du site d’origine comme un et décrit son type de contenu.  
  
 À titre d’exemple, le <xref:System.Windows.Application.GetRemoteStream%2A> code suivant <xref:System.Windows.Controls.Page> montre comment utiliser pour charger un <xref:System.Windows.Controls.Frame> `pageFrame`fichier de site d’origine et le définir comme le contenu d’un ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Tout <xref:System.Windows.Application.GetRemoteStream%2A> en appelant vous <xref:System.IO.Stream>donne accès à la , vous devez effectuer le travail supplémentaire de le convertir au type de la propriété que vous allez le définir avec. Au lieu de cela, vous pouvez laisser <xref:System.IO.Stream> WPF prendre soin d’ouvrir et de convertir le en chargeant un fichier de ressources directement dans la propriété d’un type en utilisant le code.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Page> comment charger <xref:System.Windows.Controls.Frame> `pageFrame`un directement dans un ( ) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>Regénération après changement du type de build  
 Après avoir changé le type de build d’un fichier de données d’application, vous devez regénérer l’application entière pour vérifier que ces changements sont bien appliqués. Si vous générez uniquement l’application, les changements ne sont pas appliqués.  
  
## <a name="see-also"></a>Voir aussi

- [URI à en-tête pack dans WPF](pack-uris-in-wpf.md)
