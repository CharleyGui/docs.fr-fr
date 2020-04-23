---
title: Migration d’applications WPF vers .NET Core 3,0
description: Découvrez comment migrer une application Windows Presentation Foundation (WPF) vers .NET Core 3,0.
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
# <a name="migrating-wpf-apps-to-net-core"></a>Migration d’applications WPF vers .NET Core

Cet article décrit les étapes nécessaires à la migration d’une application Windows Presentation Foundation (WPF) à partir de .NET Framework vers .NET Core 3,0. Si vous ne disposez pas d’une application WPF sur le port, mais que vous souhaitez essayer le processus, vous pouvez utiliser l’exemple d’application **Bean opérateur** disponible sur [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). L’application d’origine (ciblant .NET Framework 4.7.2) est disponible dans le dossier NetFx\BeanTraderClient. Tout d’abord, nous allons expliquer les étapes nécessaires pour porter les applications en général, puis nous allons examiner les modifications spécifiques qui s’appliquent à l’exemple de **courtier Bean** .

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Pour migrer vers .NET Core, vous devez d’abord :

01. Comprendre et mettre à jour les dépendances NuGet :

    01. Mettez à niveau les dépendances `<PackageReference>` NuGet pour utiliser le format.
    01. Examinez les dépendances NuGet de niveau supérieur pour .NET Core ou la compatibilité .NET Standard.
    01. Mettez à niveau les packages NuGet vers des versions plus récentes.
    01. Utilisez l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) pour comprendre les dépendances .net.

01. Migrez le fichier projet vers le nouveau format de style SDK :

    01. Indiquez si vous souhaitez cibler à la fois .NET Core et .NET Framework, ou uniquement .NET Core.
    01. Copiez les propriétés et éléments de fichier projet appropriés dans le nouveau fichier projet.

01. Résoudre les problèmes de génération :

    01. Ajoutez une référence au package [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) .
    01. Recherchez et corrigez les différences au niveau de l’API.
    01. Supprimez les sections *app. config* `appSettings` autres `connectionStrings`que ou.
    01. Régénérez le code généré, si nécessaire.

01. Test du Runtime :

    01. Confirmez que l’application portée fonctionne comme prévu.
    01. Méfiez- <xref:System.NotSupportedException> vous des exceptions.

## <a name="about-the-sample"></a>À propos de l’exemple

Cet article fait référence à l' [exemple d’application Bean opérateur](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) , car il utilise une variété de dépendances similaires à celles que des applications WPF réelles peuvent avoir. L’application n’est pas grande, mais elle est destinée à être une étape allant de « Hello World » en termes de complexité. L’application montre certains problèmes que les utilisateurs peuvent rencontrer lors du Portage d’applications réelles. L’application communique avec un service WCF. pour qu’elle s’exécute correctement, vous devez également exécuter le projet BeanTraderServer (disponible dans le même dépôt GitHub) et vous assurer que la configuration BeanTraderClient pointe vers le point de terminaison correct. (Par défaut, l’exemple suppose que le serveur est en cours d’exécution sur le *http://localhost:8090*même ordinateur à, ce qui est vrai si vous lancez BeanTraderServer localement.)

Gardez à l’esprit que cet exemple d’application est destiné à illustrer les défis et les solutions de Portage .NET Core. Elle n’est pas destinée à illustrer les bonnes pratiques WPF. En fait, il comprend délibérément des anti-modèles pour s’assurer que vous avez rencontré au moins deux défis intéressants lors du Portage.

## <a name="getting-ready"></a>Préparation

Le principal défi de la migration d’une application .NET Framework vers .NET Core est que ses dépendances peuvent fonctionner différemment ou pas du tout. La migration est beaucoup plus facile qu’elle ne l’était. de nombreux packages NuGet ciblent à présent .NET Standard. À compter de .NET Core 2,0, les zones d’exposition .NET Framework et .NET Core sont devenues similaires. Même dans ce cas, certaines différences (à la fois pour la prise en charge des packages NuGet et dans les API .NET disponibles) sont conservées. La première étape de la migration consiste à passer en revue les dépendances de l’application et à vérifier que les références sont dans un format qui est facilement migré vers .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Mettre à `<PackageReference>` niveau vers les références NuGet

Les anciens projets de .NET Framework répertorient généralement leurs dépendances NuGet dans un fichier *packages. config* . Le nouveau format de fichier de projet de type SDK fait référence [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) aux packages NuGet en tant qu’éléments dans le fichier csproj lui-même plutôt que dans un fichier de configuration distinct.

Lors de la migration, il existe deux avantages `<PackageReference>`à l’utilisation des références de style :

- Il s’agit du style de référence NuGet requis pour le nouveau fichier projet .NET Core. Si vous utilisez `<PackageReference>`déjà, vous pouvez copier et coller ces éléments de fichier projet directement dans le nouveau projet.
- Contrairement à un fichier Packages. config `<PackageReference>` , les éléments font uniquement référence aux dépendances de niveau supérieur dont votre projet dépend directement. Tous les autres packages NuGet transitifs seront déterminés au moment de la restauration et enregistrés dans le fichier obj\project.Assets.JSON généré automatiquement. Il est ainsi beaucoup plus facile de déterminer les dépendances de votre projet, ce qui est utile pour déterminer si les dépendances nécessaires fonctionnent sur .NET Core ou non.

