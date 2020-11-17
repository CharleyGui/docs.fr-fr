---
title: Vue d’ensemble des bibliothèques Runtime
description: Découvrez ce qui est inclus dans la section bibliothèques Runtime de la table des matières.
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687893"
---
# <a name="runtime-libraries-overview"></a>Vue d’ensemble des bibliothèques Runtime

Le [Runtime .net](../core/introduction.md#sdk-and-runtimes), qui est installé sur un ordinateur pour une utilisation par les [applications dépendantes du Framework](../core/introduction.md#deployment-models), possède un ensemble standard de bibliothèques de classes, connu sous le nom de [bibliothèques Runtime](glossary.md#runtime), de [bibliothèques d’infrastructure](glossary.md#framework-libraries)ou de la bibliothèque de [classes de base (BCL)](glossary.md#bcl). En outre, il existe des extensions pour les bibliothèques Runtime, fournies dans les packages NuGet.

Ces bibliothèques fournissent des implémentations pour de nombreux types généraux et spécifiques à l’application, des algorithmes et des fonctionnalités d’utilitaire.

## <a name="runtime-libraries"></a>Bibliothèques Runtime

Ces bibliothèques fournissent les types fondamentaux et les fonctionnalités de l’utilitaire et constituent la base de toutes les autres bibliothèques de classes .NET. La <xref:System.String?displayProperty=nameWithType> classe, qui fournit des API pour l’utilisation de chaînes, en est un exemple. Les [bibliothèques de sérialisation](serialization/index.md)sont un autre exemple.

## <a name="extensions-to-the-runtime-libraries"></a>Extensions des bibliothèques Runtime

Certaines bibliothèques sont fournies dans les packages NuGet au lieu d’être incluses dans le [Framework partagé](glossary.md#shared-framework)du Runtime. Par exemple :

* [Logging](../core/extensions/logging.md)
* [Injection de dépendances](../core/extensions/dependency-injection.md)
* [Configuration](../core/extensions/configuration.md)

## <a name="see-also"></a>Voir aussi

* [Introduction à .NET](../core/introduction.md)
* [Installer le kit de développement logiciel (SDK) .NET ou Runtime](../core/install/index.yml)
* [Sélectionnez le kit de développement logiciel (SDK) .NET installé ou la version du runtime à utiliser](../core/versions/selection.md)
* [Publier des applications dépendantes du Framework](../core/deploying/index.md#publish-framework-dependent)
