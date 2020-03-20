---
title: .NET Framework et Out-of-Band Releases
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181568"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework et sorties hors bande

.NET Framework a évolué pour accueillir différentes plates-formes, telles que les applications UWP et les applications de bureau et web traditionnelles, et pour maximiser la réutilisation du code. En plus des versions régulières de .NET Framework, de nouvelles fonctionnalités sont publiées hors bande (OOB) pour améliorer le développement multiplateforme ou pour introduire de nouvelles fonctionnalités.

## <a name="advantages-of-oob-releases"></a>Avantages des versions OOB

L’expédition de nouveaux composants ou mises à jour de composants hors bande permet à Microsoft de fournir des mises à jour plus fréquentes de .NET Framework. De plus, nous pouvons nous réunir et répondre aux commentaires des clients plus rapidement.

Lorsque vous utilisez une fonctionnalité OOB dans votre application, vos utilisateurs n’ont pas à installer la dernière version de .NET Framework pour exécuter votre application, car les assemblages OOB se déploient avec votre package d’application.

## <a name="how-oob-packages-are-distributed"></a>Mode de distribution des packages OOB

Les versions OOB pour les composants de l’heure d’exécution de langage commun de base (CLR) sont livrées par [NuGet](https://www.nuget.org/), qui est le gestionnaire de paquet pour .NET. NuGet vous permet de parcourir et d’ajouter des bibliothèques à vos projets cadre .NET facilement à partir de Visual Studio. NuGet Package Manager est inclus dans toutes les éditions de Visual Studio à partir de Visual Studio 2012. Recherchez **NuGet Package Manager** sur le menu **Tools** dans Visual Studio. Si elle n’est pas installée, suivez les instructions sur [l’installation de NuGet](/nuget/install-nuget-client-tools). Pour plus d’informations sur NuGet, voir les [docs NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Utilisez un forfait NuGet OOB

Si NuGet Package Manager est installé, vous pouvez parcourir et ajouter des références aux paquets NuGet en utilisant Solution Explorer dans Visual Studio :

1. Ouvrez le menu contextuel de votre projet dans Visual Studio, puis choisissez **Gérer les packages NuGet**. (Cette option est également disponible dans le menu **Projet**.)

2. Dans le volet gauche, cliquez sur **En ligne**.

3. Si vous souhaitez utiliser des packages de version préliminaire, dans la zone de liste déroulante du volet central, sélectionnez l’option **Inclure la version préliminaire** au lieu de **Stable uniquement**.

4. Dans le volet droit, utilisez la zone **Rechercher** pour localiser le package que vous souhaitez utiliser. Certains packages Microsoft sont identifiés par le logo Microsoft .NET Framework, et tous identifient Microsoft en tant qu'éditeur.

![Le gestionnaire de forfait NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Comme mentionné précédemment, lorsque vous déployez une application qui utilise un package OOB, les assemblys OOB sont fournis avec votre package d'application.

## <a name="types-of-oob-releases"></a>Types de versions OOB

En général, un package OOB a une ou plusieurs versions préliminaires et une version stable. La licence qui accompagne une version préliminaire n'autorise généralement pas la redistribution, mais vous permet de tester un package et de fournir des commentaires. Les commentaires sont incorporés dans toutes les mises à jour apportées au package. Une version finale est distribuée comme package stable avec NuGet et inclut une licence qui vous permet de redistribuer le package NuGet avec votre application. Les packages stables sont pris en charge par Microsoft. Microsoft fournit la prise en charge IntelliSense, ainsi que d'autres types de documentation tels que les publications de blog et les réponses de forum pour tous les packages. De plus, le code source peut ne pas être disponible avec tous les packages. Pour être tenu informé sur les packages nouveaux et mis à jour, inscrivez-vous sur le [blog du .NET Framework](https://devblogs.microsoft.com/dotnet/).

Pour trouver des forfaits préreléase et stables, choisissez **Inclure Prerelease** dans NuGet Package Manager.

## <a name="see-also"></a>Voir aussi

- [Commencer](index.md)
