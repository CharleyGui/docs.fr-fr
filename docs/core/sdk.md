---
title: Vue d’ensemble du SDK .NET
description: Découvrez le kit de développement logiciel (SDK) .NET, qui est un ensemble de bibliothèques et d’outils permettant de créer des projets .NET.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 5236d4abec5dcbf950059dd906958158cfb592fe
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216139"
---
# <a name="net-sdk-overview"></a>Vue d’ensemble du SDK .NET

Le kit de développement logiciel (SDK) .NET est un ensemble de bibliothèques et d’outils qui permettent aux développeurs de créer des applications et des bibliothèques .NET. Il contient les composants suivants, qui sont utilisés pour générer et exécuter des applications :

- Interface CLI .NET.
- Bibliothèques et Runtime .NET.
- `dotnet` [Pilote](tools/index.md#driver).

## <a name="acquiring-the-net-sdk"></a>Acquisition du kit de développement logiciel (SDK) .NET

Comme pour n’importe quel ensemble d’outils, la première étape consiste à se procurer les outils sur l’ordinateur. Selon votre scénario, vous pouvez installer le SDK à l’aide de l’une des méthodes suivantes :

- En utilisant des programmes d’installation natifs
- En utilisant le script shell d’installation

Les programmes d’installation natifs s’adressent principalement aux ordinateurs des développeurs. Le SDK est distribué selon le mécanisme d’installation natif de chaque plateforme prise en charge, comme les packages DEB sur Ubuntu ou les bundles MSI sur Windows. Ces programmes d’installation installent et configurent l’environnement comme il se doit pour permettre à l’utilisateur de tirer parti du SDK immédiatement après l’installation. Cependant, ils nécessitent aussi de disposer de privilèges d’administration sur l’ordinateur. Vous trouverez le SDK à installer dans la page [Téléchargements .NET](https://dotnet.microsoft.com/download).

Les scripts d’installation, quant à eux, ne nécessitent pas de privilèges d’administration. En revanche, ils n’installent pas les prérequis sur l’ordinateur. Vous devez donc tous les installer manuellement. Les scripts visent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration (notez les mises en garde concernant les prérequis répertoriés ci-dessus). Vous trouverez des informations complémentaires dans l’article de [ référence sur les scripts d’installation](tools/dotnet-install-script.md). Si vous souhaitez savoir comment configurer le kit de développement logiciel (SDK) sur votre serveur de builds CI, consultez l’article [utilisation du kit de développement logiciel (SDK) et des outils .net dans l’intégration continue (ci)](tools/using-ci-with-cli.md) .

Par défaut, le kit de développement logiciel (SDK) s’installe en mode côte à côte (SxS), ce qui signifie que plusieurs versions peuvent coexister à un moment donné sur un même ordinateur. La façon dont la version est choisie lorsque vous exécutez les commandes CLI est expliquée plus en détail dans l’article [Sélectionner la version .net à utiliser](versions/selection.md) .

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’interface CLI .NET](tools/index.md)
- [Vue d’ensemble du contrôle de version .NET](versions/index.md)
- [Comment supprimer le Runtime .NET et le kit de développement logiciel (SDK)](install/remove-runtime-sdk-versions.md)
- [Sélectionner la version .NET à utiliser](versions/selection.md)
