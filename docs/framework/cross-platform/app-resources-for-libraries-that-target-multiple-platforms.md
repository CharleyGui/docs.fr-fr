---
title: Ressources d'application pour les bibliothèques qui ciblent des plateformes multiples
ms.date: 07/18/2018
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
ms.openlocfilehash: a4fa3f5e5a4b0e88a0c37f84672ab4b611f89f0c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272921"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Ressources d'application pour les bibliothèques qui ciblent des plateformes multiples

Vous pouvez utiliser le type de projet de [bibliothèque de classes Portable](portable-class-library.md) .NET Framework pour vous assurer que les ressources de vos bibliothèques de classes sont accessibles à partir de plusieurs plateformes. Ce type de projet est disponible dans Visual Studio 2012 et cible le sous-ensemble portable de la bibliothèque de classes .NET Framework. L’utilisation d’une bibliothèque de classes portable garantit que votre bibliothèque est accessible à partir des applications de bureau, des applications Silverlight, des applications de Windows Phone et des applications du Windows 8. x Store.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Le projet de bibliothèque de classes portables ne met à la disposition de votre application qu’un sous-ensemble très limité des types de l' <xref:System.Resources> espace de noms, mais vous permet d’utiliser la <xref:System.Resources.ResourceManager> classe pour récupérer des ressources. Toutefois, si vous créez une application à l'aide de Visual Studio, vous devez utiliser le wrapper fortement typé créé par Visual Studio, plutôt que d'utiliser directement la classe <xref:System.Resources.ResourceManager>.

 Pour créer un wrapper fortement typé dans Visual Studio, définissez le **modificateur d’accès** du fichier de ressources principal dans le concepteur de ressources de Visual Studio sur **public**. Cela crée un fichier [resourceFileName].designer.cs ou [resourceFileName].designer.vb qui contient le wrapper fortement typé ResourceManager. Pour plus d’informations sur l’utilisation d’un wrapper de ressources fortement typé, consultez la section « génération d’une classe de ressource fortement typée » dans la rubrique [Resgen.exe (Resource File Generator)](../../framework/tools/resgen-exe-resource-file-generator.md) .

## <a name="resource-manager-in-the-portable-class-library"></a>Gestionnaire des ressources dans la bibliothèque de classes portables

 Dans un projet de bibliothèque de classes portables, tout accès aux ressources est géré par la <xref:System.Resources.ResourceManager> classe. Étant donné que les types dans l' <xref:System.Resources> espace de noms, tels que <xref:System.Resources.ResourceReader> et <xref:System.Resources.ResourceSet> , ne sont pas accessibles à partir d’un projet de bibliothèque de classes portables, ils ne peuvent pas être utilisés pour accéder aux ressources.

 Le projet de bibliothèque de classes portable comprend les quatre <xref:System.Resources.ResourceManager> membres listés dans le tableau suivant. Ces constructeurs et méthodes vous permettent d'instancier un objet <xref:System.Resources.ResourceManager> et d'extraire des ressources de chaîne.

