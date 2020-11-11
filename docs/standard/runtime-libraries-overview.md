---
title: Vue d’ensemble des bibliothèques Runtime
description: Découvrez ce qui est inclus dans la section bibliothèques Runtime de la table des matières.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507610"
---
# <a name="runtime-libraries-overview"></a>Vue d’ensemble des bibliothèques Runtime

Le [Runtime .net](../core/introduction.md#sdk-and-runtimes), qui est installé sur un ordinateur pour une utilisation par les [applications dépendantes du Framework](../core/introduction.md#deployment-models), possède un ensemble standard de bibliothèques de classes :

* Ensemble principal, inclus dans le runtime et connu sous le nom de [bibliothèques de classes de base (BCL)](glossary.md#bcl).
* Ensemble complet, inclus dans le runtime et connu sous le nom de [bibliothèques d’exécution](glossary.md#runtime) ou de bibliothèques d' [infrastructure](glossary.md#framework).
* Extensions des bibliothèques Runtime, fournies dans les packages NuGet.

Ces bibliothèques fournissent des implémentations pour de nombreux types généraux et spécifiques à l’application, des algorithmes et des fonctionnalités d’utilitaire.

## <a name="base-class-libraries"></a>Bibliothèques de classes de base

La bibliothèque de classes de base fournit les types de base et les fonctionnalités de l’utilitaire et constitue la base de toutes les autres bibliothèques de classes .NET. La <xref:System.String?displayProperty=nameWithType> classe, qui fournit des API pour l’utilisation de chaînes, en est un exemple.

## <a name="runtime-libraries"></a>Bibliothèques Runtime

Également appelés bibliothèques d’infrastructure, les bibliothèques Runtime s’appuient sur la BCL pour fournir des API utilitaire pour les tâches courantes. Les [bibliothèques de sérialisation](serialization/index.md)en sont un exemple.

## <a name="extensions-to-the-runtime-libraries"></a>Extensions des bibliothèques Runtime

Certaines des bibliothèques Runtime sont fournies dans les packages NuGet au lieu d’être intégrées au runtime qui est installé pour les applications dépendantes du Framework. L' [API de journalisation .net](../core/extensions/logging.md)en est un exemple.

## <a name="see-also"></a>Voir aussi

* [Introduction à .NET](../core/introduction.md)
* [Installer le kit de développement logiciel (SDK) .NET ou Runtime](../core/install/index.yml)
* [Sélectionnez le kit de développement logiciel (SDK) .NET installé ou la version du runtime à utiliser](../core/versions/selection.md)
* [Publier des applications dépendantes du Framework](../core/deploying/index.md#publish-framework-dependent)
