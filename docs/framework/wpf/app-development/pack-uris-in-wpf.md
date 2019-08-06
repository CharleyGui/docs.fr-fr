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
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796758"
---
# <a name="pack-uris-in-wpf"></a>URI à en-tête pack dans WPF

Dans Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] sont utilisés pour identifier et charger des fichiers de nombreuses façons, notamment:

- Spécifiant [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] le à afficher lorsqu’une application démarre pour la première fois.

- En chargeant des images

- En naviguant vers des pages

- En chargeant des fichiers de données non exécutables

En outre [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , peut être utilisé pour identifier et charger des fichiers à partir de différents emplacements, y compris les éléments suivants:

- L’assembly actuel

- Un assembly référencé

- Un emplacement relatif à un assembly

- Le site d’origine de l’application

Pour fournir un mécanisme cohérent pour identifier et charger ces types de fichiers à partir de ces [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] emplacements, tire parti de l’extensibilité du schéma d’URI à en- *tête pack*. Cette rubrique fournit une vue d’ensemble du schéma, explique comment construire un [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] Pack pour divers scénarios, traite de l’absolu et relatif [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] et [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la résolution, avant d’illustrer [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] l’utilisation de Pack à partir des deux balises et le code.

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Schéma URI à en-tête pack

Le schéma [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en-tête pack est utilisé par la spécification [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC), qui décrit un modèle d’organisation et d’identification du contenu. Les éléments clés de ce modèle sont des packages et des parties, où un *package* est un conteneur logique pour une ou plusieurs *parties*logiques. La figure suivante illustre ce concept.

![Diagramme Package et pièces](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

Pour identifier les parties, la spécification OPC tire parti de l’extensibilité de la norme RFC 2396 (Uniform Resource Identifiers (URI): Syntaxe générique) pour définir le schéma [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de Pack.

Le schéma spécifié par un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est défini par son préfixe; http, FTP et file sont des exemples connus. Le schéma [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en-tête pack utilise «Pack» comme modèle et contient deux composants: autorité et chemin d’accès. Le format d’un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]est le suivant.

*chemin* de l'*autorité*/Pack://

L' *autorité* spécifie le type de package qui contient un composant, tandis que le *chemin d’accès* spécifie l’emplacement d’une partie au sein d’un package.

Ce concept est illustré par le figure suivante :

![Relation entre package, autorité et chemin d’accès](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

Les packages et les parties s’apparentent à des applications et des fichiers, où une application (package) peut inclure un ou plusieurs fichiers (parties), notamment :

- Des fichiers de ressources compilés dans l’assembly local

- Des fichiers de ressources compilés dans un assembly référencé

- Des fichiers de ressources compilés dans un assembly de référence

- Des fichiers de contenu

- Des fichiers de site d’origine

Pour accéder à ces types de fichiers [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , prend en charge deux autorités: application:///et siteoforigin:///. L’autorité application:/// identifie les fichiers de données d’application qui sont connus au moment de la compilation, notamment les fichiers de ressources et de contenu. L’autorité siteoforigin:/// identifie les fichiers de site d’origine. La portée de chaque autorité est indiquée dans la figure suivante.

![Diagramme URI à en-tête pack](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Le composant d’autorité d’un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pack est un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] incorporé qui pointe vers un package et doit être conforme à la norme RFC 2396. De plus, le caractère « / » doit être remplacé par le caractère « , » et les caractères réservés tels que « % » et « ? » doivent être échappés. Pour plus d’informations, consultez l’OPC.

Les sections suivantes expliquent comment construire un [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] Pack à l’aide de ces deux autorités conjointement avec les chemins d’accès appropriés pour identifier les fichiers de ressources, de contenu et de site d’origine.

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>URI à en-tête pack de fichier de ressources

Les fichiers de ressources sont [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] configurés en tant qu' `Resource` éléments et sont compilés dans des assemblys. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]prend en charge la construction [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] de Pack qui peut être utilisée pour identifier les fichiers de ressources qui sont compilés dans l’assembly local ou compilés dans un assembly qui est référencé à partir de l’assembly local.

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>Fichier de ressources d’assembly local

Le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de ressources compilé dans l’assembly local utilise l’autorité et le chemin d’accès suivants:

- **Autorité** : application:///.

- **Chemin d’accès**: Nom du fichier de ressources, y compris son chemin d’accès, relatif à la racine du dossier du projet de l’assembly local.

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources situé à la racine du dossier du projet de l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources situé dans un sous-dossier du dossier du projet de l’assembly local.

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>Fichier de ressources d’assembly référencé

Le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de ressources compilé dans un assembly référencé utilise l’autorité et le chemin d’accès suivants:

- **Autorité** : application:///.

- **Chemin d’accès**: Nom d’un fichier de ressources compilé dans un assembly référencé. Le chemin doit respecter le format suivant :

  *AssemblyShortName*{ *;Version*]{ *;PublicKey*];component/*Path*

  - **NomCourtAssembly** : nom court de l’assembly référencé.

  - **;Version** [facultatif] : version de l’assembly référencé qui contient le fichier de ressources. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;CléPublique** [facultatif] : clé publique utilisée pour signer l’assembly référencé. Elle est utilisée quand plusieurs assemblys référencés ayant le même nom court sont chargés.

  - **;component** : indique que l’assembly désigné est référencé à partir de l’assembly local.

  - **/Chemin** : nom du fichier de ressources, y compris son chemin relatif à la racine du dossier du projet de l’assembly référencé.

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources situé à la racine du dossier du projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources situé dans un sous-dossier du dossier du projet de l’assembly référencé.

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de ressources qui se trouve dans le dossier racine d’un dossier de projet d’assembly spécifique à la version référencé.

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

Notez que la syntaxe [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en-tête pack pour les fichiers de ressources d’assembly référencés peut être utilisée uniquement avec l’autorité application:///. Par exemple, les éléments suivants ne sont pas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]pris en charge dans.

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>URI à en-tête pack de fichier de contenu

Le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de contenu utilise l’autorité et le chemin d’accès suivants:

- **Autorité** : application:///.

- **Chemin d’accès**: Nom du fichier de contenu, y compris son chemin d’accès relatif à l’emplacement du système de fichiers de l’assembly exécutable principal de l’application.

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de contenu, situé dans le même dossier que l’assembly exécutable.

`pack://application:,,,/ContentFile.xaml`

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de contenu, situé dans un sous-dossier relatif à l’assembly exécutable de l’application.

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> Impossible d’accéder aux fichiers de contenu HTML. Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma ne prend en charge que la navigation vers des fichiers html situés sur le site d’origine.

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>URI à en-tête pack de site d’origine

Le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un fichier de site d’origine utilise l’autorité et le chemin d’accès suivants:

- **Autorité** : siteoforigin:///.

- **Chemin d’accès**: Nom du fichier de site d’origine, y compris son chemin d’accès relatif à l’emplacement à partir duquel l’assembly exécutable a été lancé.

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de site d’origine, stocké à l’emplacement à partir duquel l’assembly exécutable est lancé.

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

L’exemple suivant montre le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier de site d’origine, stocké dans un sous-dossier relatif à l’emplacement à partir duquel l’assembly exécutable de l’application est lancé.

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>Fichiers d’échange

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]les fichiers qui sont configurés en tant qu' [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` éléments sont compilés dans des assemblys de la même façon que les fichiers de ressources. Par conséquent [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] , `Page` les éléments peuvent être identifiés [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à l’aide de Pack pour les fichiers de ressources.

Les types de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers couramment configurés en tant [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` qu’éléments ont l’un des éléments suivants comme élément racine:

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>URI à en-tête pack absolus et relatifs

Un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qualifié complet comprend le schéma, l’autorité et le chemin d’accès, et il est considéré comme un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]Pack absolu. En guise de simplification pour [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les développeurs, les éléments vous permettent généralement de définir des attributs [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]appropriés avec un pack relatif, qui comprend uniquement le chemin d’accès.

Par exemple, considérez le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] absolu suivant pour un fichier de ressources dans l’assembly local.

`pack://application:,,,/ResourceFile.xaml`

Le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relatif qui fait référence à ce fichier de ressources est le suivant.

`/ResourceFile.xaml`

> [!NOTE]
> Étant donné que les fichiers de site d’origine ne sont pas associés à des assemblys, ils ne peuvent [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]être référencés qu’avec l’Absolute Pack.

Par défaut, un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relatif est considéré comme relatif à l’emplacement du balisage ou du code qui contient la référence. Toutefois, si une barre oblique inverse de début est utilisée, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] la référence à un pack relatif est alors considérée comme relative à la racine de l’application. Par exemple, considérez la structure de projet suivante.

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Si Page1. xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à la *racine*\SubFolder\Page2.xaml, la référence peut utiliser le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pack relatif suivant.

`Page2.xaml`

Si Page1. xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à la *racine*\Page2.xaml, la référence peut utiliser le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pack relatif suivant.

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Résolution des URI à en-tête pack

Le format de Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] permet à un pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour différents types de fichiers de se présenter de la même façon. Par exemple, considérez le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]absolu suivant.

`pack://application:,,,/ResourceOrContentFile.xaml`

Ce pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] absolu peut faire référence à un fichier de ressources dans l’assembly local ou à un fichier de contenu. Il en va de même pour la relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]suivante.

`/ResourceOrContentFile.xaml`

Pour déterminer le type de fichier auquel un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fait référence, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] résout [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] les fichiers de ressources dans les assemblys locaux et les fichiers de contenu à l’aide de l’heuristique suivante:

1. Sondez les métadonnées de <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> l’assembly pour un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]attribut qui correspond au Pack.

2. Si l' <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est trouvé, le chemin d’accès à [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ce package fait référence à un fichier de contenu.

3. Si l' <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est introuvable, Sondez les fichiers de ressources définis qui sont compilés dans l’assembly local.

4. Si un fichier de ressources qui correspond au chemin d’accès [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] du package est trouvé, le chemin d' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] accès à l’en-tête pack fait référence à un fichier de ressources.

5. Si la ressource est introuvable, la créée <xref:System.Uri> en interne n’est pas valide.

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]la résolution ne s’applique [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pas à ce qui suit:

- Fichiers de contenu dans les assemblys référencés: ces types de fichiers ne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]sont pas pris en charge par.

