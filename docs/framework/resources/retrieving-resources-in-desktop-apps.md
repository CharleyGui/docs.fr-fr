---
title: Récupération de ressources dans des applications de bureau
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
ms.openlocfilehash: 17795db2cdec419a31fe862793c88506f9535ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180449"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Récupération de ressources dans des applications de bureau

Quand vous utilisez des ressources localisées dans des applications de bureau du .NET Framework, vous devez, dans l’idéal, empaqueter les ressources pour la culture neutre ou par défaut avec l’assembly principal et créer un assembly satellite séparé pour chaque langue ou culture prise en charge par votre application. Vous pouvez ensuite utiliser la classe <xref:System.Resources.ResourceManager> pour accéder aux ressources nommées, comme indiqué dans la section suivante. Si vous choisissez de ne pas incorporer les ressources dans l’assembly principal et les assemblys satellites, vous pouvez également accéder directement aux fichiers .resources binaires, comme cela est expliqué dans la section [Récupération de ressources de fichiers .resources](#from_file), plus loin dans cet article.  Pour récupérer des ressources dans les applications Windows 8.x Store, voir [Créer et récupérer des ressources dans les applications Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140)).  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Récupération de ressources d’assemblys  
 La classe <xref:System.Resources.ResourceManager> fournit l’accès aux ressources au moment de l’exécution. Utilisez la méthode <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> pour récupérer des ressources de type chaîne et la méthode <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> ou <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> pour récupérer des ressources d’un autre type. Chaque méthode a deux surcharges :  
  
- Une surcharge dont le paramètre unique est une chaîne qui contient le nom de la ressource. La méthode tente de récupérer cette ressource pour la culture du thread actuel. Pour plus d’informations, consultez les méthodes <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>et <xref:System.Resources.ResourceManager.GetStream%28System.String%29> .  
  
- Une surcharge qui a deux paramètres : une chaîne contenant le nom de la ressource, et un objet <xref:System.Globalization.CultureInfo> représentant la culture pour laquelle la ressource doit être récupérée. Si une ressource définie pour cette culture est introuvable, le Gestionnaire des ressources utilise des règles de secours pour récupérer une ressource appropriée. Pour plus d’informations, consultez les méthodes <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>et <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> .  
  
 Le Gestionnaire des ressources utilise le processus de secours pour les ressources pour déterminer de quelle manière l’application récupère les ressources spécifiques de la culture. Pour plus d’informations, consultez la section « Processus de secours pour les ressources » dans [Empaquetage et déploiement de ressources](packaging-and-deploying-resources-in-desktop-apps.md). Pour plus d’informations sur l’instanciation d’un objet <xref:System.Resources.ResourceManager> , consultez la section « Instanciation d’un objet ResourceManager » dans la rubrique de la classe <xref:System.Resources.ResourceManager> .  
  
### <a name="retrieving-string-data-an-example"></a>Récupération de données de chaîne : exemple  
 L’exemple suivant appelle la méthode <xref:System.Resources.ResourceManager.GetString%28System.String%29> pour récupérer les ressources de type chaîne de la culture d’interface utilisateur actuelle. Il inclut une ressource de chaîne neutre pour la culture Anglais (États-Unis), et les ressources localisées pour les cultures Français (France) et Russe (Russie). La ressource Anglais (États-Unis) suivante se trouve dans un fichier nommé Strings.txt :  
  
```text
TimeHeader=The current time is  
```  
  
 La ressource Français (France) se trouve dans un fichier nommé Strings.fr-FR.txt :  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 La ressource Russe (Russie) se trouve dans un fichier nommé Strings.ru-RU-txt :  
  
```text
TimeHeader=Текущее время —  
```  
  
 Le code source de cet exemple provient d’un fichier GetString.cs pour la version C# du code et d’un fichier GetString.vb pour la version Visual Basic. Ce code définit un tableau de chaînes qui contient le nom de quatre cultures : les trois cultures pour lesquelles des ressources sont disponibles et la culture Espagnol (Espagne). Une boucle exécutée cinq fois de façon aléatoire sélectionne l’une de ces cultures et l’affecte aux propriétés <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> . Elle appelle ensuite la méthode <xref:System.Resources.ResourceManager.GetString%28System.String%29> pour récupérer la chaîne localisée, qui s’affiche avec l’heure actuelle.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Le fichier de commandes (.bat) ci-dessous compile l’exemple et génère des assemblys satellites dans les répertoires appropriés. Les commandes indiquées s’appliquent au langage et au compilateur C#. Pour Visual Basic, remplacez `csc` par `vbc`, et `GetString.cs` par `GetString.vb`.  
  
```console
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Quand la culture d’interface utilisateur actuelle est Espagnol (Espagne), l’exemple affiche les ressources en langue anglaise, car les ressources pour l’espagnol ne sont pas disponibles et l’anglais est la culture par défaut définie dans cet exemple.  
  
### <a name="retrieving-object-data-two-examples"></a>Récupération de données d’objet : deux exemples  
 Vous pouvez utiliser les méthodes <xref:System.Resources.ResourceManager.GetObject%2A> et <xref:System.Resources.ResourceManager.GetStream%2A> pour récupérer des données d’objet. Cela inclut les types de données primitives, les objets sérialisables et les objets qui sont stockés au format binaire (tels que les images).  
  
 L’exemple suivant utilise la méthode <xref:System.Resources.ResourceManager.GetStream%28System.String%29> pour récupérer une image bitmap qui s’affiche dans la fenêtre de démarrage à l’ouverture d’une application. Le code source ci-dessous provient d’un fichier nommé CreateResources.cs (pour C#) ou CreateResources.vb (pour Visual Basic). Ce code crée un fichier .resx qui contient l’image sérialisée. Dans cet exemple, l’image est chargée à partir d’un fichier SplashScreen.jpg. Vous pouvez remplacer ce nom de fichier par votre image.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Le code suivant récupère la ressource et affiche l’image dans un contrôle <xref:System.Windows.Forms.PictureBox>.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Vous pouvez utiliser le fichier de commandes suivant pour générer l’exemple C#. Pour Visual Basic, remplacez `csc` par `vbc`, et modifiez l’extension du fichier de code source `.cs` en `.vb`.  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 L’exemple suivant utilise la méthode <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> pour désérialiser un objet personnalisé. Il inclut un fichier de code source UIElements.cs (UIElements.vb pour Visual Basic) qui définit la structure suivante nommée `PersonTable`. Cette structure est ensuite utilisée par une routine d’affichage de table générale qui affiche les noms localisés des colonnes de table. Notez que la structure `PersonTable` est marquée avec l’attribut <xref:System.SerializableAttribute> .  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Le code ci-dessous provient d’un fichier CreateResources.cs (CreateResources.vb pour Visual Basic). Il crée un fichier de ressources XML nommé UIResources.resx qui stocke un titre de table ainsi qu’un objet `PersonTable` qui contient des informations relatives à une application localisée en anglais.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Le code suivant, qui provient d’un fichier de code source nommé GetObject.cs (ou GetObject.vb), récupère ensuite les ressources et les affiche dans la console.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Vous pouvez créer le fichier et les assemblys de ressources nécessaires, puis lancer l’application en exécutant le fichier de commandes suivant. Vous devez utiliser l’option `/r` pour fournir à Resgen.exe une référence à UIElements.dll qui lui permet d’accéder aux informations relatives à la structure `PersonTable` . Si vous utilisez C#, remplacez le nom du compilateur `vbc` par `csc`et modifiez l’extension `.vb` en `.cs`.  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Prise en charge du contrôle de version pour les assemblys satellites  
 Par défaut, quand l’objet <xref:System.Resources.ResourceManager> récupère les ressources demandées, il recherche les assemblys satellites dont les numéros de version correspondent au numéro de version de l’assembly principal. Après avoir déployé une application, vous pouvez avoir besoin de mettre à jour l’assembly principal ou des assemblys satellites de ressources spécifiques. .NET Framework prend en charge le contrôle de version pour l’assembly principal et les assemblys satellites.  
  
 L’attribut <xref:System.Resources.SatelliteContractVersionAttribute> fournit la prise en charge du contrôle de version pour un assembly principal. Spécifiez cet attribut sur l’assembly principal d’une application si vous voulez mettre à jour et redéployer un assembly principal sans mettre à jour ses assemblys satellites. Après avoir mis à jour l’assembly principal, incrémentez son numéro de version, mais ne modifiez pas le numéro de version de contrat satellite. Quand le Gestionnaire des ressources récupère les ressources demandées, il charge la version d’assembly satellite spécifiée par cet attribut.  
  
 Les assemblys de stratégie de serveur de publication prennent en charge le contrôle de version pour les assemblys satellites. Vous pouvez mettre à jour et redéployer un assembly satellite sans avoir à mettre à jour l’assembly principal. Après la mise à jour d’un assembly satellite, incrémentez son numéro de version et distribuez-le avec un assembly de stratégie de serveur de publication. Dans l’assembly de stratégie de serveur de publication, spécifiez que votre nouvel assembly satellite offre une compatibilité descendante avec sa version précédente. Le Gestionnaire des ressources utilise l’attribut <xref:System.Resources.SatelliteContractVersionAttribute> pour déterminer la version de l’assembly satellite, mais le chargeur d’assembly établit une liaison à la version d’assembly satellite spécifiée par la stratégie de serveur de publication. Pour plus d’informations sur les assemblys de stratégie de serveur de publication, consultez [Création d’un fichier de stratégie de serveur de publication](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Pour garantir une prise en charge totale du contrôle de version des assemblys, nous vous recommandons de déployer les assemblys avec nom fort dans le [GAC](../app-domains/gac.md) et de déployer les assemblys sans nom fort dans le répertoire de l’application. Si vous déployez des assemblys avec nom fort dans le répertoire de l’application, vous ne pourrez pas incrémenter le numéro de version d’un assembly satellite lors de la mise à jour de l’assembly principal. Au lieu de cela, vous devez effectuer une mise à jour sur place où vous remplacez le code existant par le code mis à jour et conservez le même numéro de version. Par exemple, si vous souhaitez mettre à jour la version 1.0.0.0 d’un assembly satellite avec le nom d’assembly spécifié entièrement (« myApp.resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a »), remplacez-le par le fichier myApp.resources.dll mis à jour qui a été compilé avec le même nom d’assembly spécifié entièrement (« myApp.resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a »). Notez que, si vous faites des mises à jour sur place dans les fichiers d’assembly satellite, il est difficile pour une application de déterminer la version exacte d’un assembly satellite.  
  
 Pour plus d’informations sur le contrôle de version des assemblys, consultez [Versioning des assemblys](../../standard/assembly/versioning.md) et [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>Récupération de ressources de fichiers .resources  
 Si vous choisissez de ne pas déployer de ressources dans des assemblys satellites, vous pouvez utiliser un objet <xref:System.Resources.ResourceManager> pour accéder directement aux ressources des fichiers .resources. Pour ce faire, vous devez déployer les fichiers .resources correctement. Ensuite, utilisez la méthode <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> pour instancier un objet <xref:System.Resources.ResourceManager> et spécifiez le répertoire qui contient les fichiers .resources autonomes.  
  
### <a name="deploying-resources-files"></a>Déploiement de fichiers .resources  
 Quand vous incorporez des fichiers .resources dans un assembly d’application et des assemblys satellites, chaque assembly satellite porte le même nom de fichier, mais est placé dans un sous-répertoire qui reflète la culture de l’assembly satellite. En revanche, quand vous accédez directement aux ressources de fichiers .resources, vous pouvez placer tous les fichiers .resources dans le même répertoire, généralement un sous-répertoire du répertoire de l’application. Le nom du fichier .resources par défaut de l’application se compose uniquement d’un nom racine, sans indication de sa culture (par exemple, strings.resources). Les ressources de chaque culture localisée sont stockées dans un fichier dont le nom se compose du nom racine suivi de la culture (par exemple, strings.ja.resources ou strings.de-DE.resources).

 L’illustration suivante montre où placer les fichiers de ressources dans la structure de répertoires. Elle donne également les conventions de nommage des fichiers .resource.  

 ![Illustration qui montre le répertoire principal de votre application.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Utilisation du Gestionnaire des ressources  
 Une fois que vous avez créé vos ressources et les avez placées dans le répertoire approprié, créez un objet <xref:System.Resources.ResourceManager> qui utilise ces ressources en appelant la méthode <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> . Le premier paramètre spécifie le nom racine du fichier .resources par défaut de l’application (« strings » dans l’exemple de la section précédente). Le deuxième paramètre spécifie l’emplacement des ressources (« Resources » dans l’exemple précédent). Le troisième paramètre spécifie l’implémentation de <xref:System.Resources.ResourceSet> à utiliser. Si ce paramètre est `null`, le runtime par défaut <xref:System.Resources.ResourceSet> est utilisé.  
  
> [!NOTE]
> Ne déployez pas d’applications ASP.NET à l’aide de fichiers .resources autonomes, car cela peut entraîner des problèmes de verrouillage et l’arrêt du déploiement XCOPY. Nous vous recommandons de déployer les ressources ASP.NET dans des assemblys satellites. Pour plus d’informations, consultez [Vue d’ensemble des ressources des pages Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Après avoir instancié l’objet <xref:System.Resources.ResourceManager> , utilisez les méthodes <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>et <xref:System.Resources.ResourceManager.GetStream%2A> pour récupérer les ressources, comme indiqué plus haut. Toutefois, la récupération de ressources directement à partir des fichiers .resources s’effectue différemment de la récupération des ressources incorporées à partir d’assemblys. Quand vous récupérez des ressources de fichiers .resources, les méthodes <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>et <xref:System.Resources.ResourceManager.GetStream%28System.String%29> récupèrent toujours les ressources de la culture par défaut, quelle que soit la culture actuelle. Pour récupérer les ressources de la culture actuelle de l’application ou d’une autre culture, vous devez appeler la méthode <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>ou <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> et spécifier la culture pour laquelle les ressources doivent être récupérées. Pour récupérer les ressources de la culture actuelle, spécifiez la valeur de la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> comme argument `culture` . Si le Gestionnaire des ressources ne peut pas récupérer les ressources de `culture`, il récupère les ressources appropriées à l’aide des règles de secours standard pour les ressources.  
  
### <a name="an-example"></a>Exemple  
 L’exemple suivant montre comment le Gestionnaire des ressources récupère les ressources directement des fichiers .resources. Il utilise trois fichiers de ressources texte pour les cultures Anglais (États-Unis), Français (France) et Russe (Russie). La culture Anglais (États-Unis) est la culture par défaut utilisée dans cet exemple. Ses ressources sont stockées dans le fichier Strings.txt suivant :  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Les ressources pour la culture Français (France) sont stockées dans le fichier suivant, nommé Strings.fr-FR.txt :  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Les ressources pour la culture Russe (Russie) sont stockées dans le fichier suivant, nommé Strings.ru-RU.txt :  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Voici le code source de l'exemple. L’exemple instancie les objets <xref:System.Globalization.CultureInfo> pour les cultures Anglais (États-Unis), Anglais (Canada), Français (France) et Russe (Russie), et définit chacune d’elles comme culture actuelle. La méthode <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> fournit ensuite la valeur de la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> comme argument `culture` pour récupérer les ressources appropriées de la culture.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Vous pouvez compiler la version C# de l’exemple en exécutant le fichier de commandes suivant. Si vous utilisez Visual Basic, remplacez `csc` par `vbc` et modifiez l’extension `.cs` en `.vb`.  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager>
- [Ressources dans des applications de bureau](index.md)
- [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Création et récupération de ressources dans les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))
