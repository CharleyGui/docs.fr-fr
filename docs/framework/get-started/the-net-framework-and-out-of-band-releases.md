---
title: Versions .NET Framework et hors plage
description: En savoir plus sur .NET et les versions hors plage. De nouvelles fonctionnalités sont publiées hors bande (OOB) pour améliorer le développement multiplateforme ou pour introduire de nouvelles fonctionnalités.
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618764"
---
# <a name="net-framework-and-out-of-band-releases"></a>Versions finales hors plage de .NET Framework

.NET Framework a évolué pour prendre en charge différentes plateformes, telles que les applications UWP et les applications bureautiques et Web traditionnelles, et pour optimiser la réutilisation du code. En plus des versions de .NET Framework régulières, de nouvelles fonctionnalités sont publiées hors bande (OOB) pour améliorer le développement multiplateforme ou pour introduire de nouvelles fonctionnalités.

## <a name="advantages-of-oob-releases"></a>Avantages des versions OOB

La livraison de nouveaux composants ou mises à jour de composants hors bande permet à Microsoft de fournir des mises à jour plus fréquentes à .NET Framework. De plus, nous pouvons nous réunir et répondre aux commentaires des clients plus rapidement.

Lorsque vous utilisez une fonctionnalité OOB dans votre application, vos utilisateurs n’ont pas besoin d’installer la dernière version de .NET Framework pour exécuter votre application, car les assemblys OOB se déploient avec votre package d’application.

## <a name="how-oob-packages-are-distributed"></a>Mode de distribution des packages OOB

Les versions OOB des composants du CLR (Core common language runtime) sont fournies via [NuGet](https://www.nuget.org/), qui est le gestionnaire de package pour .net. NuGet vous permet de parcourir et d’ajouter facilement des bibliothèques à vos projets .NET Framework à partir de Visual Studio. Le gestionnaire de package NuGet est inclus dans toutes les éditions de Visual Studio à partir de Visual Studio 2012. Recherchez **Gestionnaire de package NuGet** dans le menu **Outils** de Visual Studio. S’il n’est pas installé, suivez les instructions de la procédure d' [installation de NuGet](/nuget/install-nuget-client-tools). Pour plus d’informations sur NuGet, consultez la [documentation NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Utiliser un package OOB NuGet

Si le gestionnaire de package NuGet est installé, vous pouvez parcourir et ajouter des références aux packages NuGet à l’aide de Explorateur de solutions dans Visual Studio :

1. Ouvrez le menu contextuel de votre projet dans Visual Studio, puis choisissez **Gérer les packages NuGet**. (Cette option est également disponible dans le menu **Projet**.)

2. Dans le volet gauche, cliquez sur **En ligne**.

3. Si vous souhaitez utiliser des packages de version préliminaire, dans la zone de liste déroulante du volet central, sélectionnez l’option **Inclure la version préliminaire** au lieu de **Stable uniquement**.

4. Dans le volet droit, utilisez la zone **Rechercher** pour localiser le package que vous souhaitez utiliser. Certains packages Microsoft sont identifiés par le logo Microsoft .NET Framework, et tous identifient Microsoft en tant qu'éditeur.

![Gestionnaire de package NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Comme mentionné précédemment, lorsque vous déployez une application qui utilise un package OOB, les assemblys OOB sont fournis avec votre package d'application.

## <a name="types-of-oob-releases"></a>Types de versions OOB

En général, un package OOB a une ou plusieurs versions préliminaires et une version stable. La licence qui accompagne une version préliminaire n'autorise généralement pas la redistribution, mais vous permet de tester un package et de fournir des commentaires. Les commentaires sont incorporés dans toutes les mises à jour apportées au package. Une version finale est distribuée comme package stable avec NuGet et inclut une licence qui vous permet de redistribuer le package NuGet avec votre application. Les packages stables sont pris en charge par Microsoft. Microsoft fournit la prise en charge IntelliSense, ainsi que d'autres types de documentation tels que les publications de blog et les réponses de forum pour tous les packages. De plus, le code source peut ne pas être disponible avec tous les packages. Pour être tenu informé sur les packages nouveaux et mis à jour, inscrivez-vous sur le [blog du .NET Framework](https://devblogs.microsoft.com/dotnet/).

Pour rechercher à la fois les packages de version préliminaire et les packages stables, choisissez **inclure la version préliminaire** dans le gestionnaire de package NuGet.

## <a name="see-also"></a>Voir aussi

- [Bien démarrer](index.md)
