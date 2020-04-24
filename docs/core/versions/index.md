---
title: Gestion des versions NET Core du runtime et du SDK
description: Cet article vous explique comment les .NET Core versions du SDK et du runtime sont gérées (similaire à la gestion sémantique des versions).
ms.date: 07/26/2018
ms.openlocfilehash: f166a6dfc1c9127eb629365efd628855489a60cb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644393"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Vue d’ensemble de la gestion des versions .NET Core

.NET Core fait référence au runtime .NET Core et au SDK .NET Core, qui contiennent les outils dont vous avez besoin pour développer des applications. Les kits SDK .NET Core sont conçus pour fonctionner avec n’importe quelle version précédente du runtime .NET Core. Cet article traite de la stratégie de gestion des versions du runtime et des SDK. Vous trouverez une explication des numéros de version de .NET Standard dans l’article de présentation de [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Le runtime .NET Core et le SDK .NET Core ajoutent de nouvelles fonctionnalités à une fréquence différente : en général, le SDK .NET Core fournit des mises à jour d’outils plus rapidement que le runtime .NET Core ne change le runtime que vous utilisez en production.

## <a name="versioning-details"></a>Informations détaillées sur la gestion des versions

« .NET Core 2.1 » fait référence au numéro de version du runtime .NET Core. Le runtime .NET Core adopte une approche de type majeur/mineur/correctif de la gestion de versions qui adhère à la [gestion sémantique de versions](#semantic-versioning).

Le SDK .NET Core n’adhère pas à la gestion sémantique de versions. Le SDK .NET Core est publié plus rapidement et ses versions doivent communiquer à la fois le runtime aligné et les propres versions mineure et corrective du SDK. Les deux premières positions de la version du SDK .NET Core sont verrouillées d’après le runtime .NET Core avec lequel cette version a été publiée. Chaque version du SDK peut créer des applications pour ce runtime ou toute version antérieure.

La troisième position du numéro de la version du SDK indique le numéro mineur et de correctif. La version mineure est multipliée par 100. La version mineure 1 avec version de correctif 2 serait représentée par le chiffre 102. Les deux derniers chiffres représentent le numéro du correctif. Par exemple, la publication de .NET Core 2.2 peut créer des versions comme indiqué dans le tableau suivant :

| Modifier                | Runtime .NET Core | .NET Core SDK (\*) |
|-----------------------|-------------------|-------------------|
| Version initiale       | 2.2.0             | 2.2.100           |
| Correctif de SDK             | 2.2.0             | 2.2.101           |
| Correctif de SDK et du runtime | 2.2.1             | 2.2.102           |
| Modifications de fonctionnalités du SDK    | 2.2.1             | 2.2.200           |

(\*) Ce graphique utilise le 2.2 .NET Core Runtime comme exemple parce qu’un artefact historique signifiait que le premier SDK pour .NET Core 2.1 est de 2.1.300. Pour plus d’informations, consultez la [Sélection de versions .NET Core](selection.md).

REMARQUES :

- Si le SDK a 10 mises à jour de fonctionnalités avant une mise à jour de fonctionnalité de runtime, les numéros de version passent à la série 1000 avec des numéros tels que 2.2.1000 comme version de fonctionnalité suivant 2.2.900. Cette situation n’est pas censée se produire.
- Il ne se produira pas 99 publications de correctifs sans une publication de fonctionnalité. Si une publication est proche de ce numéro, cela force une publication de fonctionnalité.

Vous trouverez plus de détails dans la proposition initiale dans le dépôt [dotnet/designs](https://github.com/dotnet/designs/pull/29).

## <a name="semantic-versioning"></a>Gestion sémantique de version

Le *runtime* .NET Core adhère globalement à la [gestion sémantique des versions (SemVer)](https://semver.org/), adoptant ainsi l’utilisation de la gestion de versions `MAJOR.MINOR.PATCH`, qui utilise différentes parties du numéro de version pour décrire le degré et le type de modification.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Les pièces facultatives `PRERELEASE` et `BUILDNUMBER` ne feront jamais partie des versions prises en charge, elles existent seulement sur les builds générés pendant la nuit, builds locaux générés à partir des cibles de la source et préversions non prises en charge.

### <a name="understand-runtime-version-number-changes"></a>Description des changements de numéro de version du runtime

`MAJOR` est incrémenté quand :

- Des modifications importantes sont apportées au produit, ou en cas de nouvelle direction du produit.
- Des changements cassants ont été apportés. La barre est haute pour accepter les changements cassants.
- Une version ancienne n’est plus prise en charge.
- Une version `MAJOR` plus récente d’une dépendance existante est adoptée.

`MINOR` est incrémenté quand :

- Une surface d’exposition d’API publique est ajoutée.
- Un nouveau comportement est ajouté.
- Une version `MINOR` plus récente d’une dépendance existante est adoptée.
- Une nouvelle dépendance est introduite.

`PATCH` est incrémenté quand :

- Des correctifs de bogues sont effectués.
- La prise en charge d’une plateforme plus récente est ajoutée.
- Une version `PATCH` plus récente d’une dépendance existante est adoptée.
- Toute autre modification ne relevant pas d’un des cas précédents.

Quand il existe plusieurs modifications, l’élément le plus élevé affecté par des modifications individuelles est incrémenté et les suivants sont remis à zéro. Par exemple, quand `MAJOR` est incrémenté, `MINOR` et `PATCH` sont remis à zéro. Quand `MINOR` est incrémenté, `PATCH` est remis à zéro, tandis que `MAJOR` est laissé tel quel.

## <a name="version-numbers-in-file-names"></a>Numéros de version dans les noms de fichiers

Les fichiers téléchargés pour .NET Core mentionnent la version, par exemple `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Préversions

Pour les préversions, un `-preview[number]-([build]|"final")` est ajouté à la version. Par exemple : `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Versions de maintenance

Une fois qu’une version est publiée, les branches de la version arrêtent généralement de produire des builds quotidiens pour commencer à produire des builds de maintenance. Pour les versions de maintenance, un `-servicing-[number]` est ajouté à la version. Par exemple : `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relation avec les versions .NET Standard

.NET standard se compose d’un assembly de référence .NET. Il existe plusieurs implémentations propres à chaque plateforme. L’assembly de référence contient la définition des API .NET qui font partie d’une version donnée de .NET Standard. Chaque implémentation remplit le contrat .NET Standard sur la plateforme spécifique. Pour en savoir plus, consultez l’article sur [.NET Standard](../../standard/net-standard.md) dans le Guide de .NET.

L’assembly de référence .NET Standard utilise un schéma de gestion de version `MAJOR.MINOR`. Le niveau `PATCH` n’est pas utile pour .NET Standard, car il expose uniquement une spécification d’API (aucune implémentation), et par définition toute modification apportée à l’API représenterait une modification de l’ensemble de fonctionnalités et par conséquent une nouvelle version `MINOR`.

Les implémentations sur chaque plateforme peuvent être mises à jour, généralement dans le cadre de la version de plateforme et par conséquent non évidentes pour les programmeurs utilisant .NET Standard sur cette plateforme.

Chaque version de .NET Core implémente une version de .NET Standard. L’implémentation d’une version de .NET Standard implique la prise en charge des versions précédentes de .NET Standard. Les versions de .NET standard et de .NET Core sont indépendantes. Le faut que .NET Core 2.0 implémente .NET Standard 2.0 est une coïncidence. .NET Core 2.1 implémente également .NET Standard 2.0. .NET Core prendra en charge les versions ultérieures de .NET Standard dès qu’elles seront disponibles.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | Jusqu’à 1.6     |
| 2.0       | Jusqu’à 2.0     |
| 2.1       | Jusqu’à 2.0     |
| 2.2       | Jusqu’à 2.0     |
| 3.0       | jusqu’à 2,1     |

## <a name="see-also"></a>Voir aussi

- [Versions cibles de .NET Framework](../../standard/frameworks.md)
- [Empaquetage de la distribution de .NET Core](../distribution-packaging.md)
- [Fiche d’information sur le cycle de vie de support .NET Core](https://dotnet.microsoft.com/platform/support/policy)
- [Liaison de version .NET Core 2+](https://github.com/dotnet/designs/issues/3)
- [Images Docker pour .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
