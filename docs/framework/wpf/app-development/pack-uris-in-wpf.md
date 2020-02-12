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
ms.openlocfilehash: a98c97a4aa95fb956a2ca6d417e009a281a938b6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124479"
---
# <a name="pack-uris-in-wpf"></a>URI à en-tête pack dans WPF

Dans Windows Presentation Foundation (WPF), les URI (Uniform Resource Identifiers) sont utilisés pour identifier et charger les fichiers de plusieurs façons, y compris les éléments suivants :

- Spécification de l' [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à afficher lorsqu’une application démarre pour la première fois.

- En chargeant des images

- En naviguant vers des pages

- En chargeant des fichiers de données non exécutables

En outre, les URI peuvent être utilisés pour identifier et charger des fichiers à partir de différents emplacements, y compris les éléments suivants :

- L’assembly actuel

- Un assembly référencé

- Un emplacement relatif à un assembly

- Le site d’origine de l’application

Pour fournir un mécanisme cohérent pour identifier et charger ces types de fichiers à partir de ces emplacements, WPF tire parti de l’extensibilité du schéma d’URI à en- *tête pack*. Cette rubrique fournit une vue d’ensemble du schéma, explique comment construire des URI à en-tête pack pour divers scénarios, traite des URI absolus et relatifs et la résolution d’URI, avant d’illustrer l’utilisation des URI à en-tête pack à partir du balisage et du code.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schéma URI à en-tête pack

Le schéma d’URI à en-tête pack est utilisé par la spécification [Open Packaging Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) (OPC), qui décrit un modèle d’organisation et d’identification du contenu. Les éléments clés de ce modèle sont des packages et des parties, où un *package* est un conteneur logique pour une ou plusieurs *parties*logiques. La figure suivante illustre ce concept.

