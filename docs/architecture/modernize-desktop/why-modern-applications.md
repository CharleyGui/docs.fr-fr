---
title: Pourquoi des applications de bureau modernes
description: Découvrez les technologies de bureau telles que Windows Forms, WPF et UWP dans le monde moderne.
ms.date: 09/16/2019
ms.openlocfilehash: f8b70ba9e0ee97a6e0938e3219ecd0d2324248ae
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423277"
---
# <a name="why-modern-desktop-applications"></a>Pourquoi des applications de bureau modernes

## <a name="introduction"></a>Introduction

### <a name="a-story-of-one-company"></a>Histoire d’une entreprise

Dans les premières versions de 2000, une entreprise multinationale a commencé à développer une solution de bureau distribuée pour échanger des informations entre les différentes branches de l’entreprise et exécuter des opérations optimisées sur des unités centralisées. Ils ont choisi une nouvelle infrastructure appelée Windows Forms (également appelée WinForms) pour le développement d’applications. Au fil des années, le projet a évolué vers une application mature, bien testée et éprouvée, avec des centaines de milliers de lignes de code. Le temps passé et .NET Framework 2,0 n’est plus la nouvelle technologie à chaud. Les développeurs qui travaillent sur cette application sont confrontés à un dilemme. Ils souhaitent utiliser la dernière pile de technologies dans leur développement et faire en sorte que leur application s’affiche et « s’intègre ». En même temps, ils ne souhaitent pas jeter le produit exceptionnel qu’ils ont développé plus de 15 ans et réécrire l’application entière à partir de zéro.

### <a name="your-story"></a>Votre histoire

Vous pouvez vous trouver dans le même bateau, où vous avez des applications Windows Forms ou Windows Presentation Foundation (WPF) matures qui ont prouvé leur fiabilité au fil des années. Vous souhaiterez probablement continuer à utiliser ces applications depuis de nombreuses années. En même temps, étant donné que ces applications ont été écrites il y a quelque temps, elles peuvent manquer des fonctionnalités telles que l’apparence moderne, les performances, l’intégration avec de nouveaux appareils et les fonctionnalités de la plateforme, et ainsi de suite, ce qui leur donne une idée de « l’ancien Tech ». Il existe un autre problème qui peut vous concerner en tant que développeur. Lorsque vous travaillez sur les anciennes versions de .NET Framework et que vous conservez les applications qui ont été écrites un peu de temps, vous pouvez avoir l’impression de ne pas apprendre de nouvelles technologies et de créer des compétences techniques modernes. Si c’est votre histoire, ce livre est pour vous !

## <a name="desktop-applications-nowadays"></a>Applications de bureau de nos jours

Avant la hausse de l’Internet, les applications de bureau étaient la principale approche pour créer des systèmes logiciels. Les développeurs peuvent choisir n’importe quel langage de programmation, tel que COBOL, Fortran, VB6 ou C++. Mais lorsqu’ils ont développé de petits outils ou des architectures distribuées complexes, il s’agissait de toutes les applications de bureau.

Ensuite, les technologies Internet commençaient à dérouter le monde du développement et ont gagné plus d’ingénieurs, avec des avantages tels que le déploiement simple et les processus de distribution simplifiés. Le fait qu’une fois qu’une application Web a été déployée pour la production tous les utilisateurs obtenait des mises à jour automatiques a eu un impact considérable sur l’agilité des logiciels.

Toutefois, l’infrastructure Internet, les protocoles sous-jacents et les normes comme HTTP et HTML n’ont pas été conçus pour créer des applications complexes. En fait, le principal effort de développement ne faisait qu’un seul objectif : offrir aux applications Web les mêmes fonctionnalités que celles des applications de bureau, telles que la saisie rapide des données et la gestion des États.

Même si les applications Web et mobiles se sont développées à un rythme incroyable, pour certaines tâches, les applications de bureau contiennent toujours le nombre unique en termes d’efficacité et de performances. Cela explique pourquoi il existe des millions de développeurs qui créent leurs projets avec WPF et WinForms, et la quantité de ces applications croît constamment.

Voici quelques raisons pour choisir les applications de bureau dans votre développement :

