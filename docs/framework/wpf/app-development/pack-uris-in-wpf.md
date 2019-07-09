---
title: URI à en-tête pack dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 2a0fa9b67f4fa1f3b701cb64579727bedbf5028c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663784"
---
# <a name="pack-uris-in-wpf"></a>URI à en-tête pack dans WPF

Dans Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] sont utilisés pour identifier et charger des fichiers de plusieurs façons, notamment les éléments suivants :

- En spécifiant le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à afficher lorsqu’une application démarre.

- En chargeant des images

- En naviguant vers des pages

- En chargeant des fichiers de données non exécutables

En outre, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] peut être utilisé pour identifier et charger des fichiers à partir de différents emplacements, notamment les suivantes :

- L’assembly actuel

- Un assembly référencé

- Un emplacement relatif à un assembly

- Le site d’origine de l’application

Pour fournir un mécanisme cohérent d’identification et de chargement de ces types de fichiers à partir de ces emplacements, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tire parti de l’extensibilité de la *schéma URI à en-tête pack*. Cette rubrique fournit une vue d’ensemble du schéma, explique comment construire pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour un éventail de scénarios, aborde absolute et relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] et [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] résolution, avant d’afficher l’utilisation du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à partir de ces deux balisage et le code.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schéma URI à en-tête pack

Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma est utilisé par le [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) spécification (OPC), qui décrit un modèle d’organisation et d’identification du contenu. Les éléments clés de ce modèle sont des packages et des parties, où un *package* est un conteneur logique pour un ou plus logique *parties*. La figure suivante illustre ce concept.

