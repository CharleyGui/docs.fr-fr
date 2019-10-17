---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393993"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder

Dans le cadre de la création de ASP.NET Core plus de paiement pour la lecture, la `ObjectPoolProvider` a été supprimée de l’ensemble principal de dépendances. Les composants spécifiques qui reposent sur `ObjectPoolProvider` l’ajoutent eux-mêmes.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

`WebHostBuilder` fournit `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.

#### <a name="new-behavior"></a>Nouveau comportement

`WebHostBuilder` ne fournit plus `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée pour rendre ASP.NET Core plus payant.

#### <a name="recommended-action"></a>Action recommandée

Si votre composant requiert `ObjectPoolProvider`, il doit être ajouté à vos dépendances via le `IServiceCollection`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
