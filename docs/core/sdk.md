---
title: Vue d’ensemble du SDK .NET Core
description: Découvrez le Kit SDK .NET Core, un ensemble de bibliothèques et d’outils permettant de créer des projets .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 7eb06e4fd94ed2a73af2741e98e21e02728c27e4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595739"
---
# <a name="net-core-sdk-overview"></a>Vue d’ensemble du SDK .NET Core

Le Kit SDK .NET Core est un ensemble de bibliothèques et d’outils qui permettent aux développeurs de créer des applications et des bibliothèques .NET Core. Il contient les composants suivants, qui sont utilisés pour générer et exécuter des applications :

- CLI .NET Core.
- Les bibliothèques .NET Core et Runtime
- `dotnet` [Pilote](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Obtention du SDK .NET Core

Comme pour n’importe quel ensemble d’outils, la première étape consiste à se procurer les outils sur l’ordinateur. Selon votre scénario, vous pouvez installer le SDK à l’aide de l’une des méthodes suivantes :

- En utilisant des programmes d’installation natifs
- En utilisant le script shell d’installation

Les programmes d’installation natifs s’adressent principalement aux ordinateurs des développeurs. Le SDK est distribué selon le mécanisme d’installation natif de chaque plateforme prise en charge, comme les packages DEB sur Ubuntu ou les bundles MSI sur Windows. Ces programmes d’installation installent et configurent l’environnement comme il se doit pour permettre à l’utilisateur de tirer parti du SDK immédiatement après l’installation. Cependant, ils nécessitent aussi de disposer de privilèges d’administration sur l’ordinateur. Vous trouverez le SDK à installer dans la page [Téléchargements .NET](https://dotnet.microsoft.com/download).

Les scripts d’installation, quant à eux, ne nécessitent pas de privilèges d’administration. En revanche, ils n’installent pas les prérequis sur l’ordinateur. Vous devez donc tous les installer manuellement. Les scripts visent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration (notez les mises en garde concernant les prérequis répertoriés ci-dessus). Vous trouverez des informations complémentaires dans l’article de [ référence sur les scripts d’installation](tools/dotnet-install-script.md). Pour savoir comment configurer le SDK sur votre serveur de builds CI, consultez l’article [Utilisation du SDK et des outils .NET Core avec l’intégration continue](tools/using-ci-with-cli.md).

Par défaut, le kit de développement logiciel (SDK) s’installe en mode côte à côte (SxS), ce qui signifie que plusieurs versions peuvent coexister à un moment donné sur un même ordinateur. Pour plus d’informations sur la façon dont la version est choisie lorsque vous exécutez des commandes CLI, consultez l’article [Sélectionner la version .NET Core à utiliser](versions/selection.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de CLI .NET Core](tools/index.md)
- [Vue d’ensemble de la gestion des versions .NET Core](versions/index.md)
- [Guide pratique pour supprimer un SDK et un Runtime .NET Core](install/remove-runtime-sdk-versions.md)
- [Sélectionner la version .NET Core à utiliser](versions/selection.md)
