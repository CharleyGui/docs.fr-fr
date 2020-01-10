---
title: Port de .NET Framework à .NET Core
description: Présentation du processus de portage et d’outils qui peuvent s’avérer utiles lors du portage d’un projet .NET Framework vers .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: b5b010acbccf134afe800aa5bb98a0ae6e9ffa25
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777354"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Vue d’ensemble du Portage à partir de .NET Framework vers .NET Core

Vous pouvez avoir du code qui s’exécute actuellement sur le .NET Framework que vous souhaitez porter vers .NET Core. Cet article fournit :

* Vue d’ensemble du processus de Portage.
* Liste des outils que vous pouvez trouver utiles lorsque vous portez votre code vers .NET Core.

## <a name="overview-of-the-porting-process"></a>Vue d’ensemble du processus de portage

Nous vous recommandons d’utiliser le processus suivant lors du Portage de votre projet vers .NET Core :

1. Reciblez tous les projets que vous souhaitez porter vers la cible .NET Framework 4.7.2 ou une version ultérieure.

   Cette étape garantit que vous pouvez utiliser des API alternatives pour des cibles spécifiques au .NET Framework si .NET Core ne prend en charge une API particulière.

2. Utilisez l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) pour analyser vos assemblys et voir s’ils sont portables vers .net core.

   L’outil API Portability Analyzer analyse vos assemblys compilés et génère un rapport. Ce rapport affiche un résumé de la portabilité de haut niveau et une répartition de chaque API que vous utilisez et qui n’est pas disponible sur le réseau principal.

3. Installez l' [analyseur d’API .net](../../standard/analyzers/api-analyzer.md) dans vos projets pour identifier les API déclenchant des <xref:System.PlatformNotSupportedException> sur certaines plateformes, ainsi que d’autres problèmes de compatibilité potentiels.

   Cet outil est similaire à l’analyseur de portabilité, mais au lieu d’analyser si des éléments peuvent être générés sur .NET Core, il analyse si vous utilisez une API d’une manière qui lèvera la <xref:System.PlatformNotSupportedException> au moment de l’exécution. Bien que cela ne soit pas courant si vous passez de .NET Framework 4.7.2 ou une version ultérieure, il est préférable de vérifier.

4. Convertissez toutes vos dépendances de `packages.config` au format [PackageReference](/nuget/consume-packages/package-references-in-project-files) à l’aide de l' [outil de conversion de Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Cette étape implique la conversion de vos dépendances à partir du format de `packages.config` hérité. `packages.config` ne fonctionne pas sur .NET Core, cette conversion est nécessaire si vous avez des dépendances de package.

5. Créez des projets pour .NET Core et copiez les fichiers sources, ou essayez de convertir votre fichier projet existant à l’aide d’un outil.

   .NET Core utilise un [format de fichier projet](../tools/csproj.md) simplifié (et différent) que .NET Framework. Vous devez convertir vos fichiers projet dans ce format pour continuer.

6. Portez votre code de test.

   Étant donné que le portage vers .NET Core est une modification significative de votre code base, il est fortement recommandé de porter vos projets de test afin que vous puissiez exécuter des tests au fur et à mesure que vous portez votre code. MSTest, xUnit et NUnit fonctionnent tous sur .NET Core.

En outre, vous pouvez tenter de porter des solutions plus petites ou des projets individuels en une seule opération au format de fichier projet .NET Core à l’aide de l’outil [dotnet try-Convert](https://github.com/dotnet/try-convert) . Il n’est pas garanti que les `dotnet try-convert` fonctionnent pour tous vos projets, et cela peut entraîner des modifications subtiles du comportement dont vous dépendez. Utilisez-le comme _point de départ_ pour automatiser les éléments de base qui peuvent être automatisés. Il ne s’agit pas d’une solution garantie pour la migration d’un projet.

## <a name="next-steps"></a>Étapes suivantes :

>[!div class="nextstepaction"]
>[Technologies non disponibles sur .NET Core](net-framework-tech-unavailable.md)