|Membre`ResourceManager`|Description|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Créé une instance <xref:System.Resources.ResourceManager> pour accéder au fichier de ressources nommé trouvé dans l'assembly spécifié.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Créé une instance <xref:System.Resources.ResourceManager> qui correspond au type spécifié.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Extrait une ressource nommée pour la culture actuelle.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Extrait une ressource nommée appartenant à la culture spécifiée.|

 L’exclusion d’autres <xref:System.Resources.ResourceManager> membres de la bibliothèque de classes portables signifie que les objets sérialisés, les données qui ne sont pas des chaînes et les images ne peuvent pas être récupérés à partir d’un fichier de ressources. Pour utiliser des ressources d’une bibliothèque de classes portables, vous devez stocker toutes les données d’objet sous forme de chaîne. Par exemple, vous pouvez stocker des valeurs numériques dans un fichier de ressources en les convertissant en chaînes, et les extraire, puis, vous pouvez les reconvertir en nombres à l'aide de la méthode `Parse` ou `TryParse` du type de données numériques. Vous pouvez convertir des images ou autres données binaires en représentation sous forme de chaîne en appelant la méthode <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>, et les restaurer en un tableau d'octets en appelant la méthode <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>La bibliothèque de classes portable et les applications du Windows Store

 Les projets de bibliothèque de classes portables stockent des ressources dans des fichiers. resx, qui sont ensuite compilés dans des fichiers. Resources et incorporés dans l’assembly principal ou dans des assemblys satellites au moment de la compilation. Les applications du Windows 8. x Store, en revanche, requièrent que les ressources soient stockées dans des fichiers. resw, qui sont ensuite compilés dans un seul fichier d’index de ressources de package (PRI). Toutefois, en dépit des formats de fichiers incompatibles, votre bibliothèque de classes portable fonctionnera dans une application Windows 8. x Store.

 Pour utiliser votre bibliothèque de classes à partir d’une application Windows 8. x Store, ajoutez une référence à celle-ci dans votre projet d’application Windows Store. Visual Studio extraira en toute transparence les ressources de votre assembly dans un fichier. resw et l’utilisera pour générer un fichier PRI à partir duquel l’Windows Runtime peut extraire des ressources. Au moment de l’exécution, le Windows Runtime exécute le code dans votre bibliothèque de classes portable, mais récupère les ressources de votre bibliothèque de classes portable à partir du fichier PRI.

 Si votre projet de bibliothèque de classes portables comprend des ressources localisées, vous utilisez le modèle Hub-and-spoke pour les déployer de la même façon que pour une bibliothèque dans une application de bureau. Pour utiliser votre fichier de ressources principal et tous les fichiers de ressources localisés dans votre application Windows 8. x Store, vous ajoutez une référence à l’assembly principal. Au moment de la compilation, Visual Studio extrait les ressources à partir du fichier de ressources principal et de tous les fichiers de ressources localisés dans des fichiers .resw distincts. Il compile ensuite les fichiers. resw en un seul fichier PRI auquel le Windows Runtime accède au moment de l’exécution.

<a name="NonLoc"></a>

## <a name="example-non-localized-portable-class-library"></a>Exemple : bibliothèque de classes portable non localisée

 L’exemple de bibliothèque de classes portable simple non localisé suivant utilise des ressources pour stocker les noms des colonnes et pour déterminer le nombre de caractères à réserver pour les données tabulaires. L'exemple utilise un fichier nommé LibResources.resx pour stocker les ressources de chaîne répertoriées dans le tableau suivant.

|Nom de la ressource|Valeur de la ressource|
|-------------------|--------------------|
|Né le|Date de naissance|
|BornLength|12|
|Embauché|Date d'embauche|
|HiredLength|12|
|id|id|
|ID.Length|12|
|Nom|Nom|
|NameLength|25|
|Titre|Base de données des employés|

 Le code suivant définit une `UILibrary` classe qui utilise le wrapper gestionnaire des ressources nommé `resources` généré par Visual Studio lorsque le **modificateur d’accès** pour le fichier devient **public**. La classe UILibrary analyse les données de chaîne selon les besoins. . Notez que la classe est dans l'espace de noms `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console. Elle requiert une référence à UILibrary.dll pour être ajoutée au projet d’application console.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Le code suivant illustre comment `UILibrary` accéder à la classe et à ses ressources à partir d’une application Windows 8. x Store. Elle requiert une référence à UILibrary.dll pour être ajoutée au projet d’application du Windows Store.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Exemple : bibliothèque de classes portable localisée

 L’exemple de bibliothèque de classes portable localisée suivant comprend des ressources pour les cultures français (France) et anglais (États-Unis). La culture anglais (États-Unis) est la culture par défaut de l’application ; ses ressources sont indiquées dans le tableau de la [section précédente](app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Le fichier de ressources de la culture française (France) est nommé LibResources.fr-FR.resx et inclut les ressources de type de chaîne répertoriées dans le tableau suivant. Le code source de la classe `UILibrary` est identique que celui présenté dans la section précédente.

|Nom de la ressource|Valeur de la ressource|
|-------------------|--------------------|
|Né le|Date de naissance|
|BornLength|20|
|Embauché|Date d'embauche|
|HiredLength|16|
|id|id|
|Nom|Nom|
|Titre|Base de données des employés|

 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console. Elle requiert une référence à UILibrary.dll pour être ajoutée au projet d’application console.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Le code suivant illustre comment `UILibrary` accéder à la classe et à ses ressources à partir d’une application Windows 8. x Store. Elle requiert une référence à UILibrary.dll pour être ajoutée au projet d’application du Windows Store. Il utilise la propriété statique `ApplicationLanguages.PrimaryLanguageOverride` pour définir la langue par défaut sur Français.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager>
- [Ressources dans les applications de bureau](../../framework/resources/index.md)
- [Empaquetage et déploiement de ressources](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