- Les applications de bureau ont une meilleure interaction avec l’ordinateur de l’utilisateur.
- Les performances des applications de bureau pour les calculs complexes sont nettement supérieures à celles des applications Web.
- Il est possible d’exécuter une logique personnalisée côté client, mais beaucoup plus difficile avec une application Web.
- L’utilisation du multithreading est plus simple et plus efficace dans une application de bureau.
- La courbe d’apprentissage pour la conception d’interfaces utilisateur n’est pas abrupte. Et pour WinForms, il est tout à fait intuitif avec l’expérience de glisser-déplacer de Windows Forms Designer.
- Il est facile de commencer à coder et à tester vos algorithmes sans avoir à configurer une infrastructure de serveur ni à vous soucier des problèmes de connectivité, des pare-feu et de la compatibilité des navigateurs.
- Le débogage est puissant par rapport au débogage Web.
- L’accès aux périphériques matériels, tels que les appareils photo, Bluetooth ou les lecteurs de carte, est simple.
- Étant donné que la technologie existe depuis longtemps, de nombreux experts et une base de connaissances sont disponibles pour le développement d’applications de bureau.

Ainsi, comme vous pouvez le voir, le développement pour le bureau est parfait pour de nombreuses raisons. La technologie est mature et a été testée, le cycle de développement est rapide, le débogage est puissant et sans doute, les applications de bureau ont moins de complexité et sont plus faciles à démarrer avec.

Microsoft a proposé de nombreuses technologies de bureau de l’interface utilisateur au cours des années de Win32 introduites dans 1995 to plateforme Windows universelle (UWP) commercialisées dans 2016.

![Technologies Microsoft Desktop](./media/why-modern-applications/microsoft-desktop-technologies.png)

D’après une enquête publiée par Telerik le 2016 avril, les technologies les plus populaires pour créer des applications de bureau Windows sont Windows Forms, WPF et UWP.

![Telerik Survey présentant Windows Forms, WPF et UWP en tant que technologies de bureau les plus populaires](./media/why-modern-applications/telerik-survey.png)

Vous pouvez développer dans n’importe lequel d’entre eux à l’aide de C# et Visual Basic, mais examinons de plus près.

### <a name="windows-forms"></a>Windows Forms

Publiée dans 2002, Windows Forms est une infrastructure gérée et est la technologie bureautique la plus ancienne et la plus utilisée, basée sur le moteur Windows Graphics Device Interface (GDI). Il offre une expérience de glisser-déplacer fluide pour le développement d’interfaces utilisateur dans Visual Studio.  En même temps, Windows Forms s’appuie sur le concepteur Visual Studio comme méthode principale de développement de l’interface utilisateur. par conséquent, la création de composants visuels à partir du code n’est pas évidente.

La liste suivante récapitule les principales caractéristiques de Windows Forms :

- Technologie mature avec un grand nombre d’exemples de code et de documentation.
- Concepteur puissant et productif. Ce n’est pas si commode de concevoir l’interface utilisateur à partir du code.
- Facile et intuitif à apprendre, grâce à l’expérience de glisser-déplacer du concepteur.
- Pris en charge sur n’importe quelle version de Windows.
- Pris en charge sur .NET Core 3,0 et versions ultérieures.

### <a name="wpf"></a>WPF

En fonction de la spécification du langage XAML, WPF favorise une séparation claire entre l’interface utilisateur et le code. XAML offre des fonctionnalités telles que la création de modèles, le style et la liaison, qui sont adaptées à la création d’applications volumineuses. Comme Windows Forms, il s’agit d’une infrastructure gérée, mais la conception est modulaire et réutilisable.

Voici les principales fonctionnalités de WPF :

- Technologie mature.
- Le concepteur est disponible, mais les développeurs préfèrent généralement créer la conception à partir du code à l’aide du XAML déclaratif.
- La courbe d’apprentissage est plus forte que Windows Forms.
- Pris en charge sur n’importe quelle version de Windows.
- Pris en charge sur .NET Core 3,0 et versions ultérieures.

### <a name="uwp"></a>UWP

UWP n’est pas seulement un Framework de présentation comme WPF et Windows Forms, mais il s’agit également d’une plateforme. Cette plateforme contient les éléments suivants :

- Son propre ensemble d’API (API Windows Runtime).
- Un nouveau système de déploiement (MSIX)
- Un modèle de cycle de vie d’application moderne (pour une faible consommation de batterie).
- Nouveau système de gestion des ressources (basé sur les fichiers PRI).

