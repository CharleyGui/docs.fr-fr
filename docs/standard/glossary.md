---
title: Glossaire .NET
description: Découvrez la signification de certains termes utilisés dans la documentation .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: ed4dceed1a3f39c5c4ce7a278efc37bb38ed0d94
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344207"
---
# <a name="net-glossary"></a>Glossaire .NET

L’objectif principal de ce glossaire est de préciser la signification de certains termes et acronymes qui apparaissent fréquemment dans la documentation .NET sans y être définis.

## <a name="aot"></a>AOT

Compilateur Ahead Of Time.

Semblable au compilateur [JIT](#jit), ce compilateur convertit également le langage [IL](#il) en code machine. Contrairement à la compilation JIT, la compilation AOT se produit avant que l’application ne soit exécutée et est généralement effectuée sur une autre machine. Étant donné que les chaînes d’outil AOT ne se compilent pas au moment de l’exécution, elles n’ont pas besoin de réduire le temps consacré à la compilation. Ainsi, elles peuvent dédier plus de temps à l’optimisation. Étant donné que le contexte d’AOT est l’ensemble de l’application, le compilateur AOT effectue également une liaison entre modules et une analyse de la totalité du programme, ce qui signifie que toutes les références sont suivies et qu’un seul exécutable est produit.

Consultez [CoreRT](#corert) et [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

Implémentation ASP.NET d’origine fournie avec .NET Framework.

ASP.NET est parfois un terme général qui désigne les deux implémentations d’ASP.NET, y compris ASP.NET Core. C’est le contexte qui détermine la signification véhiculée par le terme. Reportez-vous à ASP.NET 4.x lorsque vous voulez préciser que vous n’utilisez pas ASP.NET pour signifier les deux implémentations.

Voir [Documentation d’ASP.NET](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Une mise en œuvre interplateforme, haute performance et open source de ASP.NET construite sur .NET Core.

Voir [Documentation ASP.NET Core](/aspnet/#pivot=core).

## <a name="assembly"></a>assembly

Un fichier *.dll*/*.exe* qui peut contenir une collection d’API qui peuvent être appelés par des applications ou d’autres assemblages.

Un assembly peut inclure des types comme des interfaces, des classes, des structures, des énumérations et des délégués. Les assemblys qui se trouvent dans le dossier *bin* d’un projet sont parfois appelés *binaires*. Voir aussi [bibliothèque](#library).

## <a name="clr"></a>CLR

Common Language Runtime.

La signification exacte dépend du contexte, mais Common Language Runtime se réfère généralement à l’exécution de .NET Framework. Le CLR gère l’allocation et la gestion de la mémoire. Le CLR est également une machine virtuelle qui non seulement exécute des applications, mais génère et compile également du code à la volée à l’aide d’un compilateur [JIT.](#jit) L’implémentation CLR Microsoft actuelle est Windows uniquement.

## <a name="coreclr"></a>CoreCLR

.NET Core Common Language Runtime.

Ce CLR repose sur la même base de code que le CLR. À l’origine, CoreCLR était le runtime de Silverlight et était conçu pour s’exécuter sur plusieurs plateformes, notamment Windows et OS X. CoreCLR fait désormais partie de .NET Core et représente une version simplifiée du CLR. C’est toujours un runtime [multiplateforme](#cross-platform), qui prend désormais en charge de nombreuses distributions Linux. CoreCLR est également une machine virtuelle avec des capacités JIT et d’exécution de code.

## <a name="corefx"></a>CoreFX

Bibliothèque de classes de base .NET Core

Un ensemble de bibliothèques qui composent le système. \* (et dans une mesure\*limitée Microsoft. ) namespaces. La bibliothèque de classes de base est un framework de niveau inférieur à usage général sur lequel reposent les frameworks d’applications de niveau supérieur, tels qu’ASP.NET Core. Le code source du .NET Core BCL est contenu dans le [référentiel .NET Core runtime](https://github.com/dotnet/runtime). Toutefois, la plupart des API .NET Core étant également disponibles dans .NET Framework, vous pouvez considérer CoreFX comme une duplication (fork) de la bibliothèque de classes de base .NET Framework.

## <a name="corert"></a>CoreRT

Runtime .NET Core.

Contrairement à CLR/CoreCLR, CoreRT n’est pas une machine virtuelle, ce qui signifie qu’il n’inclut pas les fonctionnalités de génération et d’exécution de code à la volée en raison de l’absence d’un compilateur [JIT](#jit). Il comprend toutefois le [GC](#gc) et la capacité d’identification de type temps d’exécution (RTTI) et de réflexion. Toutefois, son système de type est conçu pour que les métadonnées de réflexion ne soient pas nécessaires. Ne pas exiger de métadonnées permet d’avoir une chaîne d’outils [AOT](#aot) qui peut relier les métadonnées superflues et (plus important encore) identifier le code que l’application n’utilise pas. CoreRT est en cours de développement.

Voir [Intro à .NET Native et CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>interplateformes

La possibilité de développer et d’exécuter une application qui peut être utilisée sur plusieurs systèmes d’exploitation différents, tels que Linux, Windows et iOS, sans avoir à réécrire spécifiquement pour chacun d’eux. Cela permet la réutilisation et la cohérence du code entre les applications sur différentes plates-formes.

## <a name="ecosystem"></a>écosystème

Tous les logiciels d’exécution, outils de développement et ressources de communautés qui permettent de générer et d’exécuter des applications pour une technologie donnée.

Le terme « écosystème .NET » diffère des termes tels que « pile .NET » en ce sens qu’il inclut les bibliothèques et les applications tierces. Voici un exemple dans une phrase :

- « L’objectif de [.NET Standard](#net-standard) est d’établir une meilleure uniformité dans l’écosystème .NET. »

## <a name="framework"></a>framework

En général, ensemble complet d’API qui facilite le développement et le déploiement d’applications basées sur une technologie particulière. Selon ce sens général, ASP.NET Core et Windows Forms sont des exemples de frameworks d’application. Voir aussi [bibliothèque](#library).

Le mot « framework » a une signification technique plus spécifique dans les termes suivants :

- [.NET Framework](#net-framework)
- [cadre cible](#target-framework)
- [TFM (moniker de la version cible de .Net Framework)](#tfm)

Dans la documentation existante, « framework » fait parfois référence à une [implémentation de .NET](#implementation-of-net). Par exemple, un article peut appeler .NET Core un framework. Nous envisageons d’éliminer de la documentation cet usage qui prête à confusion.

## <a name="gc"></a>GC

Garbage collector.

Le garbage collector est une implémentation de la gestion automatique de la mémoire.  Le GC libère la mémoire occupée par les objets qui ne sont plus en cours d’utilisation.

Consultez [Nettoyage de la mémoire](garbage-collection/index.md).

## <a name="il"></a>IL

Langage intermédiaire.

Les langages .NET de haut niveau, tels que C#, se compilent en un jeu d’instructions indépendant du matériel, qui est appelé Langage intermédiaire (IL). IL est parfois appelé MSIL (Microsoft IL) ou CIL (Common IL).

## <a name="jit"></a>JIT

Compilateur juste-à-temps.

Semblable au compilateur [AOT](#aot), ce compilateur convertit le langage [IL](#il) en code machine que le processeur comprend. Contrairement à la compilation AOT, la compilation JIT se produit à la demande et est effectuée sur la machine sur laquelle le code doit s’exécuter. Étant donné que la compilation JIT se produit pendant l’exécution de l’application, la compilation fait partie du temps d’exécution. Ainsi, les compilateurs JIT doivent trouver un équilibre entre le temps consacré à l’optimisation du code et les économies pouvant découler du code résultant. Toutefois, un compilateur JIT connaît le matériel réel et peut éviter aux développeurs d’avoir à transmettre différentes implémentations.

## <a name="implementation-of-net"></a>implémentation de .NET

Une mise en œuvre de .NET comprend :

- Un ou plusieurs runtimes. Exemples : CLR, CoreCLR, CoreRT.
- Une bibliothèque de classes qui implémente une version de .NET Standard et qui peut inclure des API supplémentaires. Exemples : bibliothèque de classes de base .NET Framework, bibliothèque de classes de base .NET Core.
- Le cas échéant, un ou plusieurs frameworks d’application. Exemples : ASP.NET, Windows Forms et WPF) sont inclus dans .NET Framework.
- Le cas échéant, des outils de développement. Certains outils de développement sont partagés entre plusieurs implémentations.

Exemples d’implémentations de .NET :

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Plateforme Windows universelle (UWP)](#uwp)

## <a name="library"></a>bibliothèque

Ensemble d’API que peuvent appeler les applications ou d’autres bibliothèques. Une bibliothèque .NET est composée d’un ou plusieurs [assemblys](#assembly).

Les mots bibliothèque et [framework](#framework) sont souvent utilisés indifféremment.

## <a name="metapackage"></a>métapackage

Package NuGet ne disposant pas de sa propre bibliothèque, mais qui est simplement une liste de dépendances. Les packages inclus peuvent éventuellement établir l’API pour un framework cible.

Voir [Les paquets, les métapackages et les cadres](../core/packages.md)

## <a name="mono"></a>Mono

Mono est une implémentation de .NET open source [multiplateforme](#cross-platform) qui est principalement utilisée quand un runtime réduit est requis. C’est le temps d’exécution qui alimente les applications Xamarin sur Android, Mac, iOS, tvOS, et watchOS et se concentre principalement sur les applications qui nécessitent une petite empreinte.

Il prend en charge toutes les versions de .NET Standard publiées.

Historiquement, Mono implémentait l’API plus volumineuse de .NET Framework et émulait certaines des fonctionnalités les plus populaires sur Unix. Il est parfois utilisé pour exécuter des applications .NET qui s’appuient sur ces fonctionnalités sous Unix.

Mono est généralement utilisé avec un compilateur juste-à-temps, mais il comporte également un compilateur statique complet (compilation Ahead Of Time) qui est utilisé sur des plateformes comme iOS.

Pour en savoir plus sur Mono, consultez la [documentation Mono](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Terme générique désignant [.NET Standard](#net-standard), ainsi que toutes les charges de travail et les [implémentations de .NET](#implementation-of-net). Toujours entièrement capitalisé, jamais ".Net".

Consultez le [Guide de .NET](index.md).

## <a name="net-core"></a>.NET Core

Une mise en œuvre interplateforme, haute performance et open source de .NET. Inclut CoreCLR (Core Common Language Runtime), CoreRT (Core AOT Runtime, en cours de développement), la bibliothèque de classes de base et le SDK Core.

Consultez [.NET Core](../core/index.yml).

## <a name="net-core-cli"></a>CLI .NET Core

Chaîne d’outils multiplateforme pour développer des applications .NET Core.

Voir [.NET Core CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>SDK .NET Core

Ensemble de bibliothèques et d’outils qui permettent aux développeurs de créer des applications et des bibliothèques .NET Core. Inclut la [CLI .NET Core](#net-core-cli) pour la génération d’applications, les bibliothèques .NET Core et le runtime pour la génération et l’exécution d’applications et l’exécutable dotnet (*dotnet.exe*) qui exécute les commandes CLI et les applications.

Consultez [Vue d’ensemble du SDK .NET Core](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Implémentation de .NET qui s’exécute uniquement sur Windows. Inclut le Common Language Runtime (CLR), la bibliothèque de classes de base et des bibliothèques de framework d’application telles qu’ASP.NET, Windows Forms et WPF.

Consultez [Guide du .NET Framework](../framework/index.yml).

## <a name="net-native"></a>.NET Native

Chaîne d’outils de compilateur qui génère du code natif Ahead Of Time (AOT), par opposition à juste-à-temps (JIT).

La compilation se produit sur la machine du développeur, à l’image du fonctionnement d’un éditeur de liens et d’un compilateur C++. Elle supprime le code inutilisé et consacre plus de temps à l’optimisation du code. Elle extrait le code des bibliothèques et le fusionne dans le fichier exécutable. Le résultat est un module unique qui représente l’application entière.

UWP fut le premier framework d’application pris en charge par .NET Native. De nos jours, nous prenons en charge la génération d’applications console natives pour Windows, macOS et Linux.

Consultez [Présentation de .NET Native et CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="net-standard"></a>.NET Standard

Spécification formelle des API .NET disponibles dans chaque implémentation de .NET.

La spécification .NET Standard est parfois appelée bibliothèque dans la documentation. Comme une bibliothèque inclut des implémentations d’API, outre des spécifications (interfaces), il est trompeur d’appeler .NET Standard une « bibliothèque ». Nous prévoyons de supprimer cette utilisation de la documentation, sauf en référence au nom du métapackage .NET Standard (`NETStandard.Library`).

Consultez [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Génération (d’images) native

Vous pouvez considérer cette technologie comme un compilateur JIT persistant. Elle compile généralement le code sur la machine où le code est exécuté, mais la compilation se produit en règle générale au moment de l’installation.

## <a name="package"></a>package

Un package NuGet &mdash; ou simplement un package &mdash; est un fichier *.zip* qui comporte un ou plusieurs assemblys portant le même nom, ainsi que des métadonnées supplémentaires, telles que le nom de l’auteur.

Le fichier *.zip* porte l’extension *.nupkg* et peut contenir des composants, tels que des fichiers *.dll* et des fichiers *.xml*, à utiliser avec plusieurs frameworks et versions cibles. Quand ils sont installés dans une application ou une bibliothèque, les composants appropriés sont sélectionnés en fonction du framework cible spécifié par l’application ou la bibliothèque. Les composants qui définissent l’interface se trouvent dans le dossier *ref*, tandis que les ressources qui définissent l’implémentation se trouvent dans le dossier *lib*.

## <a name="platform"></a>plateforme

Système d’exploitation et le matériel sur lequel il s’exécute, tel que Windows, macOS, Linux, iOS et Android.

Voici quelques exemples d’utilisation dans des phrases :

- « .NET Core est une implémentation multiplateforme de .NET ».
- « Les profils de bibliothèque de classes portable représentent les plateformes Microsoft, alors que .NET Standard est indépendant de la plateforme. »

La documentation .NET utilise fréquemment « plateforme .NET » pour désigner soit une implémentation de .NET, soit la pile .NET y compris toutes les implémentations. Ces deux utilisations ayant tendance à être confondues avec la signification principale (système d’exploitation/matériel), nous envisageons de les supprimer de la documentation.

## <a name="runtime"></a>runtime

Environnement d’exécution d’un programme managé.

Le système d’exploitation fait partie de l’environnement d’exécution, mais pas du runtime .NET. Voici quelques exemples de runtimes .NET :

- CLR (Common Language Runtime)
- Core Common Language Runtime (CoreCLR)
- .NET Native (pour la plateforme Windows universelle)
- Runtime Mono

Parfois, la documentation de .NET utilise « runtime » pour désigner une implémentation de .NET. Par exemple, dans les phrases suivantes, « runtime » doit être remplacé par « implémentation » :

- « Les différents runtimes .NET implémentent des versions spécifiques de .NET Standard. »
- « Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. » (s’applique à .NET Standard)
- « Les différents runtimes .NET implémentent des versions spécifiques de .NET Standard. … Chaque version du runtime .NET publie la version .NET Standard la plus élevée qu’elle prend en charge... »

Nous envisageons de supprimer cette utilisation incohérente.

## <a name="stack"></a>pile

Ensemble de technologies de programmation qui sont utilisées conjointement pour générer et exécuter des applications.

L’expression « la pile .NET » fait référence à .NET Standard et à toutes les implémentations de .NET. L’expression « une pile .NET » peut faire référence à une implémentation de .NET.

## <a name="target-framework"></a>version cible de .NET Framework

Ensemble d’API sur lequel repose une bibliothèque ou une application .NET.

Une application ou une bibliothèque peut cibler une version de .NET Standard (par exemple, .NET Standard 2.0), qui est la spécification d’un ensemble standard d’API parmi toutes les implémentations de .NET. Une application ou une bibliothèque peut également cibler une version d’une implémentation spécifique de .NET ; dans ce cas, elle a accès aux API spécifiques à l’implémentation. Par exemple, une application qui cible Xamarin.iOS accède aux wrappers d’API iOS fournis par Xamarin.

Pour certains frameworks cibles (par exemple, .NET Framework), les API disponibles sont définies par les assemblys qu’une implémentation de .NET installe sur un système. Les API peuvent inclure des API de framework d’application (par exemple, ASP.NET ou WinForms). Pour les frameworks cibles basés sur le package (par exemple, .NET Standard et .NET Core), les API de framework sont définies par les packages installés dans l’application ou la bibliothèque. Dans ce cas, le framework cible spécifie implicitement un métapackage qui référence tous les packages constituant le framework.

Consultez [Versions cibles de .NET Framework](frameworks.md).

## <a name="tfm"></a>TFM

Moniker de la version cible de .Net Framework.

Format de jeton standardisé pour la spécification du framework cible d’une bibliothèque ou d’une application .NET. Les frameworks cibles sont en général référencés par un nom court, tel que `net462`. Les TFM de forme longue (par exemple, .NETFramework,Version=4.6.2) existent, mais ne sont généralement pas utilisés pour spécifier un framework cible.

Consultez [Versions cibles de .NET Framework](frameworks.md).

## <a name="uwp"></a>UWP

Plateforme Windows universelle.

Implémentation de .NET qui sert à générer des logiciels et des applications Windows tactiles modernes pour l’Internet des objets (IoT). Il est conçu pour unifier les différents types d’appareils que vous voudrez peut-être cibler, y compris les PC, tablettes, téléphones, et même la Xbox. UWP fournit de nombreux services, comme un magasin d’applications centralisé, un environnement d’exécution (AppContainer) et un ensemble d’API Windows à utiliser à la place de Win32 (WinRT). Les applications peuvent être écrites en C, C, Visual Basic et JavaScript. Lors de l’utilisation de C et Visual Basic, les API .NET sont fournis par .NET Core.

## <a name="see-also"></a>Voir aussi

- [Guide de voyage .NET](index.md)
- [Guide-cadre .NET](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [Vue d’ensemble ASP.NET](/aspnet/index#pivot=aspnet)
- [ASP.NET Core Overview](/aspnet/index#pivot=core) (Vue d’ensemble d’ASP.NET Core)
