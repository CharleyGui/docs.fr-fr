---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032524"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder

Dans le cadre de la création de ASP.NET Core plus de paiement pour la lecture, `ObjectPoolProvider` a été supprimé de l’ensemble principal de dépendances. Les composants spécifiques qui dépendent de `ObjectPoolProvider` maintenant l’ajoutent eux-mêmes.

Pour plus d’informations, consultez [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`WebHostBuilder` fournit `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.

#### <a name="new-behavior"></a>Nouveau comportement

`WebHostBuilder` n’est plus fourni `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée pour rendre ASP.NET Core plus payant.

#### <a name="recommended-action"></a>Action recommandée

Si votre composant requiert `ObjectPoolProvider` , il doit être ajouté à vos dépendances via le `IServiceCollection` .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
