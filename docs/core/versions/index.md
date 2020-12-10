---
title: Gestion des versions du Runtime .NET et du kit de développement logiciel (SDK)
description: Cet article explique comment les versions du kit de développement logiciel (SDK) .NET et du runtime sont gérées (de façon similaire à la gestion sémantique des versions).
ms.date: 12/07/2020
ms.openlocfilehash: 2fe0b162b52f1e4500ec87f7d5d92054cd569552
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009304"
---
# <a name="overview-of-how-net-is-versioned"></a>Vue d’ensemble de la gestion des versions de .NET

Le [Runtime .net et le kit de développement logiciel (SDK) .net](../introduction.md#sdk-and-runtimes) ajoutent de nouvelles fonctionnalités à différentes fréquences. En général, le kit de développement logiciel (SDK) est mis à jour plus fréquemment que le Runtime. Cet article explique le runtime et les numéros de version du kit de développement logiciel (SDK).

## <a name="versioning-details"></a>Informations détaillées sur la gestion des versions

Le Runtime .NET présente une approche majeure/mineure/correctif pour le contrôle de version qui suit le contrôle de [version sémantique](#semantic-versioning).

Le kit de développement logiciel (SDK) .NET ne suit pas le contrôle de version sémantique. Le kit de développement logiciel (SDK) .NET est plus rapide et ses numéros de version doivent communiquer à la fois le runtime aligné et les versions mineures et correctives du SDK.

Les deux premières positions du numéro de version du kit de développement logiciel (SDK) .NET sont verrouillées dans le Runtime .NET qu’il a fourni avec. Chaque version du SDK peut créer des applications pour ce runtime ou toute version antérieure.

La troisième position du numéro de la version du SDK indique le numéro mineur et de correctif. La version mineure est multipliée par 100. La version mineure 1 avec version de correctif 2 serait représentée par le chiffre 102. Les deux derniers chiffres représentent le numéro du correctif. Par exemple, voici une séquence possible des numéros de version du runtime et du kit de développement logiciel (SDK) :

| Modifier                | Runtime .NET      | SDK .NET ( \* )     |
|-----------------------|-------------------|-------------------|
| Version initiale       | 2.2.0             | 2.2.100           |
| Correctif de SDK             | 2.2.0             | 2.2.101           |
| Correctif de SDK et du runtime | 2.2.1             | 2.2.102           |
| Modifications de fonctionnalités du SDK    | 2.2.1             | 2.2.200           |

REMARQUES :

- Si le SDK a 10 mises à jour de fonctionnalités avant une mise à jour de fonctionnalité de runtime, les numéros de version passent à la série 1000 avec des numéros tels que 2.2.1000 comme version de fonctionnalité suivant 2.2.900. Cette situation n’est pas censée se produire.
- Il ne se produira pas 99 publications de correctifs sans une publication de fonctionnalité. Si une publication est proche de ce numéro, cela force une publication de fonctionnalité.

Vous trouverez plus de détails dans la proposition initiale dans le dépôt [dotnet/designs](https://github.com/dotnet/designs/pull/29).

## <a name="semantic-versioning"></a>Gestion sémantique de version

Le *Runtime* .net adhère approximativement à la [gestion sémantique des versions (SemVer)](https://semver.org/), en adoptant l’utilisation du contrôle de `MAJOR.MINOR.PATCH` version, en utilisant les différentes parties du numéro de version pour décrire le degré et le type de modification.

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

Les fichiers téléchargés pour .NET portent la version, par exemple, `dotnet-sdk-2.1.300-win10-x64.exe` .

### <a name="preview-versions"></a>Préversions

Les versions préliminaires ont un `-preview[number]-([build]|"final")` ajouté au numéro de version. Par exemple : `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Versions de maintenance

Une fois qu’une version est publiée, les branches de la version arrêtent généralement de produire des builds quotidiens pour commencer à produire des builds de maintenance. Pour les versions de maintenance, un `-servicing-[number]` est ajouté à la version. Par exemple : `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relation avec les versions .NET Standard

.NET standard se compose d’un assembly de référence .NET. Il existe plusieurs implémentations propres à chaque plateforme. L’assembly de référence contient la définition des API .NET qui font partie d’une version donnée de .NET Standard. Chaque implémentation remplit le contrat .NET Standard sur la plateforme spécifique.

L’assembly de référence .NET Standard utilise un schéma de gestion de version `MAJOR.MINOR`. Le niveau `PATCH` n’est pas utile pour .NET Standard, car il expose uniquement une spécification d’API (aucune implémentation), et par définition toute modification apportée à l’API représenterait une modification de l’ensemble de fonctionnalités et par conséquent une nouvelle version `MINOR`.

Les implémentations sur chaque plateforme peuvent être mises à jour, généralement dans le cadre de la version de plateforme et par conséquent non évidentes pour les programmeurs utilisant .NET Standard sur cette plateforme.

Pour plus d'informations, consultez [.NET Standard](../../standard/net-standard.md).

## <a name="see-also"></a>Voir aussi

- [Frameworks cibles](../../standard/frameworks.md)
- [Package de distribution .NET](../distribution-packaging.md)
- [Feuille de faits du cycle de vie du support .NET](https://dotnet.microsoft.com/platform/support/policy)
- [Images d’ancrage pour .NET](https://hub.docker.com/_/microsoft-dotnet/)