![Diagramme Package et pièces](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Pour identifier les parties, la spécification OPC exploite l’extensibilité de la RFC 2396 (identificateurs de ressource uniforme (URI) : Syntaxe générique) pour définir le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma.

Le schéma spécifié par un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est défini par son préfixe ; http, ftp et file sont des exemples connus. Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma utilise « pack » comme modèle et contient deux composants : autorité et chemin d’accès. Le format est le suivant pour un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

pack://*authority*/*path*

Le *autorité* Spécifie le type de package contenant une partie, tandis que le *chemin d’accès* Spécifie l’emplacement d’une partie dans un package.

Ce concept est illustré par le figure suivante :

![Relation entre package, autorité et chemin d’accès](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Les packages et les parties s’apparentent à des applications et des fichiers, où une application (package) peut inclure un ou plusieurs fichiers (parties), notamment :

- Des fichiers de ressources compilés dans l’assembly local

- Des fichiers de ressources compilés dans un assembly référencé

- Des fichiers de ressources compilés dans un assembly de référence

- Des fichiers de contenu

- Des fichiers de site d’origine

Accéder à ces types de fichiers, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge deux autorités : application : / / / et siteoforigin : / / /. L’autorité application:/// identifie les fichiers de données d’application qui sont connus au moment de la compilation, notamment les fichiers de ressources et de contenu. L’autorité siteoforigin:/// identifie les fichiers de site d’origine. La portée de chaque autorité est indiquée dans la figure suivante.

![Diagramme URI à en-tête pack](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Le composant d’autorité d’un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est incorporé [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui pointe vers un package et doit être conforme à la norme RFC 2396. De plus, le caractère « / » doit être remplacé par le caractère « , » et les caractères réservés tels que « % » et « ? » doivent être échappés. Pour plus d’informations, consultez l’OPC.

Les sections suivantes expliquent comment construire pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à l’aide de ces deux autorités conjointement avec les chemins d’accès appropriés pour identifier les ressources, de contenu et de site des fichiers d’origine.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>URI à en-tête pack de fichier de ressources

Fichiers de ressources sont configurés en tant que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` éléments et sont compilés dans des assemblys. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge la construction du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui peut être utilisé pour identifier les fichiers de ressources qui sont compilés dans l’assembly local ou compilés dans un assembly qui est référencé à partir de l’assembly local.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Fichier de ressources d’assembly local

Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour une ressource de fichier qui est compilé dans l’assembly local utilise l’autorité et chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin d’accès**: Le nom du fichier de ressources, y compris son chemin d’accès, par rapport à la racine du dossier projet assembly local.

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve à la racine du dossier du projet de l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve dans un sous-dossier du dossier de projet de l’assembly local.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Fichier de ressources d’assembly référencé

Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour une ressource de fichier qui est compilé dans un assembly référencé utilise l’autorité et chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin d’accès**: Le nom du fichier de ressources qui est compilé dans un assembly référencé. Le chemin doit respecter le format suivant :

  *AssemblyShortName*{ *;Version*]{ *;PublicKey*];component/*Path*

  - **NomCourtAssembly** : nom court de l’assembly référencé.

  - **;Version** [facultatif] : version de l’assembly référencé qui contient le fichier de ressources. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;CléPublique** [facultatif] : clé publique utilisée pour signer l’assembly référencé. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;component** : indique que l’assembly désigné est référencé à partir de l’assembly local.

  - **/Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly référencé.

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve dans la racine du dossier de projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve dans un sous-dossier du dossier de projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve dans le dossier racine du dossier de projet de l’assembly référencé, spécifique à la version.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Notez que le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe pour les fichiers de ressources d’assembly référencé peut être utilisé uniquement avec l’application : / / / autorité. Par exemple, ce qui suit n’est pas pris en charge dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>URI à en-tête pack de fichier de contenu

Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de contenu utilise l’autorité et chemin d’accès suivants :

- **Autorité** : application:///.

- **Chemin d’accès**: Le nom du fichier de contenu, y compris son chemin d’accès relatif à l’emplacement de système de fichiers de l’assembly exécutable principal de l’application.

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de contenu, situé dans le même dossier que l’assembly exécutable.

`pack://application:,,,/ContentFile.xaml`

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de contenu, situé dans un sous-dossier relatif à l’assembly l’application exécutable.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Il est impossible de naviguer vers les fichiers de contenu [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma prend uniquement en charge la navigation vers [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] les fichiers qui se trouvent sur le site d’origine.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>URI à en-tête pack de site d’origine

Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un site d’origine fichier utilise l’autorité et chemin d’accès suivants :

- **Autorité** : siteoforigin:///.

- **Chemin d’accès**: Le nom du site de fichier d’origine, y compris son chemin d’accès relatif à l’emplacement à partir duquel l’assembly exécutable a été lancé.

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier site d’origine, stocké dans l’emplacement à partir duquel l’assembly exécutable est lancé.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

L’exemple suivant montre le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier site d’origine, stocké dans un sous-dossier relatif à l’emplacement à partir duquel l’assembly exécutable de l’application est lancée.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Fichiers d’échange

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les fichiers qui sont configurés en tant que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` éléments sont compilés dans des assemblys dans la même façon que les fichiers de ressources. Par conséquent, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` éléments peuvent être identifiés à l’aide du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour les fichiers de ressources.

Les types de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les fichiers qui sont généralement configurés en tant que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` éléments ont les valeurs suivantes comme élément racine :

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>URI à en-tête pack absolus et relatifs

Un pack complet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] inclut le schéma, l’autorité et le chemin d’accès, et il est considéré comme un pack absolu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. En guise de simplification pour les développeurs, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments vous permettent généralement de définir des attributs appropriés avec un pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], qui inclut uniquement le chemin d’accès.

Par exemple, considérez le pack absolu suivant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de ressources dans l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

Le pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à cette ressource de fichier est la suivante.

`/ResourceFile.xaml`

> [!NOTE]
> Étant donné que le site des fichiers d’origine ne sont pas associés à des assemblys, ils peuvent être référencés à pack absolu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].

Par défaut, un pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est considéré comme relatif à l’emplacement du balisage ou du code qui contient la référence. Si une barre oblique inverse de début est utilisée, toutefois, l’en-tête pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] référence est alors considéré comme relatif à la racine de l’application. Par exemple, considérez la structure de projet suivante.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Si Page1.xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à *racine*\SubFolder\Page2.xaml, la référence peut utiliser le pack relatif suivant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`Page2.xaml`

Si Page1.xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à *racine*\Page2.xaml, la référence peut utiliser le pack relatif suivant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Résolution des URI à en-tête pack

Le format du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] rend possible pour le pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour différents types de fichiers aient la même apparence. Par exemple, considérez le pack absolu suivant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`pack://application:,,,/ResourceOrContentFile.xaml`

Ce pack absolu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] peut faire référence à un fichier de ressources dans l’assembly local ou un fichier de contenu. Vaut également pour l’en-tête pack relatif suivant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

`/ResourceOrContentFile.xaml`

Afin de déterminer le type de fichier qu’un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fait référence, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] résout [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour les fichiers de ressources dans les assemblys locaux et les fichiers de contenu à l’aide de l’heuristique suivante :

1. Recherchez dans les métadonnées d’assembly pour un <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut qui correspond à la pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

2. Si le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est trouvé, le chemin d’accès du pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fait référence à un fichier de contenu.

3. Si le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est introuvable, recherchez les fichiers de ressources définis qui sont compilés dans l’assembly local.

4. Si un fichier de ressources qui correspond au chemin du pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est trouvée, le chemin d’accès du pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fait référence à un fichier de ressources.

5. Si la ressource est introuvable, créé en interne <xref:System.Uri> n’est pas valide.

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] résolution n’est pas applicable à [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui font référence à ce qui suit :

- Fichiers de contenu dans les assemblys référencés : ces types de fichiers ne sont pas pris en charge par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

- Fichiers incorporés dans les assemblys référencés : [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui les identifient sont uniques, car ils comprennent à la fois le nom de l’assembly référencé et le `;component` suffixe.

- Site des fichiers d’origine : [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui les identifient sont uniques car elles sont les seuls fichiers qui peuvent être identifiés par le pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui contiennent le siteoforigin : / / / autorité.

Une des simplifications offertes pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] permet de résolution pour le code peut être quelque peu indépendant des emplacements des fichiers de ressources et de contenu. Par exemple, si vous avez un fichier de ressources dans l’assembly local qui est reconfiguré afin d’être un fichier de contenu, le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la ressource reste le même que le code qui utilise le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programmation avec des URI à en-tête pack

Nombreux [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implémentent des propriétés qui peuvent être définies avec pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], y compris :

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Ces propriétés peuvent être définies à partir du balisage et du code. Cette section décrit les constructions de base pour les deux, et fournit des exemples de scénarios courants.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Utilisation d’URI à en-tête pack dans le balisage

Un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est spécifié dans le balisage en définissant l’élément d’un attribut avec le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Par exemple :

`<element attribute="pack://application:,,,/File.xaml" />`

Le tableau 1 illustre les différents pack absolu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que vous pouvez spécifier dans le balisage.

Tableau 1 : URI à en-tête Pack absolus dans le balisage

|Fichier|En-tête pack absolu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
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

Le tableau 2 illustre les différents pack relatif [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que vous pouvez spécifier dans le balisage.

Tableau 2 : URI à en-tête Pack relatifs dans balisage

|Fichier|Pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources dans un assembly local|`"/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly local|`"/Subfolder/ResourceFile.xaml"`|
|Fichier de ressources dans l’assembly référencé|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly référencé|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Fichier de contenu|`"/ContentFile.xaml"`|
|Fichier contenu dans un sous-dossier|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Utilisation d’URI à en-tête pack dans le code

Vous spécifiez un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dans le code en instanciant le <xref:System.Uri> classe et en passant le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] en tant que paramètre au constructeur. Cela est illustré par l'exemple suivant.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Par défaut, le <xref:System.Uri> classe considère pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour être absolus. Par conséquent, une exception est levée lorsqu’une instance de la <xref:System.Uri> classe est créée avec un pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].

```csharp
Uri uri = new Uri("/File.xaml");
```

Heureusement, le <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> surcharge de la <xref:System.Uri> constructeur de classe accepte un paramètre de type <xref:System.UriKind> vous permet de spécifier si un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est absolu ou relatif.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Vous devez spécifier uniquement <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> lorsque vous êtes certain que le pack fourni [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est un ou l’autre. Si vous ne connaissez pas le type de module [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui est utilisé, par exemple lorsqu’un utilisateur entre un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] au moment de l’exécution, utilisez <xref:System.UriKind.RelativeOrAbsolute> à la place.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Le tableau 3 illustre les différents pack relatif [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que vous pouvez spécifier dans le code à l’aide de <xref:System.Uri?displayProperty=nameWithType>.

Tableau 3 : URI à en-tête Pack absolus dans Code

|Fichier|En-tête pack absolu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
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

Le tableau 4 illustre les différents pack relatif [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que vous pouvez spécifier dans le code à l’aide <xref:System.Uri?displayProperty=nameWithType>.

Tableau 4 : URI à en-tête Pack relatifs dans Code

|Fichier|Pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources - assembly local|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly local|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de contenu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Fichier contenu dans un sous-dossier|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scénarios courants d’URI à en-tête pack

Les sections précédentes ont expliqué comment construire pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour identifier les ressources, de contenu et de site des fichiers d’origine. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ces constructions sont utilisées de différentes façons, et les sections suivantes décrivent plusieurs usages courants.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Spécification de l’interface utilisateur à afficher au démarrage d’une application

<xref:System.Windows.Application.StartupUri%2A> Spécifie le premier [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à afficher quand un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application est lancée. Pour les applications autonomes, le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut être une fenêtre, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Applications autonomes et [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peut également spécifier une page comme interface utilisateur initiale, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Si l’application est une application autonome et une page est spécifiée avec <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ouvre un <xref:System.Windows.Navigation.NavigationWindow> pour héberger la page. Pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], la page est affichée dans le navigateur hôte.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Navigation vers une page

L’exemple suivant montre comment naviguer vers une page.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Pour plus d’informations sur les différentes façons de naviguer dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [vue d’ensemble de la Navigation](navigation-overview.md).

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Spécification d’une icône de fenêtre

L’exemple suivant montre comment utiliser un URI pour spécifier l’icône d’une fenêtre.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Pour plus d'informations, consultez <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Chargement de fichiers vidéo, audio et image

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux applications d’utiliser une grande variété de types de médias, qui peuvent être identifiés et chargés avec pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], comme illustré dans les exemples suivants.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Pour plus d’informations sur l’utilisation de contenu multimédia, consultez [graphiques et multimédia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Chargement d’un dictionnaire de ressources à partir du site d’origine

Dictionnaires de ressources (<xref:System.Windows.ResourceDictionary>) peut être utilisé pour prendre en charge des thèmes d’application. L’une des façons de créer et de gérer des thèmes consiste à créer plusieurs thèmes en tant que dictionnaires de ressources situés dans le site d’origine d’une application. Ainsi, les thèmes peuvent être ajoutés et mis à jour sans qu’il soit nécessaire de recompiler et de redéployer une application. Ces dictionnaires de ressources peuvent être identifiés et chargés à l’aide du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], ce qui est indiqué dans l’exemple suivant.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Pour une vue d’ensemble des thèmes dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [Styling and Templating](../controls/styling-and-templating.md).

## <a name="see-also"></a>Voir aussi

- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
