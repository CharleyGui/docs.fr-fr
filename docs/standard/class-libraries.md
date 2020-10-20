---
title: Bibliothèques de classes .NET
description: Découvrez dans quelle mesure les bibliothèques de classes .NET vous permettent de grouper des fonctionnalités utiles en modules utilisables par plusieurs applications.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: 35e408ed3552550f19879409128784b2513e56c8
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224266"
---
# <a name="net-class-libraries"></a>Bibliothèques de classes .NET

Les bibliothèques de classes représentent le concept de [bibliothèque partagée](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pour .NET. Elles vous permettent d’inclure des fonctionnalités utiles dans des modules utilisables par plusieurs applications. Elles peuvent également servir à charger des fonctionnalités qui ne sont pas nécessaires ou connues au démarrage de l’application. Les bibliothèques de classes sont décrites à l’aide du [format de fichier d’assembly .NET](assembly/file-format.md).

Il existe trois types de bibliothèques de classes que vous pouvez utiliser :

* Les bibliothèques de classes **spécifiques d’une plateforme** ont accès à toutes les API dans une plateforme donnée (par exemple, .NET Framework, Xamarin iOS), mais sont utilisables uniquement par les applications et les bibliothèques qui ciblent cette plateforme.
* Les bibliothèques de classes **portables** ont accès à un sous-ensemble d’API et sont utilisables par les applications et les bibliothèques qui ciblent plusieurs plateformes.
* Les bibliothèques de classes **.NET Standard** sont une fusion du concept de bibliothèques spécifiques d’une plateforme et portables en un seul modèle qui offre le meilleur des deux.

## <a name="platform-specific-class-libraries"></a>Bibliothèques de classes propres à la plateforme

Les bibliothèques spécifiques d’une plateforme sont liées à une seule implémentation .NET (par exemple, .NET Framework sur Windows) et peuvent donc accepter des dépendances significatives sur un environnement d’exécution connu. Un tel environnement expose un ensemble connu d’API (API .NET et de système d’exploitation), et maintient et expose l’état attendu (par exemple, le Registre Windows).

Les développeurs qui créent des bibliothèques spécifiques à la plateforme peuvent exploiter pleinement la plateforme sous-jacente. Les bibliothèques ne s’exécutent que sur cette plateforme donnée, ce qui rend inutile les vérifications de plateforme ou d’autres formes de code conditionnel (code d’approvisionnement modulo unique pour plusieurs plateformes).

Les bibliothèques spécifiques d’une plateforme ont été le type de bibliothèque de classes principal du .NET Framework. Même si d’autres implémentations .NET sont apparues, les bibliothèques spécifiques d’une plateforme sont restées le type de bibliothèque prédominant.

## <a name="portable-class-libraries"></a>Bibliothèques de classes portables

Les bibliothèques portables sont prises en charge sur plusieurs implémentations .NET. Ils peuvent toujours prendre des dépendances sur un environnement d’exécution connu, mais l’environnement est un synthétique généré par l’intersection d’un ensemble d’implémentations .NET concrètes. Les API exposées et les hypothèses de plateforme sont un sous-ensemble de ce qui est disponible pour une bibliothèque spécifique à une plateforme.

Vous choisissez une configuration de plateforme quand vous créez une bibliothèque portable. La configuration de la plateforme est l’ensemble des plateformes que vous devez prendre en charge (par exemple, .NET Framework 4.5 +, Windows Phone 8.0 +). Plus vous avez de plateformes à prendre en charge, moins vous avez d’API et moins vous pouvez faire d’hypothèses de plateforme, selon le plus petit dénominateur commun. Cette caractéristique peut prêter à confusion dans un premier temps, étant donné que les gens pensent souvent que « plus est mieux », mais qu’il y a plus de plateformes prises en charge, moins il y a d’API disponibles.

De nombreux développeurs de bibliothèques ont abandonné la production de plusieurs bibliothèques spécifiques d’une plateforme à partir d’une seule source (à l’aide de directives de compilation conditionnelle) au profit des bibliothèques portables. Il existe [plusieurs approches](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) permettant d’accéder à une fonctionnalité spécifique d’une plateforme dans les bibliothèques portables, bait-and-switch étant la technique la plus répandue à ce stade.

## <a name="net-standard-class-libraries"></a>Bibliothèques de classes .NET Standard

Les bibliothèques .NET Standard remplacent les concepts de bibliothèques spécifiques d’une plateforme et portables. Elles sont spécifiques d’une plateforme en ce sens qu’elles exposent toutes les fonctionnalités de la plateforme sous-jacente (pas de plateforme synthétique ni d’intersection de plateformes). Elles sont portables en ce sens qu’elles fonctionnent sur toutes les plateformes de prise en charge.

.NET Standard expose un ensemble de _contrats_de bibliothèque. Les implémentations .NET doivent prendre en charge chaque contrat dans son intégralité ou pas du tout. Ainsi, chaque implémentation prend en charge un ensemble de contrats .NET Standard. Le corollaire est que chaque bibliothèque de classes .NET Standard est prise en charge sur les plateformes qui prennent en charge les dépendances de son contrat.

.NET Standard n’expose pas l’ensemble des fonctionnalités du .NET Framework (pas plus qu’un objectif), toutefois, elles exposent beaucoup plus d’API que les bibliothèques de classes portables. D’autres API seront ajoutées au fil du temps.

Les plateformes suivantes prennent en charge les bibliothèques .NET Standard :

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Plateforme Windows universelle (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Pour plus d'informations, consultez [.NET Standard](net-standard.md).

## <a name="mono-class-libraries"></a>Bibliothèques de classes Mono

Les bibliothèques de classes sont prises en charge sur mono, y compris les trois types de bibliothèques décrits précédemment. Mono a souvent été vu (correctement) comme une implémentation multiplateforme de .NET Framework. C’est en partie parce que les bibliothèques .NET Framework spécifiques d’une plateforme peuvent s’exécuter sur le runtime Mono sans modification ou recompilation. Cette caractéristique existait avant la création des bibliothèques de classes portables, elle était donc choisie en priorité pour permettre la portabilité binaire entre le .NET Framework et Mono (même si cela ne fonctionnait que dans un sens).
