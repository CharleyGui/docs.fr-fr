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
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506013"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Ressources d'application pour les bibliothèques qui ciblent des plateformes multiples
Vous pouvez utiliser le .NET Framework [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) type pour vous assurer que les ressources dans vos bibliothèques de classes sont accessible à partir de plusieurs plateformes de projet. Ce type de projet est disponible dans Visual Studio 2012 et qu’elle cible le sous-ensemble portable de la bibliothèque de classes .NET Framework. À l’aide d’une bibliothèque de classes Portable garantit que votre bibliothèque est accessible à partir d’applications de bureau, les applications Silverlight, les applications Windows Phone, et [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Le projet de bibliothèque de classes Portable rend uniquement un sous-ensemble très limité des types dans le <xref:System.Resources> espace de noms disponible pour votre application, mais il vous autorise à utiliser le <xref:System.Resources.ResourceManager> classe pour récupérer des ressources. Toutefois, si vous créez une application à l'aide de Visual Studio, vous devez utiliser le wrapper fortement typé créé par Visual Studio, plutôt que d'utiliser directement la classe <xref:System.Resources.ResourceManager>.

 Pour créer un wrapper fortement typé dans Visual Studio, définissez le fichier de ressources principal **modificateur d’accès** dans le Concepteur de ressources Visual Studio pour **Public**. Cela crée un fichier [resourceFileName].designer.cs ou [resourceFileName].designer.vb qui contient le wrapper fortement typé ResourceManager. Pour plus d’informations sur l’utilisation d’un wrapper de ressources fortement typées, consultez la section « Génération d’une classe fortement typée ressource » dans le [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) rubrique.

## <a name="resource-manager-in-the-portable-class-library"></a>Gestionnaire de ressources dans la bibliothèque de classes Portable
 Dans un projet de bibliothèque de classes Portable, tous les accès aux ressources sont géré par le <xref:System.Resources.ResourceManager> classe. Étant donné que les types dans le <xref:System.Resources> espace de noms, tel que <xref:System.Resources.ResourceReader> et <xref:System.Resources.ResourceSet>, sont non accessible à partir d’un projet de bibliothèque de classes Portable, ils ne peuvent pas être utilisés pour accéder aux ressources.

 Le projet de bibliothèque de classes Portable inclut les quatre <xref:System.Resources.ResourceManager> membres répertoriés dans le tableau suivant. Ces constructeurs et méthodes vous permettent d'instancier un objet <xref:System.Resources.ResourceManager> et d'extraire des ressources de chaîne.

|Membre`ResourceManager`|Description|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Créé une instance <xref:System.Resources.ResourceManager> pour accéder au fichier de ressources nommé trouvé dans l'assembly spécifié.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Créé une instance <xref:System.Resources.ResourceManager> qui correspond au type spécifié.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Extrait une ressource nommée pour la culture actuelle.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Extrait une ressource nommée appartenant à la culture spécifiée.|

 L’exclusion des autres <xref:System.Resources.ResourceManager> membres à partir des moyens de bibliothèque de classes Portable qui sérialiser des objets, les données non-chaînées et les images ne peut pas être récupérées à partir d’un fichier de ressources. Pour utiliser des ressources à partir d’une bibliothèque de classes Portable, vous devez stocker toutes les données d’objet sous forme de chaîne. Par exemple, vous pouvez stocker des valeurs numériques dans un fichier de ressources en les convertissant en chaînes, et les extraire, puis, vous pouvez les reconvertir en nombres à l'aide de la méthode `Parse` ou `TryParse` du type de données numériques. Vous pouvez convertir des images ou autres données binaires en représentation sous forme de chaîne en appelant la méthode <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>, et les restaurer en un tableau d'octets en appelant la méthode <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>La bibliothèque de classes Portable et les applications du Windows Store
 Les projets de bibliothèque de classes portables stockent des ressources dans les fichiers .resx, qui sont ensuite compilés en fichiers .resources et incorporés dans l’assembly principal ou dans des assemblys satellites à la compilation. En revanche, les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] requièrent que les ressources soient stockées dans des fichiers .resw, qui sont ensuite compilés dans un seul fichier d'index de ressource de package (PRI). Toutefois, en dépit de formats de fichier incompatibles, votre bibliothèque de classes portables ne fonctionnera un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application.

 Pour utiliser votre bibliothèque de classes à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à celle-ci dans votre projet d'application Windows Store. Visual Studio extrait les ressources à partir de votre assembly dans un fichier .resw et l’utiliser pour générer un fichier PRI à partir de laquelle le Runtime Windows peut extraire des ressources en toute transparence. Au moment de l’exécution, le Runtime Windows exécute le code dans votre bibliothèque de classes Portable, mais il récupère les ressources de votre bibliothèque de classes Portable à partir du fichier PRI.

 Si votre projet de bibliothèque de classes Portable inclut des ressources localisées, vous utilisez le modèle « hub and spoke » pour les déployer comme vous le feriez pour une bibliothèque dans une application de bureau. Pour utiliser votre fichier de ressources principal et n'importe quel fichier de ressources localisé dans votre application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à l'assembly principal. Au moment de la compilation, Visual Studio extrait les ressources à partir du fichier de ressources principal et de tous les fichiers de ressources localisés dans des fichiers .resw distincts. Il compile ensuite les fichiers .resw dans un seul fichier PRI qui accède à des Windows Runtime en cours d’exécution.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Exemple : Bibliothèque de classes de Portable non localisé
 L’exemple suivant de bibliothèque de classes Portable simple et non localisé utilise des ressources pour stocker les noms de colonnes et pour déterminer le nombre de caractères à réserver pour les données tabulaires. L'exemple utilise un fichier nommé LibResources.resx pour stocker les ressources de chaîne répertoriées dans le tableau suivant.

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

## <a name="example-localized-portable-class-library"></a>Exemple : Bibliothèque de classes Portable localisée
 L’exemple de bibliothèque de classes Portable localisé suivant inclut des ressources pour le Français (France) et les cultures Anglais (États-Unis). La culture anglais (États-Unis) est la culture par défaut de l’application ; ses ressources sont répertoriées dans la table dans le [section précédente](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Le fichier de ressources de la culture française (France) est nommé LibResources.fr-FR.resx et inclut les ressources de type de chaîne répertoriées dans le tableau suivant. Le code source de la classe `UILibrary` est identique que celui présenté dans la section précédente.

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
