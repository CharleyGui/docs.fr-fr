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
# <a name="packaging-fonts-with-applications"></a>Empaquetage de polices avec des applications
Cette rubrique fournit une vue d’ensemble de l’empaquetage des polices avec votre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.  
  
> [!NOTE]
> Comme avec la plupart des types de logiciels, les fichiers de police sont sous licence et ne sont pas vendus. Les licences qui régissent l’utilisation des polices varient d’un fournisseur à l’autre, mais en général, la plupart des licences, y compris celles qui couvrent les polices fournies par Microsoft avec les applications et Windows, ne permettent pas d’incorporer les polices dans des applications ou de les redistribuer autrement. Par conséquent, en tant que développeur, c’est à vous de vérifier que vous disposez des droits de licence nécessaires pour toute police incorporée dans une application ou redistribuée.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Présentation de l’empaquetage de polices  
 Vous pouvez facilement empaqueter des polices en tant que ressources dans vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications pour afficher le texte de l’interface utilisateur et d’autres types de contenu textuel. Les polices peuvent être séparées des fichiers d’assembly de l’application ou y être incorporées. Vous pouvez également créer une bibliothèque de polices de ressources uniquement, que votre application peut référencer.  
  
 Les polices OpenType et TrueType® contiennent un indicateur de type, fsType, qui indique les droits de licence d’incorporation de polices pour la police. Toutefois, cet indicateur de type concerne uniquement les polices incorporées stockées dans un document. Il ne concerne pas les polices incorporées dans une application. Vous pouvez récupérer les droits d’incorporation de police pour une police en créant un <xref:System.Windows.Media.GlyphTypeface> objet et en référençant sa <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> propriété. Pour plus d’informations sur l’indicateur fsType, reportez-vous à la section « OS/2 et métriques Windows » de la [spécification OpenType](https://www.microsoft.com/typography/otspec/os2.htm) .  
  
 Le site Web [Microsoft Typography](https://docs.microsoft.com/typography/) comprend des informations de contact qui peuvent vous aider à localiser un fournisseur de polices particulier ou à rechercher un fournisseur de polices pour un travail personnalisé.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>Ajout de polices comme éléments de contenu  
 Vous pouvez ajouter des polices à votre application sous forme d’éléments de contenu de projet séparés des fichiers d’assembly de l’application. Cela signifie que les éléments de contenu ne sont pas incorporés sous forme de ressources dans un assembly. L’exemple de fichier projet suivant montre comment définir des éléments de contenu.  
  
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
  
 Pour vérifier que l’application peut utiliser les polices au moment de l’exécution, ces dernières doivent être accessibles dans le répertoire de déploiement de l’application. L' `<CopyToOutputDirectory>` élément dans le fichier projet de l’application vous permet de copier automatiquement les polices dans le répertoire de déploiement de l’application pendant le processus de génération. L’exemple de fichier projet suivant montre comment copier les polices dans le répertoire de déploiement.  
  
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
  
 L’exemple de code suivant montre comment référencer la police de l’application comme élément de contenu. L’élément de contenu référencé doit être dans le même répertoire que les fichiers d’assembly de l’application.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>Ajout de polices comme éléments de ressource  
 Vous pouvez ajouter des polices à votre application sous forme d’éléments de ressource de projet incorporés dans les fichiers d’assembly de l’application. L’utilisation d’un sous-répertoire distinct pour les ressources permet d’organiser les fichiers projet de l’application. L’exemple de fichier projet suivant montre comment définir des polices comme éléments de ressource dans un sous-répertoire distinct.  
  
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
> Quand vous ajoutez des polices en tant que ressources à votre application, assurez-vous que vous définissez l' `<Resource>` élément, et non l' `<EmbeddedResource>` élément dans le fichier projet de votre application. L' `<EmbeddedResource>` élément pour l’action de génération n’est pas pris en charge.  
  
 L’exemple de balisage suivant indique comment référencer les ressources de police de l’application.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Référencement d’éléments de ressource de police à partir du code  
 Pour référencer des éléments de ressource de police à partir du code, vous devez fournir une référence de ressource de police en deux parties : l’URI (Uniform Resource Identifier) de base ; et la référence d’emplacement de la police. Ces valeurs sont utilisées comme paramètres pour la <xref:System.Windows.Media.FontFamily.%23ctor%2A> méthode. L’exemple de code suivant montre comment référencer les ressources de police de l’application dans le sous-répertoire de projet appelé `resources` .  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 L’URI (Uniform Resource Identifier) de base peut inclure le sous-répertoire d’application où se trouve la ressource de police. Dans ce cas, la référence de l’emplacement de la police n’a pas besoin de spécifier un répertoire, mais doit inclure un «» de début `./` , ce qui indique que la ressource de police se trouve dans le même répertoire que celui spécifié par l’URI (Uniform Resource Identifier) de base. L’exemple de code suivant montre une autre façon de référencer l’élément de ressource de police. Il est équivalent à l’exemple de code précédent.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Référencement de polices à partir du même sous-répertoire d’application  
 Vous pouvez placer le contenu de l’application et les fichiers de ressources dans le même sous-répertoire défini par l’utilisateur de votre projet d’application. L’exemple de fichier projet suivant montre une page de contenu et des ressources de police définies dans le même sous-répertoire.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Comme le contenu de l’application et la police sont dans le même sous-répertoire, la référence de police est relative au contenu d’application. Les exemples suivants montrent comment référencer les ressources de police de l’application quand la police se trouve dans le même répertoire que l’application.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Énumération des polices dans une application  
 Pour énumérer les polices comme éléments de ressource dans votre application, utilisez <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> la <xref:System.Windows.Media.Fonts.GetTypefaces%2A> méthode ou. L’exemple suivant montre comment utiliser la <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> méthode pour retourner la collection d' <xref:System.Windows.Media.FontFamily> objets à partir de l’emplacement de la police de l’application. Dans cet exemple, l’application contient un sous-répertoire nommé « Resources ».  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 L’exemple suivant montre comment utiliser la <xref:System.Windows.Media.Fonts.GetTypefaces%2A> méthode pour retourner la collection d' <xref:System.Windows.Media.Typeface> objets à partir de l’emplacement de la police de l’application. Dans cet exemple, l’application contient un sous-répertoire nommé « Resources ».  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Création d’une bibliothèque de ressources de police  
 Vous pouvez créer une bibliothèque de ressources uniquement qui contient seulement des polices, aucun code ne fait partie de ce type de projet de bibliothèque. La création d’une bibliothèque de ressources uniquement est une technique courante pour découpler les ressources du code d’application qui les utilise. Cela permet également d’inclure l’assembly de bibliothèque dans plusieurs projets d’application. L’exemple de fichier projet suivant montre les parties clés d’un projet de bibliothèque de ressources uniquement.  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>Référencement d’une police dans une bibliothèque de ressources  
 Pour référencer une police dans une bibliothèque de ressources à partir de votre application, vous devez faire précéder la référence de police du nom de l’assembly de bibliothèque. Dans cet exemple, l’assembly de ressource de police est « FontLibrary ». Pour séparer le nom de l’assembly de la référence dans l’assembly, utilisez un caractère « ; ». L’ajout du mot clé « Component » suivi de la référence au nom de la police complète la référence aux ressources de la bibliothèque de polices. L’exemple de code suivant indique comment référencer une police dans un assembly de bibliothèque de ressources.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Ce kit de développement logiciel (SDK) contient un ensemble d’exemples de polices OpenType que vous pouvez utiliser avec les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications. Les polices sont définies dans une bibliothèque de ressources uniquement. Pour plus d’informations, consultez [exemple de Pack de polices OpenType](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Limitations de l’utilisation des polices  
 La liste suivante décrit plusieurs limitations sur l’empaquetage et l’utilisation des polices dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications :  
  
- **Bits d’autorisation d’incorporation de police : Les applications ** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne vérifient ni n’appliquent les bits d’autorisation d’incorporation de police. Pour plus d’informations, consultez la section [polices Introduction_to_Packing](#introduction_to_packaging_fonts) .  
  
- **Polices du site d’origine :** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications n’autorisent pas de référence de police à un URI (Uniform Resource Identifier) http ou FTP.  
  
- **URI absolu utilisant la notation** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pack : les applications ne vous permettent pas de créer un <xref:System.Windows.Media.FontFamily> objet par programmation en utilisant "Pack :" dans le cadre de la référence URI (Uniform Resource Identifier) absolue à une police. Par exemple, `"pack://application:,,,/resources/#Pericles Light"` est une référence de police non valide.  
  
- **Incorporation de police automatique :** Au moment de la conception, il n’est pas possible de rechercher les polices utilisées par une application et de les incorporer automatiquement dans les ressources de l’application.  
  
- **Sous-ensembles de polices : Les applications ** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prennent pas en charge la création de sous-ensembles de polices pour les documents non fixes.  
  
- En cas de référence incorrecte, l’application utilise une police disponible à la place.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/) (Typographie Microsoft : Liens, actualité et contacts)
- [OpenType Specification](https://www.microsoft.com/typography/otspec/) (Spécification OpenType)
- [Fonctionnalités des polices OpenType](opentype-font-features.md)
- [Exemple de pack de polices OpenType](sample-opentype-font-pack.md)