![Diagramme Package et pièces](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Pour identifier les parties, la spécification OPC tire parti de l’extensibilité de la norme RFC 2396 (Uniform Resource Identifiers (URI) : syntaxe générique) pour définir le modèle d’URI à en-tête pack.

Le schéma spécifié par un URI est défini par son préfixe ; http, FTP et file sont des exemples connus. Le modèle d’URI à en-tête pack utilise « Pack » comme modèle et contient deux composants : autorité et chemin d’accès. Voici le format d’un URI à en-tête pack.

*chemin d’accès*/de l'*autorité* Pack://

L' *autorité* spécifie le type de package qui contient un composant, tandis que le *chemin d’accès* spécifie l’emplacement d’une partie au sein d’un package.

Ce concept est illustré par le figure suivante :

![Relation entre package, autorité et chemin d'accès](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Les packages et les parties s’apparentent à des applications et des fichiers, où une application (package) peut inclure un ou plusieurs fichiers (parties), notamment :

- Des fichiers de ressources compilés dans l’assembly local

- Des fichiers de ressources compilés dans un assembly référencé

- Des fichiers de ressources compilés dans un assembly de référence

- Des fichiers de contenu

- Des fichiers de site d’origine

Pour accéder à ces types de fichiers, WPF prend en charge deux autorités : application:///et siteoforigin:///. L’autorité application:/// identifie les fichiers de données d’application qui sont connus au moment de la compilation, notamment les fichiers de ressources et de contenu. L’autorité siteoforigin:/// identifie les fichiers de site d’origine. La portée de chaque autorité est indiquée dans la figure suivante.

![Diagramme URI à en-tête pack](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Le composant d’autorité d’un URI à en-tête pack est un URI incorporé qui pointe vers un package et doit être conforme à la norme RFC 2396. De plus, le caractère « / » doit être remplacé par le caractère « , » et les caractères réservés tels que « % » et « ? » doivent être échappés. Pour plus d’informations, consultez l’OPC.

Les sections suivantes expliquent comment construire des URI à en-tête pack à l’aide de ces deux autorités conjointement avec les chemins d’accès appropriés pour identifier les fichiers de ressources, de contenu et de site d’origine.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>URI à en-tête pack de fichier de ressources

Les fichiers de ressources sont configurés en tant qu’éléments `Resource` MSBuild et sont compilés dans des assemblys. WPF prend en charge la construction d’URI à en-tête pack qui peuvent être utilisés pour identifier des fichiers de ressources qui sont compilés dans l’assembly local ou compilés dans un assembly qui est référencé à partir de l’assembly local.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Fichier de ressources d’assembly local

L’URI à en-tête pack pour un fichier de ressources compilé dans l’assembly local utilise l’autorité et le chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly local.

L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve à la racine du dossier du projet de l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous-dossier du dossier du projet de l’assembly local.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Fichier de ressources d’assembly référencé

L’URI à en-tête pack pour un fichier de ressources compilé dans un assembly référencé utilise l’autorité et le chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin** : nom d’un fichier de ressources compilé dans un assembly référencé. Le chemin doit respecter le format suivant :

  *NomCourtAssembly*{ *; Version*] { *; PublicKey*]; composant/*chemin d’accès*

  - **NomCourtAssembly** : nom court de l’assembly référencé.

  - **;Version** [facultatif] : version de l’assembly référencé qui contient le fichier de ressources. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;CléPublique** [facultatif] : clé publique utilisée pour signer l’assembly référencé. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;component** : indique que l’assembly désigné est référencé à partir de l’assembly local.

  - **/Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly référencé.

L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve à la racine du dossier du projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous-dossier du dossier du projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

L’exemple suivant montre l’URI à en-tête pack pour un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans le dossier racine d’un dossier de projet d’assembly spécifique à la version référencé.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Notez que la syntaxe d’URI à en-tête pack pour les fichiers de ressources d’assembly référencés peut être utilisée uniquement avec l’autorité application:///. Par exemple, le code suivant n’est pas pris en charge dans WPF.

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>URI à en-tête pack de fichier de contenu

L’URI à en-tête pack pour un fichier de contenu utilise l’autorité et le chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin** : nom du fichier de contenu, y compris son chemin relatif à l’emplacement, dans le système de fichiers, de l’assembly exécutable principal de l’application.

L’exemple suivant montre l’URI à en-tête pack pour un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], situé dans le même dossier que l’assembly exécutable.

`pack://application:,,,/ContentFile.xaml`

L’exemple suivant montre l’URI à en-tête pack pour un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], situé dans un sous-dossier relatif à l’assembly exécutable de l’application.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Impossible d’accéder aux fichiers de contenu HTML. Le modèle d’URI prend uniquement en charge la navigation vers les fichiers HTML qui se trouvent sur le site d’origine.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>URI à en-tête pack de site d’origine

L’URI à en-tête pack pour un fichier de site d’origine utilise l’autorité et le chemin d’accès suivants :

- **Autorité** : siteoforigin:///.

- **Chemin** : nom du fichier de site d’origine, y compris son chemin relatif à l’emplacement à partir duquel l’assembly exécutable a été lancé.

L’exemple suivant montre l’URI à en-tête pack pour un fichier de site d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stocké à l’emplacement à partir duquel l’assembly exécutable est lancé.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

L’exemple suivant montre l’URI à en-tête pack pour un fichier de site d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stocké dans un sous-dossier relatif à l’emplacement à partir duquel l’assembly exécutable de l’application est lancé.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Fichiers d’échange

Les fichiers XAML qui sont configurés en tant qu’éléments `Page` MSBuild sont compilés dans des assemblys de la même façon que les fichiers de ressources. Par conséquent, les éléments de `Page` MSBuild peuvent être identifiés à l’aide d’URI à en-tête pack pour les fichiers de ressources.

Les types de fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] couramment configurés en tant qu’éléments de`Page` MSBuild ont l’un des éléments suivants comme élément racine :

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>URI à en-tête pack absolus et relatifs

Un URI à en-tête pack complet comprend le schéma, l’autorité et le chemin d’accès, et il est considéré comme un URI à en-tête pack absolu. En guise de simplification pour les développeurs, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments vous permettent généralement de définir des attributs appropriés avec un URI à en-tête pack relatif, qui comprend uniquement le chemin d’accès.

Par exemple, considérez l’URI à en-tête pack absolu suivant pour un fichier de ressources dans l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

L’URI à en-tête pack relatif qui fait référence à ce fichier de ressources est le suivant.

`/ResourceFile.xaml`

> [!NOTE]
> Étant donné que les fichiers de site d’origine ne sont pas associés à des assemblys, ils ne peuvent être référencés qu’avec des URI à en-tête pack absolus.

Par défaut, un URI à en-tête pack relatif est considéré comme relatif à l’emplacement du balisage ou du code qui contient la référence. Toutefois, si une barre oblique inverse de début est utilisée, la référence URI à en-tête pack relative est alors considérée comme relative à la racine de l’application. Par exemple, considérez la structure de projet suivante.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Si Page1. xaml contient un URI qui fait référence à la *racine*\SubFolder\Page2.xaml, la référence peut utiliser l’URI à en-tête pack relatif suivant.

