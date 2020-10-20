---
title: Nouveautés de .NET Core pour Desktop
description: Découvrez .NET Core, les différences entre .NET Core et .NET Framework, ainsi que les nouvelles fonctionnalités qui ont été ajoutées.
ms.date: 05/12/2020
ms.openlocfilehash: 796facaf8cd4f0d23fbcd04b90cb78fb28ebc465
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223641"
---
# <a name="whats-new-with-net-core-for-desktop"></a>Nouveautés de .NET Core pour Desktop

À compter de .NET Core 3,0, .NET Core prend en charge Windows Forms et WPF. À présent, vous avez le choix entre .NET Framework et .NET Core pour vos applications de bureau. Ce chapitre décrira ce qu’est .NET Core et quels sont ses avantages pour les applications de bureau.

## <a name="the-motivation-behind-net-core"></a>Motivation derrière .NET Core

Depuis son lancement dans 2002, .NET Framework a évolué au cours des années pour prendre en charge de nombreuses technologies comme Windows Forms, ASP.NET, Entity Framework, le Windows Store et bien d’autres. Toutes sont différentes par nature. Par conséquent, Microsoft s’approche de cette évolution en acceptant des parties de la .NET Framework et en créant une pile d’applications différente pour chaque technologie. De cette façon, les fonctionnalités de développement peuvent être personnalisées pour les besoins de la pile spécifique, ce qui optimise le potentiel de chaque plateforme. Cela mène à la fragmentation sur les versions des .NET Framework gérées par différentes équipes indépendantes. Toutes ces piles ont une structure commune, contenant un modèle d’application, une infrastructure et un Runtime, mais elles diffèrent dans l’implémentation de chacune de ces parties.

Si vous ne ciblez qu’une seule de ces plateformes, vous pouvez utiliser ce modèle. Toutefois, dans de nombreux cas, vous pouvez avoir besoin de plusieurs plateformes cibles dans la même solution. Par exemple, votre application peut avoir une partie administrateur du bureau, un site Web destiné aux clients qui partage la logique principale exécutée sur un serveur, et même un client mobile. Dans ce cas, vous avez besoin d’une expérience de codage unifiée qui peut couvrir tous ces verticaux .NET.