La plateforme a été créée pour prendre en charge tous les types de systèmes d’entrée (comme l’encre, le toucher, le boîtier, la souris, le clavier, le point de regard, etc.) dans tous les facteurs de forme avec des performances et une faible consommation de batterie à l’esprit. Pour ces raisons, l’interpréteur de commandes du système d’exploitation Windows 10 utilise des composants de la plateforme UWP.

![Structure UWP](./media/why-modern-applications/uwp-structure.png)

UWP contient une infrastructure de présentation XAML, comme WPF, mais elle présente quelques différences importantes, telles que :

- Les applications sont exécutées dans des conteneurs d’applications. Les conteneurs d’applications contrôlent les ressources auxquelles une application UWP peut accéder.
- Pris en charge uniquement sur Windows 10.
- Les applications peuvent être déployées via Microsoft Store pour faciliter leur déploiement.
- Conçu dans le cadre de l’API Windows Runtime.
- Contient un ensemble complet de contrôles intégrés enrichis et de contrôles supplémentaires disponibles par le biais des packages NuGet de la bibliothèque de l’interface utilisateur Microsoft (bibliothèque WinUI) mis à jour tous les quelques mois.

## <a name="a-tale-of-two-platforms"></a>Une histoire de deux plateformes

Au cours des 20 dernières années, tandis que les technologies de bureau de l’interface utilisateur augmentaient et suivent le chemin de Windows Forms au UWP, le matériel était également en évolution des unités PC à poids fort avec de petits moniteurs CRT vers des moniteurs haute résolution et des tablettes et des téléphones légers avec différentes techniques d’entrée de données telles que le toucher et l’encre. Ces modifications ont entraîné la création de deux concepts différents : une application de bureau et une application moderne. Une application moderne prend en compte différents facteurs de forme de périphérique, différentes méthodes d’entrée et de sortie, et tire parti des fonctionnalités de bureau modernes tout en s’exécutant sur un modèle d’exécution sandbox. L’application de bureau (traditionnelle) est, quant à elle, une application qui a besoin d’une interface utilisateur solide avec une haute densité de contrôles, qui est la mieux exploitée avec une souris et un clavier.

Le tableau suivant décrit les différences entre les deux concepts :

|   | Application moderne | Application de bureau |
| --- | --- | --- |
| Sécurité | L’exécution contient des &amp; notions de base importantes. Conçu dès le départ pour respecter la confidentialité de l’utilisateur, gérer la durée de vie de la batterie et concentrer la protection de l’appareil.  | &amp;Niveau de sécurité de l’administrateur de l’utilisateur. Vous disposez d’un accès natif au registre et aux dossiers de disque dur. |
| Déploiement | L’installation et les mises à jour sont gérées par la plateforme.   | MSI, mises à jour des programmes d’installation personnalisés &amp; . Traditionnellement une source de migraines pour les développeurs et les responsables informatiques.  |
| Distribution | Packages de distribution de distribution approuvés &amp; . La distribution est effectuée à partir d’une source approuvée et jamais à partir du Web.  | Web, &amp; distribution personnalisée SCCM. Aucun contrôle sur ce qui est installé, affecte l’ensemble de l’ordinateur.   |
| UI | Interface utilisateur moderne. Différents mécanismes d’entrée, encre, toucher, boîtier, clavier, souris, etc.  | Windows Forms, WPF, MFC. Conçu pour la souris et le clavier d’une interface utilisateur dense et pour obtenir la plus grande productivité à partir du bureau.  |
| Données | Premières données du Cloud avec Insights. Source de vérité dans le Cloud. Insights pour savoir ce qui se passe avec votre application et comment elle fonctionne.  | Données locales. Les applications de bureau traditionnelles nécessitent généralement des données locales.  |
| Conception | Conçu pour être réutilisé. Réutilisez à l’esprit les différentes plates-formes, le front-end et le back end, en exécutant des ressources dans de nombreux endroits, le cas échéant.  | Conçu pour Windows Desktop uniquement  |

Dans le cadre de l’engagement de fournir aux développeurs les meilleurs outils pour créer des applications, Microsoft met un grand effort pour mettre ces concepts en œuvre, ou nous pouvons même donner des plates-formes plus proches pour permettre aux développeurs de bénéficier du meilleur des deux mondes. Pour ce faire, Microsoft a effectué un effort bidirectionnel entre les deux plateformes.