`Page2.xaml`

Si Page1. xaml contient un URI qui fait référence à la *racine*\Page2.xaml, la référence peut utiliser l’URI à en-tête pack relatif suivant.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Résolution des URI à en-tête pack

Le format des URI à en-tête pack permet aux URI à en-tête pack pour les différents types de fichiers de se présenter de la même façon. Par exemple, considérez l’URI à en-tête pack absolu suivant.

`pack://application:,,,/ResourceOrContentFile.xaml`

Cet URI à en-tête pack absolu peut faire référence à un fichier de ressources dans l’assembly local ou à un fichier de contenu. Il en va de même pour l’URI relatif suivant.

`/ResourceOrContentFile.xaml`

Pour déterminer le type de fichier auquel un URI à en-tête pack fait référence, WPF résout les URI des fichiers de ressources dans les assemblys locaux et les fichiers de contenu à l’aide de l’heuristique suivante :

1. Sondez les métadonnées de l’assembly pour un attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> qui correspond à l’URI à en-tête pack.

2. Si l’attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est trouvé, le chemin d’accès de l’URI à en-tête pack fait référence à un fichier de contenu.

3. Si l’attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est introuvable, Sondez les fichiers de ressources définis qui sont compilés dans l’assembly local.

4. Si un fichier de ressources qui correspond au chemin d’accès de l’URI à en-tête pack est trouvé, le chemin d’accès de l’URI à en-tête pack fait référence à un fichier de ressources.

5. Si la ressource est introuvable, la <xref:System.Uri> créée en interne n’est pas valide.

La résolution d’URI ne s’applique pas aux URI qui font référence aux éléments suivants :

- Fichiers de contenu dans les assemblys référencés : ces types de fichiers ne sont pas pris en charge par WPF.

- Fichiers incorporés dans les assemblys référencés : les URI qui les identifient sont uniques, car ils incluent à la fois le nom de l’assembly référencé et le suffixe `;component`.

- Fichiers du site d’origine : les URI qui les identifient sont uniques car ce sont les seuls fichiers qui peuvent être identifiés par des URI à en-tête pack qui contiennent l’autorité siteoforigin:///.

Une simplification de la résolution des URI à en-tête pack permet au code d’être quelque peu indépendant des emplacements des fichiers de ressources et de contenu. Par exemple, si vous avez un fichier de ressources dans l’assembly local qui est reconfiguré pour être un fichier de contenu, l’URI à en-tête pack pour la ressource reste le même, tout comme le code qui utilise l’URI à en-tête pack.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programmation avec des URI à en-tête pack

De nombreuses classes WPF implémentent des propriétés qui peuvent être définies avec des URI à en-tête pack, notamment :

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Ces propriétés peuvent être définies à partir du balisage et du code. Cette section décrit les constructions de base pour les deux, et fournit des exemples de scénarios courants.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Utilisation d’URI à en-tête pack dans le balisage

Un URI à en-tête pack est spécifié dans le balisage en définissant l’élément d’un attribut avec l’URI à en-tête pack. Par exemple :

`<element attribute="pack://application:,,,/File.xaml" />`

Le tableau 1 illustre les différents URI à en-tête pack absolus que vous pouvez spécifier dans le balisage.

Tableau 1 : URI à en-tête pack absolus dans le balisage

|Fichier|URI à en-tête pack absolu|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources - assembly local|`"pack://application:,,,/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier - assembly local|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|Fichier de ressources - assembly référencé|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly référencé|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Fichier de ressources dans un assembly référencé avec version|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|Fichier de contenu|`"pack://application:,,,/ContentFile.xaml"`|
|Fichier contenu dans un sous-dossier|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|Fichier de site d’origine|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|Fichier de site d’origine dans un sous-dossier|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

Le tableau 2 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le balisage.

Tableau 2 : URI à en-tête pack relatifs dans le balisage

|Fichier|URI à en-tête pack relatif|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources dans un assembly local|`"/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly local|`"/Subfolder/ResourceFile.xaml"`|
|Fichier de ressources dans l’assembly référencé|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly référencé|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Fichier de contenu|`"/ContentFile.xaml"`|
|Fichier contenu dans un sous-dossier|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Utilisation d’URI à en-tête pack dans le code

