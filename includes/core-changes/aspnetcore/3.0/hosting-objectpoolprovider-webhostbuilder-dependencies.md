---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901761"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder

Dans le cadre de la création de ASP.NET Core plus de paiement `ObjectPoolProvider` pour la lecture, a été supprimé de l’ensemble principal de dépendances. Les composants spécifiques qui dépendent `ObjectPoolProvider` de maintenant l’ajoutent eux-mêmes.

Pour plus d’informations, consultez [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`WebHostBuilder`fournit `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.

#### <a name="new-behavior"></a>Nouveau comportement

`WebHostBuilder`n’est plus `ObjectPoolProvider` fourni par défaut dans le conteneur d’injection de paramètres.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée pour rendre ASP.NET Core plus payant.

#### <a name="recommended-action"></a>Action recommandée

Si votre composant requiert `ObjectPoolProvider`, il doit être ajouté à vos dépendances via le `IServiceCollection`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