La première étape de la migration d’une application .NET Framework vers .NET Core consiste à la mettre `<PackageReference>` à jour pour utiliser des références NuGet. Visual Studio simplifie cette solution. Il vous suffit de cliquer avec le bouton droit sur le fichier *packages. config* du projet dans le **Explorateur de solutions**de Visual Studio, puis de sélectionner **migrer packages. config vers PackageReference**.

![Mise à niveau vers PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Une boîte de dialogue s’affiche avec les dépendances NuGet de niveau supérieur calculées et vous demandant quels autres packages NuGet doivent être promus au niveau le plus élevé. Aucun de ces autres packages n’a besoin d’être de niveau supérieur pour l’exemple Bean responsable. vous pouvez donc décocher toutes ces zones. Ensuite, cliquez sur **OK** et le fichier *packages. config* est supprimé `<PackageReference>` et les éléments sont ajoutés au fichier projet.

`<PackageReference>`-les références de style ne stockent pas les packages NuGet localement dans un dossier de packages. Au lieu de cela, elles sont stockées globalement en tant qu’optimisation. Une fois la migration terminée, modifiez le fichier csproj et supprimez `<Analyzer>` tous les éléments qui font référence aux analyseurs qui proviennent précédemment de *. Répertoire \Packages* . Ne vous inquiétez pas ; étant donné que vous avez toujours les références de package NuGet, les analyseurs seront inclus dans le projet. Vous devez simplement nettoyer les anciens éléments de style `<Analyzer>` packages. config.

### <a name="review-nuget-packages"></a>Examiner les packages NuGet

Maintenant que vous pouvez voir les packages NuGet de niveau supérieur dont le projet dépend, vous pouvez vérifier si ces packages sont disponibles sur .NET Core. Vous pouvez déterminer si un package prend en charge .NET Core en examinant ses dépendances sur [NuGet.org](https://www.nuget.org/). Le site [fuget.org](https://www.fuget.org/) créé par la communauté affiche ces informations en haut de la page d’informations du package.

Quand vous ciblez .NET Core 3,0, tous les packages ciblant .NET Core ou .NET Standard doivent fonctionner (puisque .NET Core implémente la surface d’exposition .NET Standard). Dans certains cas, la version spécifique d’un package qui est utilisée ne cible pas .NET Core ou .NET Standard, mais les versions plus récentes. Dans ce cas, vous devez envisager une mise à niveau vers la version la plus récente du package.

Vous pouvez également utiliser des packages ciblant .NET Framework, mais cela présente des risques. .NET Core vers .NET Framework les dépendances sont autorisées, car les zones de surface de .NET Framework et .NET Core sont suffisamment semblables pour que ces dépendances fonctionnent *souvent* . Toutefois, si le package tente d’utiliser une API .NET qui n’est pas présente dans .NET Core, vous rencontrerez une exception d’exécution. Pour cette raison, vous ne devez référencer des packages .NET Framework que si aucune autre option n’est disponible et comprendre que cela impose une charge de test.

Si des packages référencés ne ciblent pas .NET Core ou .NET Standard, vous devez réfléchir à d’autres solutions :

- Existe-t-il d’autres packages similaires qui peuvent être utilisés à la place ? Parfois, les auteurs NuGet publient des’séparés'. Versions principales de leurs bibliothèques ciblant spécifiquement .NET Core. Les packages Enterprise Library sont un exemple de la publication de la communauté». Solutions Netcore». Dans d’autres cas, des kits de développement logiciel récents pour un service particulier (parfois avec des noms de packages différents) sont disponibles pour .NET Standard. Si aucune solution n’est disponible, vous pouvez continuer à utiliser les packages ciblés .NET Framework, en sachant que vous devrez les tester minutieusement une fois exécuté sur .NET Core.

L’exemple de courtier de haricot présente les dépendances NuGet de niveau supérieur suivantes :

- [**Castle. Windsor, version 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Ce package cible .NET Standard 1,6, il fonctionne donc sur .NET Core.

- [**Microsoft. CodeAnalysis. FxCopAnalyzers, version 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Il s’agit d’un méta-package, donc il n’est pas évident de savoir immédiatement quelles plateformes il prend en charge, mais la [documentation](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) indique que sa version la plus récente (2.9.2) fonctionnera pour les .NET Framework et .net core.

- [**Nito. AsyncEx, version 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Ce package ne cible pas .NET Core, mais la version 5,0 la plus récente le fait. Cette opération est courante lors de la migration, car de nombreux packages NuGet ont récemment ajouté la prise en charge de .NET Standard, mais les anciennes versions de projet ne ciblent que les .NET Framework. Si la différence de version n’est qu’une différence de version mineure, il est souvent facile de procéder à une mise à niveau vers la version la plus récente. Étant donné qu’il s’agit d’une modification de version majeure, vous devez effectuer une mise à niveau avec prudence, car il y a peut-être des modifications avec rupture dans le package. Toutefois, un chemin d’accès est correct.

- [**MahApps. Metro, version 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Ce package ne cible pas non plus .NET Core, mais dispose d’une version préliminaire plus récente (2,0-alpha). Là encore, vous devez consulter les modifications avec rupture, mais le package le plus récent est encourageant.

Les dépendances NuGet de l’exemple de courtier Bean sont toutes deux cibles .NET Standard/. NET Core ou ont des versions plus récentes qui, par conséquent, il est peu probable qu’il y ait des problèmes de blocage ici.

### <a name="upgrade-nuget-packages"></a>Mettre à niveau les packages NuGet

Si possible, il serait judicieux de mettre à niveau les versions de tous les packages qui ciblent uniquement .NET Core ou .NET Standard avec des versions plus récentes à ce stade (avec le projet qui cible toujours .NET Framework) pour découvrir et résoudre les modifications avec rupture.

Si vous préférez ne pas apporter de modifications matérielles à la version .NET Framework existante de l’application, cela peut attendre jusqu’à ce que vous ayez un nouveau fichier projet ciblant .NET Core. Toutefois, la mise à niveau des packages NuGet vers des versions compatibles .NET Core à l’avance rend le processus de migration encore plus facile une fois que vous avez créé le nouveau fichier projet et réduit le nombre de différences entre les versions .NET Framework et .NET Core de l’application.

Avec l’exemple Bean responsable, toutes les mises à niveau nécessaires peuvent être effectuées facilement (à l’aide du gestionnaire de package NuGet de Visual Studio), à une exception près : la mise à niveau de **MahApps. Metro 1.6.5** vers **2,0** révèle des modifications avec rupture relatives aux API de gestion des thèmes et des accents.

Dans l’idéal, l’application est mise à jour pour utiliser la version la plus récente du package (car elle est plus susceptible de fonctionner sur .NET Core). Dans certains cas, toutefois, cela peut ne pas être possible. Dans ce cas, ne mettez pas à niveau **MahApps. Metro** , car les modifications nécessaires sont non triviales et ce didacticiel se concentre sur la migration vers .net Core 3, et non sur **MahApps. Metro 2.** En outre, il s’agit d’une dépendance .NET Framework à faible risque, car l’application de l’opérateur du haricot n’exerce qu’une petite partie de **MahApps. Metro**. Bien entendu, il est nécessaire de tester pour s’assurer que tout fonctionne une fois la migration terminée. S’il s’agissait d’un scénario réaliste, il serait judicieux de créer un problème pour suivre le travail à migrer vers **MahApps. Metro** version 2,0, car la migration n’a pas été effectuée à l’heure actuelle.

Une fois les packages NuGet mis à jour vers les versions `<PackageReference>` récentes, le groupe d’éléments dans le fichier projet de l’exemple de courtier Bean doit ressembler à ce qui suit.

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

### <a name="net-framework-portability-analysis"></a>Analyse de la portabilité .NET Framework

Une fois que vous comprenez l’état des dépendances NuGet de votre projet, la prochaine chose à prendre en compte est .NET Framework les dépendances de l’API. L’outil de l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) est utile pour comprendre quelles API .net votre projet utilise sont disponibles sur d’autres plateformes .net.

L’outil se présente sous la forme d’un plug [-](https://github.com/Microsoft/dotnet-apiport/releases) [in Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), d’un outil de ligne de commande ou encapsulé dans une [interface graphique utilisateur simple](https://github.com/Microsoft/dotnet-apiport-ui), ce qui simplifie ses options. Vous pouvez en savoir plus sur l’utilisation de l’analyseur de portabilité .NET (port d’API) à l’aide de l’interface graphique utilisateur dans le billet de blog [sur le portage des applications de bureau vers .net Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) . Si vous préférez utiliser la ligne de commande, les étapes nécessaires sont les suivantes :

1. Téléchargez l' [Analyseur de portabilité .net](https://github.com/Microsoft/dotnet-apiport/releases) si vous ne l’avez pas déjà.
1. Assurez-vous que l’application de .NET Framework est correctement reportée (il s’agit d’une bonne idée avant la migration).
1. Exécutez le port de l’API avec une ligne de commande telle que celle-ci.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    L' `-f` argument spécifie le chemin d’accès contenant les fichiers binaires à analyser. L' `-r` argument spécifie le format de fichier de sortie souhaité. L' `-t` argument spécifie la plateforme .net sur laquelle analyser l’utilisation de l’API. Dans ce cas, vous devez utiliser .NET Core.

Lorsque vous ouvrez le rapport HTML, la première section répertorie tous les fichiers binaires analysés et le pourcentage des API .NET qu’ils utilisent sur la plateforme ciblée. Le pourcentage n’est pas significatif par lui-même. Ce qui est plus utile est de voir les API spécifiques qui sont manquantes. Pour ce faire, sélectionnez un nom d’assembly ou faites défiler les rapports pour obtenir des assemblys individuels.

Concentrez-vous sur les assemblys pour lesquels vous possédez le code source. Dans le rapport ApiPort de l’opérateur Bean, par exemple, de nombreux fichiers binaires sont répertoriés, mais la plupart d’entre eux appartiennent à des packages NuGet. `Castle.Windsor`indique qu’il dépend de certaines API System. Web manquantes dans .NET Core. Ce n’est pas un problème, car vous `Castle.Windsor` avez déjà vérifié que prend en charge .net core. Il est courant que les packages NuGet aient des binaires différents à utiliser avec différentes plateformes .NET. par conséquent, si `Castle.Windsor` la version .NET Framework de utilise des API System. Web ou non n’est pas pertinente tant que le package cible également .NET standard ou .net Core (ce qu’elle fait).

Avec l’exemple de courtier de haricot, le seul binaire que vous devez prendre en compte est **BeanTraderClient** et le rapport montre que seules deux API .NET `System.ServiceModel.ClientBase<T>.Close` sont `System.ServiceModel.ClientBase<T>.Open`manquantes : et.

![Rapport de portabilité BeanTraderClient](./media/convert-project-from-net-framework/portability-report.png)

Il est peu probable qu’il y ait des problèmes de blocage, car les API clientes WCF sont (principalement) prises en charge sur .NET Core. elles doivent donc être disponibles pour ces API centrales. En fait, en observant `System.ServiceModel`la surface d’exposition .net Core <https://apisof.net>(à l’aide de), vous constatez qu’il existe des alternatives Async dans .net core à la place.

Sur la base de ce rapport et de l’analyse de dépendance NuGet précédente, il semblerait qu’il n’y ait pas de problèmes majeurs lors de la migration de l’exemple de courtier Bean vers .NET Core. Vous êtes prêt pour l’étape suivante dans laquelle vous allez démarrer la migration.

## <a name="migrating-the-project-file"></a>Migration du fichier projet

Si votre application n’utilise pas le nouveau [format de fichier projet de type SDK](../../core/tools/csproj.md), vous aurez besoin d’un nouveau fichier projet pour cibler .net core. Vous pouvez remplacer le fichier csproj existant ou, si vous préférez conserver le projet existant intact dans son état actuel, vous pouvez ajouter un nouveau fichier csproj ciblant .NET Core. Vous pouvez créer des versions de l’application pour .NET Framework et .NET Core avec un seul fichier projet de type SDK avec [multi-ciblage](../../standard/library-guidance/cross-platform-targeting.md) (en `<TargetFrameworks>` spécifiant plusieurs cibles).

Pour créer le nouveau fichier projet, vous pouvez créer un projet WPF dans Visual Studio ou utiliser la `dotnet new wpf` commande dans un répertoire temporaire pour générer le fichier projet, puis le copier/le renommer à l’emplacement correct. Il existe également un outil créé par la Communauté, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), qui permet d’automatiser une partie de la migration des fichiers projet. L’outil est utile, mais il a toujours besoin d’un homme pour passer en revue les résultats afin de s’assurer que tous les détails de la migration sont corrects. L’outil ne gère pas de manière optimale les packages NuGet à partir des fichiers *packages. config* . Si l’outil s’exécute sur un fichier projet qui utilise toujours un fichier *packages. config* pour faire référence à des packages NuGet, `<PackageReference>` il migre automatiquement vers les `<PackageReference>` éléments, mais il ajoute des éléments pour tous les packages, et non uniquement pour *les* éléments de niveau supérieur. Si vous avez déjà migré vers`<PackageReference>` des éléments avec Visual Studio (comme vous l’avez fait dans cet exemple), l’outil peut vous aider dans le reste de la conversion. Comme Scott Hanselman recommande dans [son billet de blog sur la migration de fichiers csproj, le](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)Portage à la main est éducatif et donnera de meilleurs résultats si vous n’avez que quelques projets à porter. Toutefois, si vous portez des dizaines ou des centaines de fichiers de projet, un outil tel que [CsprojToVs2017] peut être une aide.

Pour créer un nouveau fichier projet pour l’exemple Bean responsable, exécutez `dotnet new wpf` dans un répertoire temporaire et déplacez le fichier *. csproj* généré dans le dossier *BeanTraderClient* et renommez-le **BeanTraderClient. Core. csproj**.

Étant donné que le nouveau format de fichier projet comprend automatiquement des fichiers C#, des fichiers *resx* et des fichiers XAML qu’il trouve dans ou sous son répertoire, le fichier projet est déjà presque terminé. Pour terminer la migration, ouvrez les fichiers de projet anciens et nouveaux côte à côte, puis examinez l’ancien pour voir si les informations qu’il contient doivent être migrées. Dans l’exemple de cas d’opérateur Bean, les éléments suivants doivent être copiés dans le nouveau projet :

- Les `<RootNamespace>`propriétés `<AssemblyName>`, et `<ApplicationIcon>` doivent toutes être copiées.

- Vous devez également ajouter une `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` propriété au nouveau fichier projet, car l’exemple de courtier de haricot comprend des attributs au niveau de `[AssemblyTitle]`l’assembly (comme) dans un fichier AssemblyInfo.cs. Par défaut, les nouveaux projets de type SDK génèrent automatiquement ces attributs en fonction des propriétés du fichier csproj. Comme vous ne voulez pas que cela se produise dans ce cas (les attributs générés automatiquement sont en conflit avec ceux de AssemblyInfo.cs), vous désactivez les attributs générés automatiquement avec `<GenerateAssemblyInfo>`.

- Bien que les fichiers *resx* soient automatiquement inclus en tant que `<Resource>` ressources incorporées, les autres éléments tels que les images ne le sont pas. Copiez donc les `<Resource>` éléments pour l’incorporation des fichiers d’image et d’icône. Vous pouvez simplifier les références png à une seule ligne à l’aide de la prise en charge du nouveau format de fichier `<Resource Include="**\*.png" />`projet pour les modèles globbing :.

- De même, `<None>` les éléments sont inclus automatiquement, mais ils ne sont pas copiés dans le répertoire de sortie, par défaut. Étant donné que le projet Bean opérateur `<None>` comprend un élément qui *est* copié dans le répertoire de `PreserveNewest` sortie (à l’aide de comportements), vous devez `<None>` mettre à jour l’élément rempli automatiquement pour ce fichier, comme ceci.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- L’exemple Bean opérateur comprend un fichier XAML (default. accent. Xaml) en `Content` tant que (plutôt que `Page`), car les thèmes et les accents définis dans ce fichier sont chargés à partir du XAML du fichier au moment de l’exécution, au lieu d’être incorporés dans l’application elle-même. Toutefois, le nouveau système de projet comprend automatiquement ce `<Page>`fichier en tant que fichier XAML. Vous devez donc supprimer le fichier XAML en tant que page (`<Page Remove="**\Default.Accent.xaml" />`) et l’ajouter en tant que contenu.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Enfin, ajoutez des références NuGet en copiant `<ItemGroup>` le avec tous `<PackageReference>` les éléments. Si vous n’aviez pas précédemment mis à niveau les packages NuGet vers des versions compatibles avec .NET Core, vous pouviez le faire maintenant que les références de package se trouvent dans un projet .NET Core spécifique.

À ce stade, il doit être possible d’ajouter le nouveau projet à la solution BeanTrader et de l’ouvrir dans Visual Studio. Le projet doit être correct dans **Explorateur de solutions**et `dotnet restore BeanTraderClient.Core.csproj` doit restaurer correctement les packages (avec deux avertissements attendus liés à la version MahApps. Metro que vous utilisez pour cibler .NET Framework).

Bien qu’il soit possible de conserver les deux fichiers de projet côte à côte (et peut même être souhaitable si vous souhaitez continuer à générer l’ancien projet exactement tel qu’il était), cela complique le processus de migration (les deux projets essaieront d’utiliser les mêmes dossiers bin et obj) et ne sont généralement pas nécessaires. Si vous souhaitez générer pour les cibles .NET Core et .NET Framework, vous pouvez remplacer la `<TargetFramework>netcoreapp3.0</TargetFramework>` propriété dans le nouveau fichier projet par à `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` la place. Pour l’exemple Bean responsable, supprimez l’ancien fichier de projet (BeanTraderClient. csproj), car il n’est plus nécessaire. Si vous préférez conserver les deux fichiers de projet, assurez-vous qu’ils sont générés sur différents chemins de sortie et de sortie intermédiaires.

## <a name="fix-build-issues"></a>Résoudre les problèmes de build

La troisième étape du processus de Portage consiste à obtenir le projet à générer. Certaines applications sont déjà générées correctement une fois que le fichier projet est converti en projet de type SDK. Si c’est le cas pour votre application, félicitations ! Vous pouvez passer à l’étape 4. D’autres applications auront besoin de certaines mises à jour pour les mettre en œuvre pour .NET Core. Si vous essayez d’exécuter `dotnet build` l’exemple de projet Bean opérateur maintenant, par exemple (ou de le générer dans Visual Studio), il y aura de nombreuses erreurs, mais vous les obtiendrez rapidement fixe.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System. ServiceModel fait référence à et Microsoft. Windows. Compatibility

Il manque des références pour les API qui sont disponibles pour .NET Core, mais qui ne sont pas automatiquement incluses dans le package d’application .NET Core. Pour résoudre ce cas, vous devez référencer le `Microsoft.Windows.Compatibility` package. Le package de compatibilité comprend un large éventail d’API qui sont courantes dans les applications de bureau Windows, telles que le client WCF, les services d’annuaire, le registre, la configuration, les API de listes de contrôle d’accès (ACL) et bien plus encore.

Avec l’exemple Bean d’opérateur, la majorité des erreurs de build sont dues à <xref:System.ServiceModel> des types manquants. Ils peuvent être traités en référençant les packages NuGet WCF nécessaires. Toutefois, les API clientes WCF sont parmi `Microsoft.Windows.Compatibility` celles présentes dans le package. par conséquent, le fait de référencer le package de compatibilité est une solution encore meilleure (puisqu’il résout également les problèmes liés aux API, ainsi que les solutions aux problèmes WCF que le package de compatibilité rend disponible). Le `Microsoft.Windows.Compatibility` package vous aide dans la plupart des scénarios de Portage .net Core 3,0 WPF et WinForms. Après l’ajout de la référence `Microsoft.Windows.Compatibility`NuGet à, une seule erreur de build est conservée.

### <a name="cleaning-up-unused-files"></a>Nettoyage des fichiers inutilisés

L’un des types de problèmes de migration qui s’affichent est souvent lié aux fichiers C# et XAML qui n’étaient pas inclus précédemment dans la build qui a été récupéré par les nouveaux projets de type SDK qui incluent *toutes les* sources automatiquement.

L’erreur de build suivante que vous voyez dans l’exemple de courtier de haricot fait référence à une implémentation d’interface incorrecte dans *OldUnusedViewModel.cs*. Le nom de fichier est un indicateur, mais à l’inspection, vous constaterez que ce fichier source est incorrect. Il n’a pas provoqué les problèmes précédemment, car il n’était pas inclus dans le projet d' .NET Framework d’origine. Les fichiers sources qui étaient présents sur le disque mais non inclus dans l’ancien *csproj* sont maintenant inclus automatiquement.

Pour les problèmes uniques comme celui-ci, il est facile de le comparer au *csproj* précédent pour confirmer que le fichier n’est pas nécessaire, `<Compile Remove="" />` puis, si le fichier source n’est plus nécessaire, supprimez-le. Dans ce cas, il est préférable de simplement supprimer *OldUnusedViewModel.cs*.

Si vous avez de nombreux fichiers sources qui doivent être exclus de cette manière, vous pouvez désactiver l’inclusion automatique des fichiers C# en affectant `<EnableDefaultCompileItems>` à la propriété la valeur false dans le fichier projet. Ensuite, vous pouvez copier `<Compile Include>` des éléments de l’ancien fichier projet vers le nouveau, afin de générer uniquement les sources que vous souhaitez inclure. De même, `<EnableDefaultPageItems>` peut être utilisé pour désactiver l’insertion automatique des pages XAML et `<EnableDefaultItems>` peut contrôler les deux avec une seule propriété.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Un court de côté sur les compilateurs à plusieurs passes

Après avoir supprimé le fichier incriminé de l’exemple Bean responsable, vous pouvez regénérer et afficher quatre erreurs. Vous ne l’avez pas encore fait ? Pourquoi le nombre d’erreurs est-il atteint ? Le compilateur C# est un [compilateur à plusieurs passes](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). Cela signifie qu’il parcourt chaque fichier source à deux reprises. Tout d’abord, le compilateur examine simplement les métadonnées et les déclarations dans chaque fichier source et identifie les problèmes au niveau de la déclaration. Il s’agit des erreurs que vous avez résolues. Ensuite, il parcourt à nouveau le code pour générer la source C# dans IL. Il s’agit du deuxième ensemble d’erreurs que vous êtes en train de voir.

> [!NOTE]
> Le compilateur C# effectue [plus que deux passes](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes), mais le résultat final est que les erreurs de compilateur pour les modifications de code volumineuses, telles que celles-ci, ont tendance à être en deux vagues.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Correctifs de dépendance tiers (Castle. Windsor)

Une autre classe de problème qui s’affiche dans certains scénarios de migration est l’API différences entre .NET Framework et les versions .NET Core des dépendances. Même si un package NuGet cible à la fois .NET Framework et .NET Standard ou .NET Core, il peut y avoir différentes bibliothèques à utiliser avec différentes cibles .NET. Cela permet aux packages de prendre en charge de nombreuses plateformes .NET différentes, ce qui peut nécessiter des implémentations différentes. Cela signifie également qu’il peut y avoir de petites différences d’API dans les bibliothèques lors du ciblage de différentes plateformes .NET.

L’ensemble suivant d’erreurs que vous verrez dans l’exemple de courtier de haricot `Castle.Windsor` est lié aux API. Le projet .NET Core Bean opérateur utilise la même version de `Castle.Windsor` que le projet de .NET Framework ciblé (4.1.1), mais les implémentations de ces deux plateformes sont légèrement différentes.

Dans ce cas, vous voyez les problèmes suivants qui doivent être résolus :

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`n’est pas disponible sur .NET Core. Toutefois `Classes.FromAssemblyContaining` , l’API similaire est disponible. par conséquent, nous pouvons remplacer les deux utilisations `Classes.FromThisAssembly()` de par des `Classes.FromAssemblyContaining(t)`appels à `t` , où est le type effectuant l’appel.
1. De même, dans *Bootstrapper.cs*, `Castle.Windsor.Installer.FromAssembly`. Cela n’est pas disponible sur .NET Core. Au lieu de cela, cet appel peut `FromAssembly.Containing(typeof(Bootstrapper))`être remplacé par.

### <a name="updating-wcf-client-usage"></a>Mise à jour de l’utilisation du client WCF

Après avoir corrigé `Castle.Windsor` les différences, la dernière erreur de build restante dans le projet .net Core `BeanTraderServiceClient` Bean opérateur est que ( `DuplexClientBase`qui dérive de `Open` ) n’a pas de méthode. Cela n’est pas surprenant, car il s’agit d’une API qui a été mise en surbrillance par l’analyseur de portabilité .NET au début de ce processus de migration. `BeanTraderServiceClient` Toutefois, nous allons attirer notre attention sur un problème plus important. Ce client WCF a été généré automatiquement par l’outil [Svcutil. exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .

**Les clients WCF générés par Svcutil sont destinés à être utilisés sur .NET Framework.**

Les solutions qui utilisent des clients WCF générés par Svcutil devront régénérer les clients compatibles .NET Standard pour une utilisation avec .NET Core. L’une des principales raisons pour lesquelles les anciens clients ne fonctionneront pas est qu’ils dépendent de la configuration des applications pour définir des liaisons et des points de terminaison WCF. Étant donné que les API .NET Standard WCF peuvent fonctionner sur plusieurs plateformes (où les API System. configuration ne sont pas disponibles), les clients WCF pour les scénarios .NET Core et .NET Standard doivent définir des liaisons et des points de terminaison par programme plutôt que dans la configuration.

En fait, toute utilisation du client WCF qui dépend de `<system.serviceModel>` la section App. config (qu’elle soit créée avec Svcutil ou manuellement) doit être modifiée pour fonctionner sur .net core.

Il existe deux façons de générer automatiquement des clients WCF compatibles .NET Standard :

- L' `dotnet-svcutil` outil est un outil .net qui génère des clients WCF d’une manière similaire à la façon dont Svcutil fonctionnait précédemment.
- Visual Studio peut générer des clients WCF à l’aide de l’option de [référence de service Web WCF](../../core/additional-tools/wcf-web-service-reference-guide.md) de sa fonctionnalité services connectés.

L’une ou l’autre approche fonctionne bien. Vous pouvez également écrire le code client WCF vous-même. Pour cet exemple, j’ai choisi d’utiliser la fonctionnalité de service connecté de Visual Studio. Pour ce faire, cliquez avec le bouton droit sur le projet *BeanTraderClient. Core* dans l’Explorateur de solutions de Visual Studio, puis sélectionnez **Ajouter** > un**service connecté**. Ensuite, choisissez le fournisseur de référence de service Web WCF. Une boîte de dialogue s’affiche alors, dans laquelle vous pouvez spécifier l’adresse du service Web de l'`localhost:8080` opérateur du serveur principal Bean (si vous exécutez le serveur localement) et l’espace de noms que les types générés doivent utiliser (**BeanTrader. service**, par exemple).

![Boîte de dialogue service connecté de référence de service Web WCF](./media/convert-project-from-net-framework/connected-service-dialog.png)

Une fois que vous avez sélectionné le bouton **Terminer** , un nouveau nœud de services connectés est ajouté au projet et un fichier Reference.cs est ajouté sous ce nœud contenant le nouveau client WCF .NET standard pour l’accès au service Bean opérateur. Si vous examinez les `GetEndpointAddress` méthodes `GetBindingForEndpoint` ou dans ce fichier, vous verrez que les liaisons et les points de terminaison sont maintenant générés par programmation (au lieu de via la configuration de l’application). La fonctionnalité « Ajouter un Services connectés » peut également ajouter des références à certains packages System. ServiceModel dans le fichier projet, ce qui n’est pas nécessaire, car tous les packages WCF nécessaires sont inclus par le biais de Microsoft. Windows. Compatibility. Vérifiez si des éléments System. ServiceModel `<PackageReference>` supplémentaires ont été ajoutés dans le csproj et, le cas échéant, supprimez-les.

Notre projet a de nouvelles classes de client WCF maintenant (dans *Reference.cs*), mais il contient toujours les anciens (dans BeanTrader.cs). Il existe deux options à ce stade :

- Si vous souhaitez être en mesure de générer le projet de .NET Framework d’origine (parallèlement au nouveau .NET Core), vous pouvez utiliser un `<Compile Remove="BeanTrader.cs" />` élément dans le fichier csproj du projet .net Core afin que les versions .NET Framework et .net Core de l’application utilisent différents clients WCF. Cela présente l’avantage de laisser le projet de .NET Framework existant inchangé, mais présente l’inconvénient que le code qui utilise les clients WCF générés peut avoir besoin d’être légèrement différent dans le cas .NET Core que dans le projet .NET Framework. il est donc probable que `#if` vous deviez utiliser des directives pour compiler de façon conditionnelle une utilisation du client WCF (en créant des clients, par exemple) pour qu’ils fonctionnent de façon unidirectionnelle lorsqu’ils sont générés pour .net core. .NET Framework

- Si, en revanche, une certaine évolution du code dans le projet de .NET Framework existant est acceptable, vous pouvez supprimer tous les *BeanTrader.cs* ensemble. Étant donné que le nouveau client WCF est conçu pour .NET Standard, il fonctionnera à la fois dans les scénarios .NET Core et .NET Framework. Si vous générez pour .NET Framework en plus de .NET Core (soit par le biais du multi-ciblage, soit en utilisant deux fichiers csproj), vous pouvez utiliser ce nouveau fichier *Reference.cs* pour les deux cibles. Cette approche présente l’avantage que le code n’a pas besoin de bifurquer pour prendre en charge deux clients WCF différents. le même code sera utilisé partout. L’inconvénient est qu’il implique de modifier le projet de .NET Framework (vraisemblablement stable).

Dans le cas de l’exemple de courtier de haricot, vous pouvez apporter des modifications mineures au projet d’origine. si cela facilite la migration, procédez comme suit pour rapprocher l’utilisation du client WCF :

01. Ajoutez le nouveau fichier Reference.cs à la .NET Framework projet *BeanTraderClient. csproj* à l’aide du menu contextuel’ajouter un élément existant’de l’Explorateur de solutions. Veillez à ajouter « As Link » pour que le même fichier soit utilisé par les deux projets (par opposition à la copie du fichier C#). Si vous générez pour .NET Core et .NET Framework avec un seul csproj (à l’aide du multi-ciblage), cette étape n’est pas nécessaire.

01. Supprimez *BeanTrader.cs*.

01. Le nouveau client WCF est similaire à l’ancien, mais un certain nombre d’espaces de noms dans le code généré sont différents. Pour cette raison, il est nécessaire de mettre à jour le projet afin que les types de clients WCF soient utilisés à partir de BeanTrader. service (ou du nom d’espace de noms que vous avez choisi) au lieu de BeanTrader. Model ou sans espace de noms. La génération de *BeanTraderClient. Core. csproj* vous aidera à identifier l’endroit où ces modifications doivent être apportées. Les correctifs seront nécessaires en C# et dans les fichiers sources XAML.

01. Enfin, vous découvrirez qu’il y a une erreur dans *BeanTraderServiceClientFactory.cs* , car les constructeurs disponibles pour `BeanTraderServiceClient` le type ont changé. Il était possible de fournir un `InstanceContext` argument (qui a été créé à l’aide `CallbackHandler` d’un `Castle.Windsor` à partir du conteneur IOC). Les nouveaux constructeurs créent de nouveaux `CallbackHandler`. Toutefois, il existe des constructeurs dans `BeanTraderServiceClient`le type de base de qui correspondent à ce que vous souhaitez. Étant donné que le code client WCF généré automatiquement se trouve dans des classes partielles, vous pouvez facilement l’étendre. Pour ce faire, créez un nouveau fichier appelé *BeanTraderServiceClient.cs* , puis créez une classe partielle portant ce même nom (à l’aide de l’espace de noms BeanTrader. service). Ajoutez ensuite un constructeur au type partiel comme indiqué ici.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Avec ces modifications apportées, l’exemple de courtier Bean utilisera désormais un nouveau client WCF compatible avec la .NET Standard. vous pouvez donc utiliser `Open` `await OpenAsync` à la place le correctif final pour modifier l’appel dans *TradingService.cs* .

Avec les problèmes WCF résolus, la version .NET Core de l’exemple de courtier de haricot est désormais générée correctement.

## <a name="runtime-testing"></a>Test du Runtime

Il est facile d’oublier que le travail de migration n’est pas effectué dès que le projet est généré proprement sur .NET Core. Il est également important de garder le temps de tester l’application portée. Une fois que les opérations sont correctement générées, assurez-vous que l’application s’exécute et fonctionne comme prévu, en particulier si vous utilisez des packages ciblant .NET Framework.

Nous allons essayer de lancer l’application de l’opérateur de l’opérateur du rôle de haricot et de voir ce qui se passe. L’application n’a pas beaucoup de succès avant d’échouer avec l’exception suivante.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

Cela paraît logique, bien sûr. N’oubliez pas que WCF n’utilise plus la configuration d’application, de sorte que l’ancienne section System. serviceModel du fichier app. config doit être supprimée. Le client WCF mis à jour contient toutes les mêmes informations dans son code, donc la section de configuration n’est plus nécessaire. Si vous souhaitez que le point de terminaison WCF soit configurable dans App. config, vous pouvez l’ajouter en tant que paramètre d’application et mettre à jour le code du client WCF pour récupérer le point de terminaison du service WCF à partir de la configuration.

Après avoir supprimé la section System. serviceModel du *fichier app. config*, l’application se lance mais échoue avec une autre exception quand un utilisateur se connecte.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

L’API non prise en charge `Func<T>.BeginInvoke`est. Comme expliqué dans [dotnet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940), .net Core ne prend pas `BeginInvoke` en `EndInvoke` charge les méthodes et sur les types délégués en raison des dépendances de communication à distance sous-jacentes. Ce problème et son correctif sont expliqués plus en détail dans le billet de blog [migration Delegate. BeginInvoke pour .net Core](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) , mais l’essentiel est `BeginInvoke` que `EndInvoke` les appels et doivent être `Task.Run` remplacés par (ou des alternatives Async, si possible). En appliquant la solution générale ici `BeginInvoke` , l’appel peut être remplacé `Invoke` par un appel `Task.Run`lancé par.

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

Après la suppression `BeginInvoke` de l’utilisation, l’application de l’opérateur de haricot s’exécute correctement sur .net Core !

![Opérateur Bean s’exécutant sur .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Toutes les applications étant différentes, les étapes spécifiques nécessaires à la migration de vos propres applications vers .NET Core peuvent varier. Mais j’espère que l’exemple Bean commerçant illustre le flux de travail général et les types de problèmes qui peuvent se produire. Et, en dépit de la longueur de cet article, les modifications réelles nécessaires dans l’exemple d’opérateur Bean pour le rendre opérationnel sur .NET Core étaient relativement limitées. De nombreuses applications migrent vers .NET Core de la même façon ; avec des modifications de code limitées ou même non nécessaires.
