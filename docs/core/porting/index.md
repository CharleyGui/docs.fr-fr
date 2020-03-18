---
title: Port de .NET Framework à .NET Core
description: Présentation du processus de portage et d’outils qui peuvent s’avérer utiles lors du portage d’un projet .NET Framework vers .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937323"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Aperçu du portage du cadre .NET à .NET Core

Vous pouvez avoir du code qui fonctionne actuellement sur le cadre .NET que vous êtes intéressé à porter à .NET Core. Cet article fournit :

* Un aperçu du processus de portage.
* Une liste d’outils que vous pouvez trouver utile lorsque vous transférez votre code à .NET Core.

## <a name="overview-of-the-porting-process"></a>Vue d’ensemble du processus de portage

Nous vous recommandons d’utiliser le processus suivant lors du portage de votre projet à .NET Core:

1. Retarget tous les projets que vous souhaitez portuairer pour cibler .NET Framework 4.7.2 ou plus.

   Cette étape garantit que vous pouvez utiliser des API alternatives pour des cibles spécifiques au .NET Framework si .NET Core ne prend en charge une API particulière.

2. Utilisez [l’analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour analyser vos assemblages et voir si elles sont portables à .NET Core.

   L’outil API Portability Analyzer analyse vos assemblages compilés et génère un rapport. Ce rapport montre un résumé de portabilité de haut niveau et une ventilation de chaque API que vous utilisez qui n’est pas disponible sur NET Core.

3. Installez [l’analyseur d’API .NET](../../standard/analyzers/api-analyzer.md) dans <xref:System.PlatformNotSupportedException> vos projets pour identifier les API qui jettent sur certaines plates-formes et d’autres problèmes de compatibilité potentiels.

   Cet outil est similaire à l’analyseur de portabilité, mais au lieu d’analyser si le code peut s’appuyer <xref:System.PlatformNotSupportedException> sur .NET Core, il analyse si vous utilisez une API d’une manière qui lancera un à l’heure de fonctionnement. Bien que ce n’est pas commun si vous vous déplacez de .NET Framework 4.7.2 ou plus, il est bon de vérifier. Pour plus d’informations sur les API qui jettent des exceptions sur .NET Core, voir [API qui jettent toujours des exceptions sur .NET Core](../compatibility/unsupported-apis.md).

4. Convertissez toutes `packages.config` vos dépendances au format [PackageReference](/nuget/consume-packages/package-references-in-project-files) avec l’outil [de conversion dans Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Cette étape consiste à convertir vos `packages.config` dépendances à partir du format hérité. `packages.config`ne fonctionne pas sur .NET Core, donc cette conversion est nécessaire si vous avez des dépendances de paquet.

5. Créez de nouveaux projets pour .NET Core et copiez sur les fichiers source, ou essayez de convertir votre fichier de projet existant avec un outil.

   .NET Core utilise un format de [fichier de projet](../tools/csproj.md) simplifié (et différent) que .NET Framework. Vous devrez convertir vos fichiers de projet en ce format pour continuer.

6. Port votre code de test.

   Parce que le portage vers .NET Core est une modification significative de votre base de code, il est fortement recommandé de porter vos projets de test afin que vous puissiez exécuter des tests que vous portez votre code plus. MSTest, xUnit, et NUnit tous les travaux sur .NET Core.

En outre, vous pouvez essayer de porter des solutions plus petites ou des projets individuels dans une opération au format de fichier de projet .NET Core avec [l’outil d’essai-convertir dotnet.](https://github.com/dotnet/try-convert) `dotnet try-convert`n’est pas garanti de travailler pour tous vos projets, et il peut causer des changements subtils dans le comportement dont vous dépendiez. Utilisez-le comme point _de départ_ qui automatise les choses de base qui peuvent être automatisées. Ce n’est pas une solution garantie pour migrer un projet.

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Analyser les dépendances](third-party-deps.md)
