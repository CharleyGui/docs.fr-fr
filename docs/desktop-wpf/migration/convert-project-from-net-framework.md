---
title: Migrer WPF Apps à .NET Core 3.0
description: Apprenez à migrer une application de la Windows Presentation Foundation (WPF) vers .NET Core 3.0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071310"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrer les applications WPF à .NET Core

Cet article couvre les étapes nécessaires pour migrer une application de la Fondation de présentation Windows (WPF) de .NET Framework à .NET Core 3.0. Si vous n’avez pas d’application WPF à portée de main pour le port, mais que vous souhaitez essayer le processus, vous pouvez utiliser **l’application d’échantillon Bean Trader** disponible sur [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). L’application originale (ciblant .NET Framework 4.7.2) est disponible dans le dossier NetFx-BeanTraderClient. Tout d’abord, nous allons expliquer les étapes nécessaires pour les applications portuaires en général, puis nous allons marcher à travers les modifications spécifiques qui s’appliquent à **l’échantillon Bean Trader.**

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Pour migrer vers .NET Core, vous devez d’abord :

01. Comprendre et mettre à jour les dépendances de NuGet :

    01. Améliorer les dépendances NuGet `<PackageReference>` pour utiliser le format.
    01. Examinez les dépendances NuGet de haut niveau pour la compatibilité .NET Core ou .NET Standard.
    01. Mettre à niveau les forfaits NuGet vers de nouvelles versions.
    01. Utilisez [l’analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour comprendre les dépendances .NET.

01. Migrez le fichier du projet vers le nouveau format de style SDK :

    01. Choisissez de cibler à la fois .NET Core et .NET Framework, ou seulement .NET Core.
    01. Copiez les propriétés et les éléments pertinents du fichier de projet au nouveau fichier de projet.

01. Résoudre les problèmes de construction :

    01. Ajoutez une référence au package [Microsoft.Windows.Compatibility.](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)
    01. Trouver et corriger les différences au niveau de l’API.
    01. Supprimer les sections *app.config* autres que `appSettings` ou `connectionStrings`.
    01. Régénérer le code généré, si nécessaire.

01. Test de temps d’exécution :

    01. Confirmez que l’application porte comme prévu.
    01. Méfiez-vous des <xref:System.NotSupportedException> exceptions.

## <a name="about-the-sample"></a>À propos de l’exemple

Cet article fait référence à [l’application d’échantillon Bean Trader](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) parce qu’elle utilise une variété de dépendances similaires à celles que les applications WPF du monde réel pourraient avoir. L’application n’est pas grande, mais est censé être un pas en avant de «Hello World» en termes de complexité. L’application démontre certains problèmes que les utilisateurs peuvent rencontrer tout en transférant de vraies applications. L’application communique avec un service WCF, donc pour qu’il s’exécute correctement, vous aurez également besoin d’exécuter le projet BeanTraderServer (disponible dans le même référentiel GitHub) et assurez-vous que la configuration BeanTraderClient points au point de terminaison correct. (Par défaut, l’échantillon suppose que le serveur *http://localhost:8090*fonctionne sur la même machine à , ce qui sera vrai si vous lancez BeanTraderServer localement.)

Gardez à l’esprit que cette application d’échantillon est destinée à démontrer les défis et les solutions de portage .NET Core. Il n’est pas destiné à démontrer les meilleures pratiques WPF. En fait, il comprend délibérément quelques anti-modèles pour s’assurer que vous rencontrez au moins un couple de défis intéressants tout en portant.

## <a name="getting-ready"></a>Préparation

Le principal défi de la migration d’une application cadre .NET à .NET Core est que ses dépendances peuvent fonctionner différemment ou pas du tout. La migration est beaucoup plus facile qu’elle ne l’était; de nombreux paquets NuGet ciblent désormais .NET Standard. À partir de .NET Core 2.0, le cadre .NET et les surfaces de base .NET sont devenus similaires. Malgré cela, certaines différences (à la fois dans le soutien des paquets NuGet et dans les API .NET disponibles) restent. La première étape dans la migration est de revoir les dépendances de l’application et de s’assurer que les références sont dans un format qui est facilement migré vers .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Mise `<PackageReference>` à niveau vers les références NuGet

Les anciens projets cadre .NET énumèrent généralement leurs dépendances NuGet dans un fichier *packages.config.* Le nouveau format de fichier de projet de [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) style SDK fait référence aux paquets NuGet comme éléments dans le fichier csproj lui-même plutôt que dans un fichier config distinct.

Lors de la migration, il ya `<PackageReference>`deux avantages à l’aide de références de style:

- C’est le style de référence NuGet qui est nécessaire pour le nouveau fichier de projet .NET Core. Si vous utilisez `<PackageReference>`déjà, ces éléments de fichiers de projet peuvent être copiés et collés directement dans le nouveau projet.
- Contrairement à un fichier `<PackageReference>` packages.config, les éléments ne se réfèrent qu’aux dépendances de haut niveau dont votre projet dépend directement. Tous les autres paquets NuGet transitifs seront déterminés au moment de la restauration et enregistrés dans le fichier autogenerated obj-project.assets.json. Il est donc beaucoup plus facile de déterminer les dépendances de votre projet, ce qui est utile pour déterminer si les dépendances nécessaires fonctionneront sur .NET Core ou non.

La première étape pour migrer une application cadre .NET à `<PackageReference>` .NET Core est de le mettre à jour pour utiliser des références NuGet. Visual Studio rend cela simple. Il suffit de cliquer à droite le fichier *packages.config* du projet dans Visual Studio **Solution Explorer**, puis sélectionnez **Paquets Migrate.config à PackageReference**.

![Mise à niveau vers PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Un dialogue apparaît montrant les dépendances NuGet calculées de haut niveau et demandant quels autres paquets NuGet devraient être promus au plus haut niveau. Aucun de ces autres paquets doivent être de haut niveau pour l’échantillon Bean Trader, de sorte que vous pouvez décocher toutes ces boîtes. Ensuite, cliquez sur **Ok** et le fichier `<PackageReference>` *packages.config* est supprimé et des éléments sont ajoutés au fichier du projet.

`<PackageReference>`Les références de style ne stockent pas les paquets NuGet localement dans un dossier de paquets. Au lieu de cela, ils sont stockés dans le monde entier comme une optimisation. Après la migration se termine, modifier le fichier `<Analyzer>` csproj et supprimer tous les éléments se référant aux analyseurs qui provenaient auparavant de la *.. Répertoire de paquets.* Ne vous inquiétez pas; puisque vous avez toujours les références de paquet NuGet, les analyseurs seront inclus dans le projet. Vous avez juste besoin de nettoyer les `<Analyzer>` anciens paquets.config-modèle éléments.

### <a name="review-nuget-packages"></a>Publier un avis sur les forfaits NuGet

Maintenant que vous pouvez voir les paquets NuGet de haut niveau dont dépend le projet, vous pouvez examiner si ces paquets sont disponibles sur .NET Core. Vous pouvez déterminer si un paquet prend en charge .NET Core en examinant ses dépendances sur [nuget.org](https://www.nuget.org/). Le site [fuget.org](https://www.fuget.org/) créé par la communauté montre cette information en bonne place en haut de la page d’information sur les colis.

Lors du ciblage .NET Core 3.0, tous les paquets ciblant .NET Core ou .NET Standard doivent fonctionner (puisque .NET Core implémente la surface standard .NET). Dans certains cas, la version spécifique d’un paquet utilisé ne ciblera pas .NET Core ou .NET Standard, mais les versions plus nouvelles le feront. Dans ce cas, vous devriez envisager de passer à la dernière version du paquet.

Vous pouvez utiliser des paquets ciblant .NET Framework, ainsi, mais qui introduit un certain risque. .NET Core to .NET Les dépendances du Cadre sont autorisées parce que les surfaces .NET Core et .NET Framework sont assez semblables pour que ces dépendances fonctionnent *souvent.* Toutefois, si le paquet tente d’utiliser un API .NET qui n’est pas présent dans .NET Core, vous rencontrerez une exception de temps d’exécution. Pour cette raison, vous ne devez référence .NET paquets cadre quand aucune autre option n’est disponible et de comprendre que cela impose un fardeau de test.

S’il existe des paquets référencés qui ne ciblent pas .NET Core ou .NET Standard, vous devrez penser à d’autres alternatives :

- Y a-t-il d’autres paquets similaires qui peuvent être utilisés à la place? Parfois, les auteurs de NuGet publient séparément '. Les versions de base de leurs bibliothèques ciblant spécifiquement .NET Core. Les forfaits Bibliothèque d’entreprise sont un exemple de l’édition communautaire " . NetCore" alternatives. Dans d’autres cas, de nouveaux SDK pour un service particulier (parfois avec des noms de forfaits différents) sont disponibles pour .NET Standard. Si aucune alternative n’est disponible, vous pouvez procéder à l’aide des paquets .NET Framework-targeted, en gardant à l’esprit que vous aurez besoin de les tester à fond une fois en cours d’exécution sur .NET Core.

L’échantillon Bean Trader a les dépendances NuGet de haut niveau suivantes :

- [**Castle.Windsor, version 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Ce paquet cible .NET Standard 1.6, de sorte qu’il fonctionne sur .NET Core.

- [**Microsoft.CodeAnalysis.FxCopAnalyzers, version 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Il s’agit d’un méta-package, il n’est donc pas immédiatement évident quelles plates-formes il prend en charge, mais [la documentation](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) indique que sa version la plus récente (2.9.2) fonctionnera à la fois pour .NET Framework et .NET Core.

- [**Nito.AsyncEx, version 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Ce paquet ne cible pas .NET Core, mais la version 5.0 la plus récente le fait. Ceci est commun lors de la migration parce que de nombreux paquets NuGet ont ajouté .NET Standard support récemment, mais les versions plus anciennes du projet ne cibleront .NET Framework. Si la différence de version n’est qu’une différence de version mineure, il est souvent facile de mettre à niveau vers la version plus récente. Parce qu’il s’agit d’un changement de version majeur, vous devez être prudent mise à niveau car il pourrait y avoir des changements de rupture dans le paquet. Il y a cependant une voie à suivre, ce qui est bien.

- [**MahApps.Metro, version 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Ce paquet ne cible pas non plus .NET Core, mais a une nouvelle pré-version (2.0-alpha) qui le fait. Encore une fois, vous devez faire attention aux changements de rupture, mais le nouveau paquet est encourageant.

Les dépendances NuGet de l’échantillon De Bean Trader sont toutes ciblées .NET Standard/.NET Core ou ont de nouvelles versions qui le font, il est donc peu probable qu’il y ait des problèmes de blocage ici.

### <a name="upgrade-nuget-packages"></a>Améliorer les forfaits NuGet

Si possible, il serait bon de mettre à niveau les versions de tous les paquets qui ciblent seulement .NET Core ou .NET Standard avec des versions plus récentes à ce stade (avec le projet toujours ciblant .NET Framework) pour découvrir et aborder tout changement de rupture au début.

Si vous préférez ne pas apporter de modifications matérielles à la version cadre .NET existante de l’application, cela peut attendre jusqu’à ce que vous ayez un nouveau fichier de projet ciblant .NET Core. Cependant, la mise à niveau des paquets NuGet en versions compatibles .NET Core à l’avance rend le processus de migration encore plus facile une fois que vous créez le nouveau fichier de projet et réduit le nombre de différences entre le cadre .NET et les versions .NET Core de l’application.

Avec l’échantillon Bean Trader, toutes les mises à niveau nécessaires peuvent être effectuées facilement (en utilisant le gestionnaire de forfaits NuGet de Visual Studio) à une exception près : la mise à niveau de **MahApps.Metro 1.6.5** à **2.0** révèle des changements de rupture liés aux API de gestion des thèmes et des accents.

Idéalement, l’application serait mise à jour pour utiliser la nouvelle version du paquet (puisque c’est plus susceptible de fonctionner sur .NET Core). Dans certains cas, cependant, cela peut ne pas être faisable. Dans ces cas, ne pas mettre à niveau **MahApps.Metro** parce que les changements nécessaires sont non-trivial et ce tutoriel se concentre sur la migration vers .NET Core 3, pas à **MahApps.Metro 2.** En outre, il s’agit d’une dépendance à faible risque .NET Framework parce que l’application Bean Trader exerce seulement une petite partie de **MahApps.Metro**. Il faudra, bien sûr, des tests pour s’assurer que tout fonctionne une fois la migration terminée. S’il s’agissait d’un scénario réel, il serait bon de déposer un problème pour suivre le travail de passer à **MahApps.Metro** version 2.0 puisque ne pas faire la migration laisse maintenant derrière lui une certaine dette technique.

Une fois que les paquets NuGet `<PackageReference>` sont mis à jour sur des versions récentes, le groupe d’éléments dans le fichier de projet de l’échantillon Bean Trader devrait ressembler à ceci.

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET Analyse de la portabilité du Cadre

Une fois que vous comprenez l’état des dépendances NuGet de votre projet, la prochaine chose à considérer est .NET Framework API dépendances. [L’outil .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) est utile pour comprendre lequel des API .NET que votre projet utilise sont disponibles sur d’autres plates-formes .NET.

L’outil est livré comme un [plugin Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), un [outil de commande-ligne](https://github.com/Microsoft/dotnet-apiport/releases), ou enveloppé dans une [interface graphique simple](https://github.com/Microsoft/dotnet-apiport-ui), qui simplifie ses options. Vous pouvez en savoir plus sur l’utilisation de l’analyseur de portabilité .NET (API Port) en utilisant l’interface utilisateur dans les [applications de bureau Porting pour .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) blog post. Si vous préférez utiliser la ligne de commande, les étapes nécessaires sont les suivantes :

1. Téléchargez [l’analyseur de portabilité .NET](https://github.com/Microsoft/dotnet-apiport/releases) si vous ne l’avez pas déjà.
1. Assurez-vous que l’application cadre .NET à porter construit avec succès (c’est une bonne idée avant la migration indépendamment).
1. Exécuter API Port avec une ligne de commande comme celle-ci.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    L’argument `-f` précise le chemin contenant les binaires à analyser. L’argument `-r` précise le format de fichier de sortie que vous voulez. L’argument `-t` spécifie quelle plate-forme .NET pour analyser l’utilisation de l’API contre. Dans ce cas, vous voulez .NET Core.

Lorsque vous ouvrez le rapport HTML, la première section répertorie tous les binaires analysés et quel pourcentage des API .NET qu’ils utilisent sont disponibles sur la plate-forme ciblée. Le pourcentage n’est pas significatif en soi. Ce qui est plus utile est de voir les API spécifiques qui manquent. Pour ce faire, sélectionnez un nom d’assemblage ou faites défiler vers le bas vers les rapports pour les assemblages individuels.

Concentrez-vous sur les assemblages pour lequel vous possédez le code source. Dans le rapport Bean Trader ApiPort, par exemple, il existe de nombreux binaires répertoriés, mais la plupart d’entre eux appartiennent à des paquets NuGet. `Castle.Windsor`montre que cela dépend de certains API System.Web qui manquent dans .NET Core. Ce n’est pas une préoccupation `Castle.Windsor` parce que vous avez déjà vérifié que prend en charge .NET Core. Il est courant pour les paquets NuGet d’avoir différents binaires pour une `Castle.Windsor` utilisation avec différentes plates-formes .NET, donc si la version cadre .NET des utilisations System.Web API ou non n’est pas pertinente tant que le paquet cible également .NET Standard ou .NET Core (ce qu’il fait).

Avec l’échantillon Bean Trader, le seul binaire que vous devez considérer est **BeanTraderClient** et `System.ServiceModel.ClientBase<T>.Close` `System.ServiceModel.ClientBase<T>.Open`le rapport montre que seulement deux API .NET sont manquants: et .

![Rapport sur la portabilité de BeanTraderClient](./media/convert-project-from-net-framework/portability-report.png)

Il est peu probable qu’il bloque les problèmes parce que les API clients de la WCF sont (principalement) prises en charge sur .NET Core, il doit donc y avoir des alternatives disponibles pour ces API centrales. En fait, `System.ServiceModel`en regardant la surface de <https://apisof.net>base de .NET (en utilisant ), vous voyez qu’il ya des alternatives async dans .NET Core à la place.

Sur la base de ce rapport et de l’analyse précédente de la dépendance NuGet, il semble qu’il ne devrait pas y avoir de problèmes majeurs de migration de l’échantillon De Bean Trader à .NET Core. Vous êtes prêt pour la prochaine étape dans laquelle vous allez réellement commencer la migration.

## <a name="migrating-the-project-file"></a>Migration du fichier projet

Si votre application n’utilise pas le nouveau [format de fichier de projet de style SDK,](../../core/tools/csproj.md)vous aurez besoin d’un nouveau fichier de projet pour cibler .NET Core. Vous pouvez remplacer le fichier csproj existant ou, si vous préférez garder le projet existant intact dans son état actuel, vous pouvez ajouter un nouveau fichier csproj ciblant .NET Core. Vous pouvez créer des versions de l’application pour .NET Framework et .NET Core avec un `<TargetFrameworks>` seul fichier de projet de style SDK avec [multi-ciblage](../../standard/library-guidance/cross-platform-targeting.md) (spécifiant plusieurs cibles).

Pour créer le nouveau fichier de projet, vous pouvez créer `dotnet new wpf` un nouveau projet WPF dans Visual Studio ou utiliser la commande dans un répertoire temporaire pour générer le fichier de projet, puis le copier/renommer à l’emplacement correct. Il existe également un outil créé par la communauté, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), qui peut automatiser une partie de la migration des fichiers de projet. L’outil est utile, mais a encore besoin d’un humain pour examiner les résultats pour s’assurer que tous les détails de la migration sont corrects. Un domaine particulier que l’outil ne gère pas de manière optimale est la migration des paquets NuGet à partir de fichiers *packages.config.* Si l’outil s’exécute sur un fichier de projet qui utilise toujours un `<PackageReference>` fichier *packages.config* pour référencer les paquets NuGet, il migrera automatiquement vers des éléments, mais ajoutera `<PackageReference>` des éléments pour tous *les* paquets au lieu de seulement les plus hauts niveaux. Si vous avez déjà`<PackageReference>` migré vers des éléments avec Visual Studio (comme vous l’avez fait dans cet échantillon), alors l’outil peut vous aider avec le reste de la conversion. Comme Scott Hanselman recommande dans [son blog sur la migration des fichiers csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), le portage à la main est éducatif et donnera de meilleurs résultats si vous n’avez que quelques projets à port. Mais si vous transférez des dizaines ou des centaines de fichiers de projet, alors un outil comme [CsprojToVs2017] peut être une aide.

Pour créer un nouveau fichier de projet `dotnet new wpf` pour l’échantillon Bean Trader, exécutez dans un répertoire temporaire et déplacez le fichier *généré .csproj* dans le dossier *BeanTraderClient* et renommez-le **BeanTraderClient.Core.csproj**.

Étant donné que le nouveau format de fichier de projet inclut automatiquement les fichiers C, les fichiers *resx* et les fichiers XAML qu’il trouve dans ou sous son répertoire, le fichier de projet est déjà presque complet ! Pour terminer la migration, ouvrez les fichiers anciens et nouveaux fichiers de projet côte à côte et regardez à travers l’ancien pour voir si des informations qu’il contient doit être migrée. Dans le cas de l’échantillon Bean Trader, les éléments suivants doivent être copiés sur le nouveau projet :

- Le `<RootNamespace>` `<AssemblyName>`, `<ApplicationIcon>` , et les propriétés doivent toutes être copiées.

- Vous devez également `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` ajouter une propriété au nouveau fichier de projet puisque l’échantillon bean Trader inclut des attributs de niveau d’assemblage (comme `[AssemblyTitle]`) dans un fichier AssemblyInfo.cs. Par défaut, de nouveaux projets de style SDK permettront d’autogénérer ces attributs en fonction des propriétés du fichier csproj. Parce que vous ne voulez pas que cela se produise dans ce cas (les attributs autogénérés serait `<GenerateAssemblyInfo>`en conflit avec ceux de AssemblyInfo.cs), vous désactiver les attributs autogénérés avec .

- Bien que les fichiers *resx* soient `<Resource>` automatiquement inclus comme ressources intégrées, d’autres éléments comme les images ne le sont pas. Ainsi, copiez les `<Resource>` éléments pour intégrer des fichiers d’image et d’icône. Vous pouvez simplifier les références de png à une seule ligne en utilisant `<Resource Include="**\*.png" />`le support du nouveau format de fichier de projet pour les modèles de glisse: .

- De `<None>` même, les éléments sont inclus automatiquement, mais ils ne sont pas copiés à l’annuaire de sortie, par défaut. Parce que le projet `<None>` Bean Trader comprend un élément qui `PreserveNewest` *est* copié à l’annuaire de sortie (en utilisant des comportements), vous devez mettre à jour l’élément automatiquement peuplé `<None>` pour ce fichier, comme ceci.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- L’échantillon Bean Trader comprend un fichier XAML (Default.Accent.xaml) comme `Content` (plutôt que comme un `Page`) parce que les thèmes et les accents définis dans ce fichier sont chargés à partir de XAML du fichier au moment de l’exécution, plutôt que d’être intégré dans l’application elle-même. Le nouveau système de projet `<Page>`inclut automatiquement ce fichier comme un , cependant, car il s’agit d’un fichier XAML. Donc, vous devez à la fois supprimer le`<Page Remove="**\Default.Accent.xaml" />`fichier XAML comme une page ( ) et l’ajouter comme contenu.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Enfin, ajoutez des références NuGet en copiant le `<ItemGroup>` avec tous les `<PackageReference>` éléments. Si vous n’aviez pas précédemment mis à niveau les paquets NuGet en versions compatibles .NET Core, vous pouvez le faire maintenant que les références de paquets sont dans un projet .NET Core-spécifique.

À ce stade, il devrait être possible d’ajouter le nouveau projet à la solution BeanTrader et de l’ouvrir dans Visual Studio. Le projet devrait sembler correct `dotnet restore BeanTraderClient.Core.csproj` dans Solution **Explorer**, et devrait restaurer avec succès les paquets (avec deux avertissements attendus liés à la version MahApps.Metro que vous utilisez le ciblage .NET Framework).

Bien qu’il soit possible de garder les deux fichiers de projet côte à côte (et peut même être souhaitable si vous voulez continuer à construire l’ancien projet exactement comme il était), il complique le processus de migration (les deux projets vont essayer d’utiliser le même bac et dossiers obj) et n’est généralement pas nécessaire. Si vous voulez construire pour les objectifs .NET Core `<TargetFramework>netcoreapp3.0</TargetFramework>` et .NET Framework, `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` vous pouvez remplacer la propriété dans le nouveau fichier de projet avec à la place. Pour l’échantillon Bean Trader, supprimez l’ancien fichier de projet (BeanTraderClient.csproj) car il n’est plus nécessaire. Si vous préférez conserver les deux fichiers de projet, assurez-vous de les faire construire à des voies de sortie différentes et intermédiaires.

## <a name="fix-build-issues"></a>Résoudre les problèmes de construction

La troisième étape du processus de portage consiste à construire le projet. Certaines applications seront déjà créées avec succès une fois que le fichier du projet est converti en un projet de style SDK. Si c’est le cas pour votre application, félicitations! Vous pouvez passer à l’étape 4. D’autres applications auront besoin de quelques mises à jour pour les faire construire pour .NET Core. Si vous essayez `dotnet build` d’exécuter sur le projet d’échantillon Bean Trader maintenant, par exemple, (ou le construire dans Visual Studio), il y aura beaucoup d’erreurs, mais vous les obtiendrez fixé rapidement.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Références System.ServiceModel et Microsoft.Windows.Compatibility

Une source commune d’erreurs est des références manquantes pour les API qui sont disponibles pour .NET Core, mais pas automatiquement inclus dans le métapackage de l’application .NET Core. Pour remédier à cette `Microsoft.Windows.Compatibility` situation, vous devez faire référence au paquet. Le paquet de compatibilité comprend un large ensemble d’API qui sont courantes dans les applications de bureau Windows, telles que les clients WCF, les services d’annuaire, le registre, la configuration, les API APL, et plus encore.

Avec l’échantillon Bean Trader, la majorité des <xref:System.ServiceModel> erreurs de construction sont dues à des types manquants. Ceux-ci pourraient être abordés en faisant référence aux paquets WCF NuGet nécessaires. Les API clients WCF sont `Microsoft.Windows.Compatibility` parmi ceux présents dans le paquet, cependant, ainsi référencement du paquet de compatibilité est une solution encore meilleure (puisqu’il aborde également tous les problèmes liés aux API aussi bien que des solutions aux issues de WCF que le paquet de compatibilité rend disponible). Le `Microsoft.Windows.Compatibility` paquet aide dans la plupart des scénarios de portage .NET Core 3.0 WPF et WinForms. Après avoir ajouté la `Microsoft.Windows.Compatibility`référence NuGet à , une seule erreur de construction reste!

### <a name="cleaning-up-unused-files"></a>Nettoyage des fichiers inutilisés

Un type de problème de migration qui se présente se rapporte souvent aux fichiers C et XAML qui n’étaient pas auparavant inclus dans la construction qui sont ramassés par les nouveaux projets de style SDK qui comprennent *toutes les* sources automatiquement.

L’erreur de construction suivante que vous voyez dans l’échantillon Bean Trader se réfère à une mauvaise implémentation d’interface dans *OldUnusedViewModel.cs*. Le nom du fichier est un indice, mais lors de l’inspection, vous constaterez que ce fichier source est incorrect. Il n’a pas causé de problèmes auparavant parce qu’il n’était pas inclus dans le projet cadre original .NET. Les fichiers sources qui étaient présents sur disque mais non inclus dans l’ancien *csproj* sont inclus automatiquement dès maintenant.

Pour des questions ponctuelles comme celle-ci, il est facile de comparer au *csproj* précédent `<Compile Remove="" />` pour confirmer que le fichier n’est pas nécessaire, puis soit il ou, si le fichier source n’est plus nécessaire n’importe où, le supprimer. Dans ce cas, il est sûr de simplement supprimer *OldUnusedViewModel.cs*.

Si vous avez de nombreux fichiers source qui devraient être exclus de cette façon, `<EnableDefaultCompileItems>` vous pouvez désactiver l’auto-inclusion des fichiers C en définissant la propriété à faux dans le fichier du projet. Ensuite, vous `<Compile Include>` pouvez copier des éléments de l’ancien fichier de projet à la nouvelle afin de ne construire que les sources que vous aviez l’intention d’inclure. De `<EnableDefaultPageItems>` même, peut être utilisé pour désactiver l’auto-inclusion des pages XAML et `<EnableDefaultItems>` peut contrôler les deux avec une seule propriété.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Un bref côté sur les compilateurs multi-pass

Après avoir retiré le fichier incriminé de l’échantillon Bean Trader, vous pouvez re-construire et obtiendrez quatre erreurs. Tu n’en avais pas avant ? Pourquoi le nombre d’erreurs a-t-il augmenté? Le compilateur C est un [compilateur multi-pass](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). Cela signifie qu’il passe par chaque fichier source deux fois. Tout d’abord, le compilateur se contente d’examiner les métadonnées et les déclarations dans chaque fichier source et identifie tout problème au niveau de la déclaration. Ce sont les erreurs que vous avez corrigées. Ensuite, il passe à nouveau par le code pour construire la source C EN IL; ce sont la deuxième série d’erreurs que vous voyez maintenant.

> [!NOTE]
> Le compilateur C fait [plus que seulement deux passes,](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)mais le résultat final est que les erreurs de compilateur pour les grands changements de code comme celui-ci ont tendance à venir en deux vagues.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Corrections de dépendance de tiers (Castle.Windsor)

Une autre catégorie de questions qui apparaît dans certains scénarios de migration est les différences API entre .NET Framework et .NET Core versions des dépendances. Même si un paquet NuGet cible à la fois .NET Framework et .NET Standard ou .NET Core, il peut y avoir différentes bibliothèques pour une utilisation avec des objectifs .NET différents. Cela permet aux paquets de prendre en charge de nombreuses plates-formes .NET différentes, qui peuvent nécessiter des implémentations différentes. Cela signifie également qu’il peut y avoir de petites différences d’API dans les bibliothèques lors du ciblage de différentes plates-formes .NET.

La prochaine série d’erreurs que vous verrez dans `Castle.Windsor` l’échantillon Bean Trader sont liées aux API. Le projet .NET Core Bean Trader `Castle.Windsor` utilise la même version que le projet .NET Framework-targeted (4.1.1), mais les implémentations de ces deux plates-formes sont légèrement différentes.

Dans ce cas, vous voyez les questions suivantes qui doivent être corrigées :

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`n’est pas disponible sur .NET Core. Il ya, cependant, `Classes.FromAssemblyContaining` l’API similaire disponible, `Classes.FromThisAssembly()` de sorte `Classes.FromAssemblyContaining(t)`que `t` nous pouvons remplacer les deux utilisations d’appels à , où est le type de faire l’appel.
1. De même, en *Bootstrapper.cs*, `Castle.Windsor.Installer.FromAssembly`. Ce n’est pas disponible sur .NET Core. Au lieu de cela, `FromAssembly.Containing(typeof(Bootstrapper))`cet appel peut être remplacé par .

### <a name="updating-wcf-client-usage"></a>Mise à jour de l’utilisation des clients WCF

Après avoir `Castle.Windsor` corrigé les différences, la dernière erreur de construction restante `BeanTraderServiceClient` dans le `DuplexClientBase`projet .NET Core `Open` Bean Trader est que (qui dérive de ) n’a pas de méthode. Ce n’est pas surprenant puisqu’il s’agit d’une API qui a été mise en évidence par l’analyseur de la portabilité .NET au début de ce processus de migration. Cependant, `BeanTraderServiceClient` l’attention attire notre attention sur une question plus vaste. Ce client WCF a été autogénéré par l’outil [Svcutil.exe.](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

**Les clients WCF générés par Svcutil sont destinés à être utilisés sur .NET Framework.**

Les solutions qui utilisent des clients WCF générés par le svcutil devront régénérer les clients compatibles avec la norme .NET pour une utilisation avec .NET Core. L’une des principales raisons pour lesquelles les anciens clients ne fonctionneront pas est qu’ils dépendent de la configuration de l’application pour définir les liaisons et les paramètres WCF. Parce que les API WCF standard .NET peuvent fonctionner interplateforme (où les API System.Configuration ne sont pas disponibles), les clients WCF pour les scénarios .NET Core et .NET Standard doivent définir les liaisons et les points de terminaison programmatiquement plutôt que dans la configuration.

En fait, toute utilisation du client `<system.serviceModel>` WCF qui dépend de la section app.config (qu’elle soit créée avec Svcutil ou manuellement) devra être modifiée pour travailler sur .NET Core.

Il existe deux façons de générer automatiquement des clients WCF compatibles avec la norme .NET :

- L’outil `dotnet-svcutil` est un outil .NET qui génère des clients WCF d’une manière qui est similaire à la façon dont Svcutil a travaillé précédemment.
- Visual Studio peut générer des clients WCF en utilisant l’option [WCF Web Service Reference](../../core/additional-tools/wcf-web-service-reference-guide.md) de sa fonction Services connectés.

L’une ou l’autre approche fonctionne bien. Alternativement, bien sûr, vous pouvez écrire le code client WCF vous-même. Pour cet exemple, j’ai choisi d’utiliser la fonction Visual Studio Connected Service. Pour ce faire, cliquez à droite sur le projet *BeanTraderClient.Core* dans l’explorateur de solutions de Visual Studio et sélectionnez **Add** > **Connected Service**. Ensuite, choisissez le fournisseur de référence de service Web WCF. Cela fera état d’un dialogue où vous pouvez spécifier`localhost:8080` l’adresse du service Web Backend Bean Trader (si vous exécutez le serveur localement) et l’espace nom qui a généré des types devraient utiliser (**BeanTrader.Service**, par exemple).

![WCF Web Service Reference Connected Service Dialog](./media/convert-project-from-net-framework/connected-service-dialog.png)

Une fois que vous avez choisi le bouton **Finition,** un nouveau nœud services connectés est ajouté au projet et un fichier Reference.cs est ajouté sous ce nœud contenant le nouveau client .NET Standard WCF pour accéder au service Bean Trader. Si vous regardez `GetEndpointAddress` `GetBindingForEndpoint` les méthodes ou les méthodes de ce fichier, vous verrez que les fixations et les paramètres sont maintenant générés de façon programmatique (au lieu de via app config). La fonction «Ajouter des services connectés» peut également ajouter des références à certains paquets System.ServiceModel dans le fichier du projet, qui ne sont pas nécessaires puisque tous les paquets WCF nécessaires sont inclus via Microsoft.Windows.Compatibility. Vérifiez le csproj pour voir si des `<PackageReference>` éléments supplémentaires de System.ServiceModel ont été ajoutés, et si oui, supprimez-les.

Notre projet a de nouvelles classes de clients WCF maintenant (en *Reference.cs),* mais il a aussi encore les anciens (en BeanTrader.cs). Il y a deux options à ce stade :

- Si vous souhaitez être en mesure de construire le projet cadre .NET original (à `<Compile Remove="BeanTrader.cs" />` côté du nouveau .NET Core-targeted one), vous pouvez utiliser un élément dans le fichier csproj du projet .NET Core afin que les versions .NET Framework et .NET Core de l’application utilisent différents clients WCF. Cela a l’avantage de laisser le projet cadre .NET existant inchangé, mais a l’inconvénient que le code utilisant les clients WCF générés peuvent avoir besoin `#if` d’être légèrement différent dans le cas .NET Core qu’il ne l’était dans le projet cadre .NET, de sorte que vous aurez probablement besoin d’utiliser des directives pour compiler sous condition une certaine utilisation des clients WCF (création de clients, par exemple) de travailler d’une manière lorsqu’il était construit pour .NET Core et une autre façon lorsqu’il est construit pour .NET Framework.

- Si, d’autre part, un certain désabonnement de code dans le projet cadre .NET existant est acceptable, vous pouvez supprimer *BeanTrader.cs* tous ensemble. Parce que le nouveau client WCF est conçu pour .NET Standard, il fonctionnera à la fois dans les scénarios .NET Core et .NET Framework. Si vous construisez pour .NET Framework en plus de .NET Core (soit par multi-ciblage ou en ayant deux fichiers csproj), vous pouvez utiliser ce nouveau fichier *Reference.cs* pour les deux cibles. Cette approche a l’avantage que le code n’aura pas besoin de bifurquer pour soutenir deux clients WCF différents; le même code sera utilisé partout. L’inconvénient est qu’il s’agit de modifier le projet cadre (probablement stable) .NET.

Dans le cas de l’échantillon Bean Trader, vous pouvez apporter de petites modifications au projet original s’il facilite la migration, alors suivez ces étapes pour concilier l’utilisation des clients WCF :

01. Ajoutez le nouveau fichier Reference.cs au projet .NET Framework *BeanTraderClient.csproj* à l’aide du menu contextuel « Ajouter l’élément existant » de l’explorateur de solution. Assurez-vous d’ajouter « comme lien » afin que le même fichier soit utilisé par les deux projets (plutôt que de copier le fichier C). Si vous construisez pour .NET Core et .NET Framework avec un seul csproj (en utilisant multi-ciblage), alors cette étape n’est pas nécessaire.

01. Supprimer *BeanTrader.cs*.

01. Le nouveau client WCF est similaire à l’ancien, mais un certain nombre d’espaces de nom dans le code généré sont différents. Pour cette raison, il est nécessaire de mettre à jour le projet afin que les types de clients WCF sont utilisés à partir de BeanTrader.Service (ou quel que soit le nom que vous avez choisi) au lieu de BeanTrader.Model ou sans espace nom. Construire *BeanTraderClient.Core.csproj* aidera à identifier où ces changements doivent être apportés. Des correctifs seront nécessaires à la fois dans les fichiers de source C et XAML.

01. Enfin, vous découvrirez qu’il *BeanTraderServiceClientFactory.cs* y a une erreur dans `BeanTraderServiceClient` BeanTraderServiceClientFactory.cs parce que les constructeurs disponibles pour le type ont changé. Il était possible de `InstanceContext` fournir un argument (qui `Castle.Windsor` a été créé à l’aide d’un `CallbackHandler` conteneur IoC). Les nouveaux constructeurs `CallbackHandler`créent de nouveaux s. Il ya, cependant, `BeanTraderServiceClient`les constructeurs dans le type de base qui correspondent à ce que vous voulez. Étant donné que le code client WCF autogénéré existe dans les classes partielles, vous pouvez facilement l’étendre. Pour ce faire, créez un nouveau fichier appelé *BeanTraderServiceClient.cs,* puis créez une classe partielle avec ce même nom (en utilisant le namespace BeanTrader.Service). Ensuite, ajoutez un constructeur au type partiel tel qu’il est indiqué ici.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Avec ces modifications apportées, l’échantillon Bean Trader sera désormais à l’aide d’un nouveau `Open` client WCF compatible `await OpenAsync` standard .NET et vous pouvez faire le correctif final de changer l’appel dans *TradingService.cs* à utiliser à la place.

Avec les questions WCF abordés, la version .NET Core de l’échantillon Bean Trader construit maintenant proprement!

## <a name="runtime-testing"></a>Test de temps d’exécution

Il est facile d’oublier que les travaux de migration ne se font pas dès que le projet se développe proprement contre .NET Core. Il est important de laisser le temps de tester l’application ported, aussi. Une fois que les choses se construisent avec succès, assurez-vous que l’application fonctionne et fonctionne comme prévu, surtout si vous utilisez des paquets ciblant .NET Framework.

Essayons de lancer l’application Ported Bean Trader et voir ce qui se passe. L’application ne va pas loin avant d’échouer à l’exception suivante.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

C’est logique, bien sûr. Rappelez-vous que WCF n’utilise plus la configuration de l’application, de sorte que l’ancienne section system.serviceModel du fichier app.config doit être supprimée. Le client WCF mis à jour inclut toutes les mêmes informations dans son code, de sorte que la section config n’est plus nécessaire. Si vous vouliez que le point de terminaison WCF soit configurable dans app.config, vous pouvez l’ajouter comme paramètre d’application et mettre à jour le code client WCF pour récupérer le critère de service WCF de la configuration.

Après avoir supprimé la section system.serviceModel de *app.config*, l’application lance mais échoue à une autre exception lorsqu’un utilisateur s’y inscrit.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

L’API non pris `Func<T>.BeginInvoke`en soutien est . Comme expliqué dans [dotnet/corefx-5940](https://github.com/dotnet/corefx/issues/5940), .NET `BeginInvoke` Core `EndInvoke` ne prend pas en charge les types et les méthodes sur les types de délégués en raison de dépendances sous-jacentes de remotage. Ce problème et son correctif sont expliqués plus en détail dans le [Délégué Migrateur.BeginInvoke appels pour .NET Core](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) blog post, mais l’essentiel est `BeginInvoke` que et `EndInvoke` les appels doivent être remplacés par `Task.Run` (ou des alternatives async, si possible). En appliquant la `BeginInvoke` solution générale ici, `Invoke` l’appel peut être remplacé par un appel lancé par `Task.Run`.

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

Après avoir `BeginInvoke` supprimé l’utilisation, l’application Bean Trader fonctionne avec succès sur .NET Core!

![Bean Trader en cours d’exécution sur .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Toutes les applications sont différentes, de sorte que les étapes spécifiques nécessaires pour migrer vos propres applications vers .NET Core variera. Mais j’espère que l’échantillon Bean Trader démontre le flux de travail général et les types de questions qui peuvent être attendus. Et, malgré la longueur de cet article, les changements réels nécessaires dans l’échantillon de Bean Trader pour le faire fonctionner sur .NET Core étaient assez limités. De nombreuses applications migrent vers .NET Core de cette même manière; avec des modifications de code limitées ou même nulles nécessaires.