Au moment de la publication de Windows 8, le concept de bibliothèques de classes portables (classes portables) est né. À l’origine, la .NET Framework a été conçue en partant du principe qu’elle serait toujours déployée en tant qu’unité unique, donc la [factorisation](https://wikipedia.org/wiki/Decomposition_(computer_science)) n’était pas un problème. Pour faire face au problème de partage de code entre les verticaux, la force motrice était de savoir comment refactoriser l’infrastructure. L’idée des contrats est de fournir une surface d’exposition d’API bien factorisée. Les contrats sont simplement des assemblys avec lesquels vous compilez et qui sont conçus avec un facteur approprié pour prendre en charge les dépendances entre eux.

Cela a pour conséquence de raisonner sur les différences d’API entre les verticaux au niveau de l’assembly, par opposition au niveau d’API individuel que nous avions auparavant. Cet aspect active une expérience de bibliothèque de classes qui peut cibler plusieurs verticaux, également appelés bibliothèques de classes portables.

![Historique des versions de .NET Framework](./media/whats-new-dotnet-core/release-history.png)

Avec la bibliothèque de classes portable, l’expérience de développement est unifiée en fonction de la forme de l’API. Et le plus grand besoin de créer des bibliothèques s’exécutant sur des verticaux différents est également traité. Mais il y a un grand défi : les API sont portables uniquement lorsque l’implémentation est avancée sur toutes les verticales.

Une meilleure approche consiste à unifier les implémentations entre les verticaux en fournissant une implémentation bien factorisée au lieu d’une vue bien factorisée. Il est beaucoup plus simple de demander à chaque équipe qui possède un composant spécifique de réfléchir à la façon dont ses API fonctionnent dans toutes les verticales que de tenter de fournir rétroactivement une pile d’API cohérente par-dessus. C’est là qu’intervient .NET Standard. Pour plus d’informations, consultez la section suivante.

Une autre grande difficulté consiste à déployer le .NET Framework. Le .NET Framework est une infrastructure à l’ensemble de l’ordinateur. Toute modification apportée à cette application affecte toutes les applications qui en dépendent. Bien que ce modèle de déploiement présente de nombreux avantages, tels que la réduction de l’espace disque et l’accès centralisé aux services, il présente des pièges.

Pour commencer, il est difficile pour les développeurs d’applications de prendre une dépendance sur un Framework récemment publié. Ils doivent prendre une dépendance sur le système d’exploitation le plus récent ou fournir un programme d’installation d’application qui installe le .NET Framework avec l’application. Si vous êtes un développeur Web, vous n’avez peut-être même pas cette option, car le service informatique établit la version prise en charge du serveur.

Même si vous êtes prêt à utiliser un programme d’installation pour enchaîner dans le programme d’installation de .NET Framework, vous constaterez peut-être que la mise à niveau du .NET Framework peut interrompre d’autres applications.

Malgré les efforts nécessaires pour fournir des versions à compatibilité descendante de l’infrastructure, des modifications compatibles peuvent perturber les applications. Par exemple, l’ajout d’une interface à un type existant peut modifier la manière dont ce type est sérialisé et provoquer des problèmes de rupture en fonction du code existant. Étant donné que la base .NET Framework installée est énorme, la lutte contre ces scénarios de simulation ralentit le rythme des innovations au sein du .NET Framework.

Pour résoudre tous ces problèmes, Microsoft a développé .NET Core pour aborder l’évolution de la plate-forme .NET.

## <a name="introduction-to-net-core"></a>Introduction à .NET Core

.NET Core est l’évolution de la technologie .NET de Microsoft dans une plateforme modulaire, multiplateforme, open source et Cloud. Il s’exécute sur Windows, macOS et Linux, avec des plans pour s’exécuter également sur des architectures ARM comme Android et IoT.

L’objectif de .NET Core est de fournir une plateforme unifiée pour tous les types d’applications, notamment les applications Windows, multiplateforme et mobiles. [.NET standard](../../standard/net-standard.md) l’active en fournissant des API de base partagées, qui sont requises par chaque modèle d’application, et exclut toute API spécifique au modèle d’application.

Ce Framework offre aux applications de nombreux avantages en termes d’efficacité et de performances, ce qui simplifie l’empaquetage et le déploiement dans les différentes plateformes prises en charge.

Les avantages de .NET Core proviennent de ces trois caractéristiques :

- **Multiplateforme :** Elle permet l’exécution d’applications sur différentes plateformes (Windows, macOS et Linux).
- **Open Source :** la plateforme .net Core est open source et disponible par le biais de GitHub, ce qui favorise la transparence et les contributions de la communauté.
- **Pris en charge :** Microsoft prend officiellement en charge .NET Core.

À compter de .NET Core 3,0, en plus de la prise en charge existante du Web et du Cloud, il y a également une prise en charge pour les domaines de bureau, IoT et IA. L’objectif de cette infrastructure est impressionnant : pour cibler chaque type de développement .NET présent et futur. Microsoft envisage d’effectuer cette vision avec .NET 5 à la fin du 2020. Le nom « Core » a été supprimé pour renforcer son unicité dans le monde .NET.

![Tous les domaines de .NET 5](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework et .NET Core

Maintenant que vous comprenez la pertinence de .NET Core au sein de la stratégie Microsoft pour .NET, vous vous demandez peut-être ce qui se passe avec .NET Framework. Vous pouvez poser des questions telles que : êtes-vous obligé de l’abandonner ? Va-t-il disparaître ? Quelles sont mes options pour moderniser les applications que j’ai sur .NET Framework ?

Dans 2019, la dernière version de la **.NET Framework-4,8** a été publiée. Elle comprenait trois améliorations majeures pour les applications de bureau :

- **Contrôles de navigateur et de média modernes**: aujourd’hui, les applications de bureau .NET utilisent Internet Explorer et le lecteur Windows Media pour illustrer le HTML et la lecture de fichiers multimédias. Étant donné que ces contrôles hérités n’affichent pas le HTML le plus récent ou lisent les fichiers multimédias les plus récents, de nouveaux contrôles ont été ajoutés pour tirer parti de Microsoft Edge et des lecteurs multimédia récents qui prennent en charge les normes les plus récentes.
- **Accès aux contrôles UWP**: UWP contient de nouveaux contrôles qui tirent parti des fonctionnalités Windows les plus récentes et des affichages tactiles. Vous n’avez pas besoin de réécrire vos applications pour utiliser ces nouvelles fonctionnalités et contrôles. vous pouvez donc utiliser ces nouvelles fonctionnalités dans votre code WPF ou Windows Forms existant.
- **Améliorations**de la haute résolution : la résolution des affichages passe à des résolutions de 4 Ko et de 8 Ko. Ainsi, .NET Framework 4,8 ajoute de nouvelles améliorations HDPI pour s’assurer que vos applications Windows Forms et WPF existantes peuvent paraître intéressantes sur ces nouveaux affichages.

Étant donné que .NET Framework est installé sur des millions d’ordinateurs, Microsoft continuera à le prendre en charge mais n’ajoutera pas de nouvelles fonctionnalités.

.NET Core est la version open source, multiplateforme et à déplacement rapide de .NET. En raison de sa nature côte à côte, il peut apporter des modifications sans crainte de perturber une application. Cela signifie que .NET Core obtiendra de nouvelles API et fonctionnalités de langage au fil du temps, ce qui .NET Framework pas. En outre, **.net Core** possède déjà des fonctionnalités qui étaient impossibles pour .NET Framework, telles que :

- **Versions côte à côte de .net prenant en charge Windows Forms et WPF**: cela résout le problème des effets secondaires lors de la mise à jour de la version de l’infrastructure de l’ordinateur. Plusieurs versions de .NET Core peuvent être installées sur le même ordinateur et chaque application spécifie la version de .NET Core qu’elle doit utiliser. Encore plus, vous pouvez développer et exécuter des Windows Forms et WPF en plus de .NET Core.
- **Incorporer .net directement dans une application**: vous pouvez déployer .net core dans le cadre de votre package d’application. Cela vous permet de tirer parti de la dernière version, des fonctionnalités et des API sans devoir attendre l’installation d’une version spécifique sur l’ordinateur.
- **Tirez parti des fonctionnalités de .net Core**: .net Core est la version rapide et open source de .net. Sa nature côte à côte permet d’introduire rapidement de nouvelles API novatrices et des améliorations de bibliothèques de classes de base (BCL) sans risque d’interruption de la compatibilité. Désormais, les Windows Forms et les applications WPF peuvent tirer parti des dernières fonctionnalités de .NET Core, qui incluent également des correctifs plus fondamentaux pour les performances d’exécution, la prise en charge de la haute résolution, etc.

Une partie essentielle de la feuille de route pour Microsoft était de faciliter la migration des applications vers .NET Core et à l’avenir vers .NET 5. Toutefois, si vous avez des applications de .NET Framework existantes, vous ne devriez pas vous sentir à passer à .NET Core. .NET Framework sera entièrement pris en charge et fera toujours partie de Windows. Toutefois, si vous souhaitez utiliser les nouvelles fonctionnalités de langage et les API à l’avenir, vous devrez déplacer vos applications vers .NET Core.

Pour les nouvelles applications de bureau, nous vous recommandons de démarrer directement sur .NET Core. Elle est légère et multiplateforme, s’exécute côte à côte, offre des performances élevées et s’adapte parfaitement aux architectures des conteneurs et des microservices.

![Vous pouvez mettre à jour vos applications de .NET Framework à l’aide de la dernière version de .NET Framework ou porter vos applications sur .NET Core](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard et PCL

[.NET standard](../../standard/net-standard.md) est une spécification formelle des API .net qui sont destinées à être disponibles sur toutes les implémentations de .net. La motivation derrière .NET Standard consiste à établir une meilleure uniformité dans l’écosystème .NET. .NET Standard est une spécification d’API .NET qui constituent un ensemble uniforme de contrats pour la compilation de votre code. Ces contrats sont implémentés dans chaque version de .NET, ce qui permet de portabilité entre les différentes implémentations de .NET.

.NET Standard permet les scénarios clés suivants :

- Définit un ensemble uniforme d’API de bibliothèques de classes de base pour toutes les implémentations .NET à implémenter, indépendamment de la charge de travail.
- Permet aux développeurs de générer des bibliothèques portables utilisables sur toutes les implémentations de .NET, à l’aide de ce même ensemble d’API.

.NET Standard est l’évolution de classes portables et la liste suivante présente les différences fondamentales entre .NET Standard et classes portables :

- .NET Standard est un ensemble d’API organisée, choisi par Microsoft. Classes portables ne sont pas.
- Les API que contient un PCL dépendent des plateformes que vous choisissez de cibler lors de sa création. Cela rend une bibliothèque de classes portable uniquement partageable pour les cibles spécifiques que vous choisissez.
- .NET Standard est indépendant de la plateforme, il peut s’exécuter n’importe où, sur Windows, macOS, Linux, etc.
- Classes portables peut également être exécuté sur plusieurs plateformes, mais elles ont une portée plus limitée. Classes portables peut uniquement cibler un ensemble limité de plateformes.

## <a name="new-desktop-features-in-net-core"></a>Nouvelles fonctionnalités de bureau dans .NET Core

### <a name="support-for-windows-forms-and-wpf"></a>Prise en charge de Windows Forms et WPF

Windows Forms et WPF font partie de .NET Core depuis la version 3,0. Les deux frameworks de présentation sont pour Windows uniquement, donc ils ne sont pas multiplateformes. Vous pouvez considérer WPF comme une couche riche sur DirectX et Windows Forms comme une couche plus fine sur GDI+. WPF et Windows Forms font l’essentiel de l’exposition et de l’exercice de la plupart des fonctionnalités de l’application de bureau dans Windows. Ainsi, Windows Forms et WPF sont disponibles pour .NET Core et .NET Framework. Vous pouvez maintenant démarrer vos applications de bureau ciblant .NET Core et migrer vos applications existantes de .NET Framework vers .NET Core.

Une nouvelle version de .NET Standard, version 2,1, a été publiée en même temps que .NET Core 3,0. Comme prévu, les versions de .NET Core 3. x prennent en charge .NET Standard 2,1 et versions antérieures.

En outre, il est important de noter que les implémentations Windows Forms et WPF pour .NET Core sont Open source.

### <a name="xaml-islands"></a>XAML Islands

Les [îlots XAML](/windows/apps/desktop/modernize/xaml-islands) sont un ensemble de composants permettant aux développeurs d’utiliser les nouveaux contrôles Windows 10 (contrôles XAML UWP) dans leurs applications WPF natives, Windows Forms et natives (comme MFC). Vous pouvez avoir vos « îlots » de contrôles XAML UWP partout où vous le souhaitez au sein de vos applications Win32.

Ces îlots XAML sont possibles, car Windows 10, version 1903 introduit un ensemble d’API qui permet d’héberger le contenu XAML UWP dans Windows Win32 à l’aide des gestionnaires Windows (HWND). Notez que seules les applications qui s’exécutent sur Windows 10 1903 et versions ultérieures peuvent utiliser des îlots XAML.

Pour faciliter la création d’îlots XAML pour les développeurs Windows Forms et WPF, le kit de développement logiciel de la communauté Windows introduit un ensemble de wrappers .NET dans plusieurs packages NuGet. Ces wrappers sont les contrôles encapsulés et d’hébergement :

- Les contrôles encapsulés [WebView](/windows/communitytoolkit/controls/wpf-winforms/webview), [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible), [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas), [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)et [collection MapControl](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol) encapsulent certains contrôles XAML UWP dans des contrôles Windows Forms ou WPF, masquant ainsi les concepts UWP pour ces développeurs.
- Le contrôle [WindowsXamlHost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) pour Windows Forms et WPF permet aux autres contrôles XAML UWP non encapsulés et les contrôles personnalisés de pouvoir être chargés dans un îlot XAML.

### <a name="access-to-all-windows-10-apis"></a>Accès à toutes les API Windows 10

Windows 10 offre une grande quantité d’API disponibles pour les développeurs. Ces API donnent accès à un large éventail de fonctionnalités, telles que l’authentification, le Bluetooth, les rendez-vous et les contacts. Ces API sont désormais exposées via .NET Core et donnent aux développeurs Windows la possibilité de créer des applications de bureau puissantes en tirant parti des fonctionnalités présentes sur Windows 10.

### <a name="side-by-side-support-and-self-contained-exes"></a>Prise en charge côte à côte et exe autonomes

Le modèle de déploiement .NET Core est l’un des principaux avantages que les développeurs de postes de travail Windows rencontreront avec .NET Core. La possibilité d’installer .NET Core à l’échelle mondiale offre une grande partie des avantages de l’installation centrale et de la maintenance de .NET Framework, tout en ne nécessitant pas de mises à jour sur place.

Quand une nouvelle version de .NET Core est publiée, vous pouvez mettre à jour chaque application sur un ordinateur en fonction des besoins, sans que cela affecte les autres applications. Les nouvelles versions de .NET Core sont installées dans leurs propres répertoires et existent côte à côte.

Si vous devez déployer avec l’isolation, vous pouvez déployer .NET Core avec votre application. .NET Core regroupera votre application avec le Runtime .NET Core comme dans un exécutable unique.

Ces options de déploiement ont été demandées par les développeurs pendant beaucoup de temps, mais étaient difficiles à obtenir à l’aide de .NET Framework. L’architecture modulaire utilisée par .NET Core rend ces options de déploiement flexibles possibles.

### <a name="performance"></a>Performances

Depuis son démarrage, ciblant les charges de travail Web et Cloud, les performances de .NET Core ont été intégrées dans son ADN. Le code côté serveur doit être suffisamment performant pour satisfaire les scénarios de haute concurrence et les scores .NET Core aujourd’hui en tant que plate-forme Web de performances optimale sur le marché.

Vous pouvez tirer parti de ces améliorations de performances lorsque vous utilisez .NET Core pour créer une nouvelle génération d’applications de bureau.

## <a name="benefits-of-open-source"></a>Avantages de Open source

Quelques mots sur .NET Core étant Open source. La création d’une pile multiplateforme est une opération complexe qui nécessite l’interaction d’équipes spécialisées sur chacune des plateformes ciblées. Cet effort nécessite une grande collaboration à l’intérieur et à l’extérieur de Microsoft. En le rendant Open source et donc ouvert à la collaboration publique, vous bénéficiez de l’excellence du style de développement Agile, ce qui augmente la qualité, car les problèmes sont détectés par une communauté de développeurs très importante et active.

Il s’agit d’un facteur de réussite clé de .NET Core qui continuera d’accélérer le plan d’évolution mentionné précédemment : pour être la seule plateforme .NET dont n’importe quel développeur aura besoin pour créer n’importe quelle application.

>[!div class="step-by-step"]
>[Précédent](why-modern-applications.md) 
> [Suivant](migrate-modern-applications.md)
