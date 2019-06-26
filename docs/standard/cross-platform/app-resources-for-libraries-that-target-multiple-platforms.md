---
title: Ressources d'application pour les bibliothèques qui ciblent des plateformes multiples
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba4546397adcfcf6142b41482f574cf86607a6b9
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402116"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Ressources d'application pour les bibliothèques qui ciblent des plateformes multiples
Vous pouvez utiliser le .NET Framework [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) type pour vous assurer que les ressources dans vos bibliothèques de classes sont accessible à partir de plusieurs plateformes de projet. Ce type de projet est disponible dans Visual Studio 2012 et qu’elle cible le sous-ensemble portable de la bibliothèque de classes .NET Framework. L'utilisation de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] garantit l'accessibilité de votre bibliothèque à partir des applications de bureau, des [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], Silverlight et Windows Phone.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] ne génère qu'un sous-ensemble très limité des types dans l'espace de noms <xref:System.Resources> disponible pour votre application, mais il vous permet d'utiliser la classe <xref:System.Resources.ResourceManager> pour extraire des ressources. Toutefois, si vous créez une application à l'aide de Visual Studio, vous devez utiliser le wrapper fortement typé créé par Visual Studio, plutôt que d'utiliser directement la classe <xref:System.Resources.ResourceManager>.

 Pour créer un wrapper fortement typé dans Visual Studio, définissez le fichier de ressources principal **modificateur d’accès** dans le Concepteur de ressources Visual Studio pour **Public**. Cela crée un fichier [resourceFileName].designer.cs ou [resourceFileName].designer.vb qui contient le wrapper fortement typé ResourceManager. Pour plus d’informations sur l’utilisation d’un wrapper de ressources fortement typées, consultez la section « Génération d’une classe fortement typée ressource » dans le [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) rubrique.

## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Gestionnaire des ressources dans [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]
 Dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], tout accès aux ressources est géré par la classe <xref:System.Resources.ResourceManager>. Étant donné que les types dans l'espace de noms <xref:System.Resources>, tels que <xref:System.Resources.ResourceReader> et <xref:System.Resources.ResourceSet>, ne sont pas accessibles à partir d'un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], elles ne peuvent pas être utilisées pour accéder aux ressources.

 Le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclut les quatre membres <xref:System.Resources.ResourceManager> répertoriés dans le tableau suivant. Ces constructeurs et méthodes vous permettent d'instancier un objet <xref:System.Resources.ResourceManager> et d'extraire des ressources de chaîne.

|Membre`ResourceManager`|Description|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Créé une instance <xref:System.Resources.ResourceManager> pour accéder au fichier de ressources nommé trouvé dans l'assembly spécifié.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Créé une instance <xref:System.Resources.ResourceManager> qui correspond au type spécifié.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Extrait une ressource nommée pour la culture actuelle.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Extrait une ressource nommée appartenant à la culture spécifiée.|

 L'exclusion d'autres membres <xref:System.Resources.ResourceManager> de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] signifie que les objets sérialisés, les données qui ne sont pas des chaînes, et les images ne peuvent pas être extraits à partir d'un fichier de ressources. Pour utiliser des ressources à partir de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], vous devez stocker les données d'objet sous forme de chaîne. Par exemple, vous pouvez stocker des valeurs numériques dans un fichier de ressources en les convertissant en chaînes, et les extraire, puis, vous pouvez les reconvertir en nombres à l'aide de la méthode `Parse` ou `TryParse` du type de données numériques. Vous pouvez convertir des images ou autres données binaires en représentation sous forme de chaîne en appelant la méthode <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>, et les restaurer en un tableau d'octets en appelant la méthode <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] et Applications Windows Store
 Les projets [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] stockent des ressources dans des fichiers .resx, qui sont alors compilés dans des fichiers .resources et incorporés dans l'assembly principal ou dans des assemblys satellites au moment de la compilation. En revanche, les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] requièrent que les ressources soient stockées dans des fichiers .resw, qui sont ensuite compilés dans un seul fichier d'index de ressource de package (PRI). Toutefois, en dépit de formats de fichier incompatibles, le [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] s'exécutera dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].

 Pour utiliser votre bibliothèque de classes à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à celle-ci dans votre projet d'application Windows Store. Visual Studio extrait les ressources à partir de votre assembly dans un fichier .resw et l’utiliser pour générer un fichier PRI à partir de laquelle le Runtime Windows peut extraire des ressources en toute transparence. Au moment de l’exécution, le Runtime Windows exécute le code dans votre [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], mais il récupère les ressources de votre bibliothèque de classes Portable à partir du fichier PRI.

 Si le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclut des ressources localisées, utilisez le modèle « hub and spoke » pour les déployer comme vous le feriez pour une bibliothèque dans une application de bureau. Pour utiliser votre fichier de ressources principal et n'importe quel fichier de ressources localisé dans votre application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à l'assembly principal. Au moment de la compilation, Visual Studio extrait les ressources à partir du fichier de ressources principal et de tous les fichiers de ressources localisés dans des fichiers .resw distincts. Il compile ensuite les fichiers .resw dans un seul fichier PRI qui accède à des Windows Runtime en cours d’exécution.

<a name="NonLoc"></a>
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Exemple : Non localisé [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]
 L'exemple suivant d'un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] simple et non localisé utilise des ressources pour stocker les noms des colonnes et déterminer le nombre de caractères à réserver aux données tabulaires. L'exemple utilise un fichier nommé LibResources.resx pour stocker les ressources de chaîne répertoriées dans le tableau suivant.

|Nom de la ressource|Valeur de la ressource|
|-------------------|--------------------|
|Né le|Date de naissance|
|BornLength|12|
|Embauché|Date d'embauche|
|HiredLength|12|
|Id|Id|
|ID.Length|12|
|Nom|Nom|
|NameLength|25|
|Titre|Base de données des employés|

 Le code suivant définit un `UILibrary` classe qui utilise le wrapper de gestionnaire de ressources nommé `resources` généré par Visual Studio lorsque le **modificateur d’accès** pour le fichier est remplacé par **Public** . La classe UILibrary analyse les données de chaîne selon les besoins. . Notez que la classe est dans l'espace de noms `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console. Cela nécessite une référence à UILibrary.dll doit être ajouté au projet d’application console.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Cela nécessite une référence à UILibrary.dll doit être ajouté au projet d’application Windows Store.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Exemple : Localisé [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]
 L'exemple de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localisé suivant inclut des ressources pour les cultures française (France) et anglaise (États-Unis). La culture anglais (États-Unis) est la culture par défaut de l’application ; ses ressources sont répertoriées dans la table dans le [section précédente](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Le fichier de ressources de la culture française (France) est nommé LibResources.fr-FR.resx et inclut les ressources de type de chaîne répertoriées dans le tableau suivant. Le code source de la classe `UILibrary` est identique que celui présenté dans la section précédente.

|Nom de la ressource|Valeur de la ressource|
|-------------------|--------------------|
|Né le|Date de naissance|
|BornLength|20|
|Embauché|Date d'embauche|
|HiredLength|16|
|Id|Id|
|Nom|Nom|
|Titre|Base de données des employés|

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console. Cela nécessite une référence à UILibrary.dll doit être ajouté au projet d’application console.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Cela nécessite une référence à UILibrary.dll doit être ajouté au projet d’application Windows Store. Il utilise la propriété statique `ApplicationLanguages.PrimaryLanguageOverride` pour définir la langue par défaut sur Français.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager>
- [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)
- [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