Vous spécifiez un URI à en-tête pack dans le code en instanciant la classe <xref:System.Uri> et en passant l’URI à en-tête pack en tant que paramètre au constructeur. Cette opération est illustrée dans l’exemple suivant.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Par défaut, la classe <xref:System.Uri> considère que les URI à en-tête pack sont absolus. Par conséquent, une exception est levée lorsqu’une instance de la classe <xref:System.Uri> est créée avec un URI à en-tête pack relatif.

```csharp
Uri uri = new Uri("/File.xaml");
```

Heureusement, la surcharge <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> du constructeur de classe <xref:System.Uri> accepte un paramètre de type <xref:System.UriKind> pour vous permettre de spécifier si un URI à en-tête pack est absolu ou relatif.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Vous devez spécifier uniquement <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> lorsque vous êtes certain que l’URI à en-tête pack fourni est l’un ou l’autre. Si vous ne connaissez pas le type d’URI à en-tête pack utilisé, par exemple quand un utilisateur entre un URI à en-tête pack au moment de l’exécution, utilisez <xref:System.UriKind.RelativeOrAbsolute> à la place.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Le tableau 3 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le code à l’aide de <xref:System.Uri?displayProperty=nameWithType>.

Tableau 3 : URI à en-tête pack absolus dans le code

|Fichier|URI à en-tête pack absolu|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources - assembly local|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|Fichier de ressources dans un sous-dossier - assembly local|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Fichier de ressources - assembly référencé|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|Fichier de ressources dans un sous-dossier de l’assembly référencé|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|Fichier de ressources dans un assembly référencé avec version|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|Fichier de contenu|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|Fichier contenu dans un sous-dossier|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|Fichier de site d’origine|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|Fichier de site d’origine dans un sous-dossier|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

Le tableau 4 illustre les différents URI à en-tête pack relatifs que vous pouvez spécifier dans le code à l’aide de <xref:System.Uri?displayProperty=nameWithType>.

Tableau 4 : URI à en-tête pack relatifs dans le code

|Fichier|URI à en-tête pack relatif|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources - assembly local|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly local|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de contenu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Fichier contenu dans un sous-dossier|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scénarios courants d’URI à en-tête pack

Les sections précédentes ont expliqué comment construire des URI à en-tête pack pour identifier les fichiers de ressources, de contenu et de site d’origine. Dans WPF, ces constructions sont utilisées de différentes façons, et les sections suivantes couvrent plusieurs utilisations courantes.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Spécification de l’interface utilisateur à afficher au démarrage d’une application

<xref:System.Windows.Application.StartupUri%2A> spécifie le premier [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à afficher lorsqu’une application WPF est lancée. Pour les applications autonomes, la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut être une fenêtre, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Les applications autonomes et les applications de navigateur XAML (XBAP) peuvent également spécifier une page comme interface utilisateur initiale, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Si l’application est une application autonome et qu’une page est spécifiée avec <xref:System.Windows.Application.StartupUri%2A>, WPF ouvre un <xref:System.Windows.Navigation.NavigationWindow> pour héberger la page. Pour les applications XBAP, la page est affichée dans le navigateur hôte.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Navigation vers une page

L’exemple suivant montre comment naviguer vers une page.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Pour plus d’informations sur les différentes façons de naviguer dans WPF, consultez [vue d’ensemble](navigation-overview.md)de la navigation.

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Spécification d’une icône de fenêtre

L’exemple suivant montre comment utiliser un URI pour spécifier l’icône d’une fenêtre.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Pour plus d’informations, consultez <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Chargement de fichiers vidéo, audio et image

WPF permet aux applications d’utiliser un large éventail de types de médias, qui peuvent tous être identifiés et chargés avec des URI à en-tête pack, comme illustré dans les exemples suivants.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Pour plus d’informations sur l’utilisation du contenu multimédia, consultez [Graphics and Multimedia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Chargement d’un dictionnaire de ressources à partir du site d’origine

Les dictionnaires de ressources (<xref:System.Windows.ResourceDictionary>) peuvent être utilisés pour prendre en charge les thèmes d’application. L’une des façons de créer et de gérer des thèmes consiste à créer plusieurs thèmes en tant que dictionnaires de ressources situés dans le site d’origine d’une application. Ainsi, les thèmes peuvent être ajoutés et mis à jour sans qu’il soit nécessaire de recompiler et de redéployer une application. Ces dictionnaires de ressources peuvent être identifiés et chargés à l’aide d’URI à en-tête pack, comme indiqué dans l’exemple suivant.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Pour obtenir une vue d’ensemble des thèmes dans WPF, consultez [styles et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

## <a name="see-also"></a>Voir aussi

- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
