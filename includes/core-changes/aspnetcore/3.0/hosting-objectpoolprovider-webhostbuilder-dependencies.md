---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901761"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hébergement: ObjectPoolProvider supprimé des dépendances WebHostBuilder

Dans le cadre de rendre ASP.NET Core plus `ObjectPoolProvider` de payer pour le jeu, le a été retiré de l’ensemble principal des dépendances. Des composants spécifiques `ObjectPoolProvider` sur qui s’appuient l’ajoutent maintenant eux-mêmes.

Pour discussion, voir [dotnet/aspnetcore 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`WebHostBuilder`fournit `ObjectPoolProvider` par défaut dans le conteneur DI.

#### <a name="new-behavior"></a>Nouveau comportement

`WebHostBuilder`ne fournit `ObjectPoolProvider` plus par défaut dans le conteneur DI.

#### <a name="reason-for-change"></a>Raison du changement

Ce changement a été apporté pour rendre ASP.NET Core plus de salaire pour le jeu.

#### <a name="recommended-action"></a>Action recommandée

Si votre `ObjectPoolProvider`composant nécessite, il doit être ajouté `IServiceCollection`à vos dépendances via le .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