- Fichiers incorporés dans les assemblys référencés: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui les identifient sont uniques parce qu’ils incluent le nom de l’assembly référencé et le `;component` suffixe.

- Fichiers du site d’origine [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : les identifiant sont uniques, car il s’agit des seuls fichiers qui peuvent être [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] identifiés par un Pack qui contiennent l’autorité siteoforigin:///.

Une simplification de la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] résolution de Pack permet au code d’être quelque peu indépendant des emplacements des fichiers de ressources et de contenu. Par exemple, si vous avez un fichier de ressources dans l’assembly local qui est reconfiguré pour être un fichier de contenu, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] le Pack de la ressource reste le même, tout comme le code qui l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]utilise.

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>Programmation avec des URI à en-tête pack

De [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nombreuses classes implémentent des propriétés qui peuvent être [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]définies avec Pack, notamment:

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

Ces propriétés peuvent être définies à partir du balisage et du code. Cette section décrit les constructions de base pour les deux, et fournit des exemples de scénarios courants.

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>Utilisation d’URI à en-tête pack dans le balisage

Un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est spécifié dans le balisage en définissant l’élément d’un attribut [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]avec le package. Par exemple :

`<element attribute="pack://application:,,,/File.xaml" />`

Le tableau 1 illustre les différents packs [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] absolus que vous pouvez spécifier dans le balisage.

Tableau 1 : URI à en-tête pack absolus dans le balisage

|Fichier|Pack absolu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
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

Le tableau 2 illustre les différents packs [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relatifs que vous pouvez spécifier dans le balisage.

Tableau 2 : URI à en-tête pack relatifs dans le balisage

|Fichier|Pack relatif[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources dans un assembly local|`"/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly local|`"/Subfolder/ResourceFile.xaml"`|
|Fichier de ressources dans l’assembly référencé|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|Fichier de ressources dans un sous-dossier de l’assembly référencé|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|Fichier de contenu|`"/ContentFile.xaml"`|
|Fichier contenu dans un sous-dossier|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>Utilisation d’URI à en-tête pack dans le code

Vous spécifiez un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pack dans le code en <xref:System.Uri> instanciant la classe et [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] en passant le Pack en tant que paramètre au constructeur. Cela est illustré par l'exemple suivant.

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

Par défaut, la <xref:System.Uri> classe considère le [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] Pack comme étant absolu. Par conséquent, une exception est levée lorsqu’une instance de <xref:System.Uri> la classe est créée avec un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]relatif.

```csharp
Uri uri = new Uri("/File.xaml");
```

Heureusement, la <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> surcharge <xref:System.Uri> du constructeur de classe accepte un paramètre de type <xref:System.UriKind> pour vous permettre de spécifier si un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est absolu ou relatif.

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

Vous devez spécifier uniquement <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> lorsque vous êtes certain que le Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fourni est l’un ou l’autre. Si vous ne connaissez pas le type de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pack utilisé, par exemple quand un utilisateur entre un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] au moment de l’exécution, <xref:System.UriKind.RelativeOrAbsolute> utilisez à la place.

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

Le tableau 3 illustre les différents packs [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relatifs que vous pouvez spécifier dans le code <xref:System.Uri?displayProperty=nameWithType>à l’aide de.

Tableau 3 : URI à en-tête pack absolus dans le code

|Fichier|Pack absolu[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
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

Le tableau 4 illustre les différents packs [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relatifs que vous pouvez spécifier dans le <xref:System.Uri?displayProperty=nameWithType>code à l’aide de.

Tableau 4 : URI à en-tête pack relatifs dans le code

|Fichier|Pack relatif[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|Fichier de ressources - assembly local|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly local|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de ressources dans un sous-dossier - assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|Fichier de contenu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|Fichier contenu dans un sous-dossier|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>Scénarios courants d’URI à en-tête pack

Les sections précédentes ont expliqué comment construire un pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pour identifier les fichiers de ressources, de contenu et de site d’origine. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ces constructions sont utilisées de différentes façons, et les sections suivantes couvrent plusieurs utilisations courantes.

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Spécification de l’interface utilisateur à afficher au démarrage d’une application

<xref:System.Windows.Application.StartupUri%2A>Spécifie le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] premier à afficher lorsqu' [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] une application est lancée. Pour les applications autonomes [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , peut être une fenêtre, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

Les applications autonomes et [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également spécifier une page comme interface utilisateur initiale, comme illustré dans l’exemple suivant.

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

Si l’application est une application autonome et qu’une page est spécifiée <xref:System.Windows.Application.StartupUri%2A>avec [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , ouvre <xref:System.Windows.Navigation.NavigationWindow> un pour héberger la page. Pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], la page s’affiche dans le navigateur hôte.

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>Navigation vers une page

L’exemple suivant montre comment naviguer vers une page.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Pour plus d’informations sur les différentes façons de naviguer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]dans, consultez [vue d’ensemble](navigation-overview.md)de la navigation.

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>Spécification d’une icône de fenêtre

L’exemple suivant montre comment utiliser un URI pour spécifier l’icône d’une fenêtre.

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

Pour plus d'informations, consultez <xref:System.Windows.Window.Icon%2A>.

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>Chargement de fichiers vidéo, audio et image

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]permet aux applications d’utiliser un large éventail de types de médias, qui peuvent tous être identifiés et chargés avec [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]Pack, comme indiqué dans les exemples suivants.

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

Pour plus d’informations sur l’utilisation du contenu multimédia, consultez [Graphics and Multimedia](../graphics-multimedia/index.md).

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Chargement d’un dictionnaire de ressources à partir du site d’origine

Les dictionnaires de<xref:System.Windows.ResourceDictionary>ressources () peuvent être utilisés pour prendre en charge les thèmes d’application. L’une des façons de créer et de gérer des thèmes consiste à créer plusieurs thèmes en tant que dictionnaires de ressources situés dans le site d’origine d’une application. Ainsi, les thèmes peuvent être ajoutés et mis à jour sans qu’il soit nécessaire de recompiler et de redéployer une application. Ces dictionnaires de ressources peuvent être identifiés et chargés à [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]l’aide de Pack, ce qui est illustré dans l’exemple suivant.

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

Pour obtenir une vue d’ensemble [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]des thèmes dans, consultez [styles et création de modèles](../controls/styling-and-templating.md).

## <a name="see-also"></a>Voir aussi

- [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md)