![Effort bidirectionnel entre une application moderne et des applications de bureau](./media/why-modern-applications/bidirectional-effort.png)

1. Déplacez les scénarios d’application de bureau vers la plateforme d’application moderne. Le développement de bureau traditionnel est toujours populaire, car il résout certains scénarios. Il est logique de prendre ces scénarios de bureau courants et de les intégrer à la plateforme de bureau moderne pour rendre la plateforme entièrement efficace.

    ![Déplacez les scénarios d’application de bureau vers la plateforme d’application moderne](./media/why-modern-applications/desktop-to-modern.png)

1. Déplacez les fonctionnalités d’application modernes dans les applications de bureau. Pour les applications de bureau existantes qui ont besoin d’une méthode pour tirer parti des fonctionnalités modernes sans réécrire à partir de zéro, les fonctionnalités de la plateforme d’applications moderne sont transmises à l’application de bureau.

    ![Déplacer des fonctionnalités d’application modernes dans des applications de bureau](./media/why-modern-applications/modern-to-desktop.png)

Dans cet ouvrage, nous nous concentrerons sur la deuxième partie et montrons comment vous pouvez moderniser vos applications de bureau existantes.

## <a name="paths-to-modernization"></a>Chemins d’accès à moderniser

La structure de ce guide reflète trois axes différents pour accomplir la modernisation : fonctionnalités, déploiement et installation modernes.

### <a name="modern-features"></a>Fonctionnalités modernes

Imaginons que vous avez une application de Windows Forms opérationnelle qu’un représentant commercial de votre entreprise utilise pour remplir une commande client. Une nouvelle exigence est fournie pour permettre au client de signer la commande à l’aide d’un stylet. L’encrage est natif dans les systèmes d’exploitation et les technologies actuels, mais il n’était pas disponible lors du développement de l’application.

Ce chemin vous montrera comment tirer parti des fonctionnalités de bureau modernes dans le développement de postes de travail existant.

### <a name="deployment"></a>Déploiement

Les cycles de développement modernes ont souligné pour fournir de l’agilité sur la manière dont les nouvelles versions des applications sont déployées sur chaque utilisateur. Étant donné que les applications Windows Forms et WPF sont basées sur une version particulière du .NET Framework qui doivent être présentes sur l’ordinateur, elles ne peuvent pas tirer parti des nouvelles fonctionnalités de la version de .NET Framework sans l’intervention des personnes qui ont des effets secondaires sur les autres applications exécutées sur le même ordinateur. Il a limité le rythme d’innovation pour les développeurs qui les obligent à rester sur les versions obsolètes du .NET Framework.

Depuis le lancement de .NET Core 3,0, vous pouvez tirer parti d’une nouvelle approche de déploiement de plusieurs versions de .NET Core côte à côte et en spécifiant la version de .NET Core que chaque application doit cibler. De cette façon, vous pouvez utiliser les fonctionnalités les plus récentes d’une application tout en étant certain que vous n’allez pas interrompre les autres applications.

### <a name="installation"></a>Installation

Les applications de bureau s’appuient toujours sur une sorte de processus d’installation avant que l’utilisateur puisse commencer à les utiliser. Ce fait a introduit dans le jeu un ensemble de technologies, depuis MSI et ClickOnce vers des programmes d’installation personnalisés ou même un déploiement XCOPY. L’une de ces méthodes concerne les problèmes délicats, car les applications ont besoin d’un moyen d’accéder aux ressources partagées sur l’ordinateur. Parfois, l’installation doit accéder au registre pour insérer ou mettre à jour de nouvelles valeurs de clés, parfois pour mettre à jour les DLL partagées référencées par l’application principale. Cela provoque un soucis continu pour les utilisateurs, en créant cette perception qu’une fois que vous avez installé une application, votre ordinateur ne sera jamais le même, même si vous le désinstallez par la suite.

Dans ce livre, nous allons introduire une nouvelle façon d’installer des applications avec MSIX qui résout le problème décrit précédemment. Vous apprendrez comment vous pouvez facilement configurer un empaquetage, une installation et des mises à jour pour votre application.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](whats-new-dotnet-core.md)
