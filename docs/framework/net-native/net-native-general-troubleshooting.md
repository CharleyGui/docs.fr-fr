---
title: Résolution des problèmes généraux liés à .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5f61b0e250c4f51a966bc60959f7559d8e2fe2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049398"
---
# <a name="net-native-general-troubleshooting"></a>Résolution des problèmes généraux liés à .NET Native

Cette rubrique décrit comment résoudre les problèmes potentiels que vous pouvez rencontrer lors du développement d’applications avec .NET Native.

- **Problématique** La fenêtre de sortie de la génération n’est pas correctement mise à jour.

  **Résolution :** La fenêtre sortie de la génération n’est mise à jour qu’une fois la génération terminée. La génération pouvant prendre plusieurs minutes, les mises à jour peuvent mettre du temps à apparaître.

- **Problématique** Le temps de génération de la version commerciale de votre application pour ARM a augmenté.

  **Résolution :** Lorsque vous déployez une application sur votre appareil ARM, l’infrastructure .NET Native est appelée. Cette compilation effectue un grand nombre d'optimisations tout en garantissant que la sémantique non statique telle que la réflexion continue de fonctionner. En outre, la partie du .NET Framework que l'application utilise est liée de manière statique pour optimiser les performances et doit être compilée en code natif également. C'est pourquoi la compilation prend plus de temps.

  Toutefois, les temps de compilation ne dépassent pas de plus d'une minute la compilation standard de la plupart des applications sur un ordinateur de développement ordinaire.  En règle générale, la seule génération d'images natives pour le .NET Framework sur un ordinateur de développement standard prend plusieurs minutes.  Même avec le .NET Framework et toutes les optimisations visant à améliorer le code généré, la génération des applications dure généralement une ou deux minutes.

  Nous allons continuer à travailler sur l'amélioration des performances de la compilation en nous penchant sur la compilation multithread et sur d'autres optimisations.

- **Problématique** Vous ne savez pas si votre application a été compilée à l’aide de .NET Native.

  **Résolution :** Si le compilateur .NET Native est appelé, vous remarquerez des temps de génération plus longs et le gestionnaire des tâches affichera différents processus de .NET Native composant, tels que ILC. exe et nutc_driver. exe.

  Une fois que vous avez correctement généré votre projet avec .net native, vous trouverez la sortie\\sous obj*config*\ *ARCH*\\*ProjectName*. ilc\out.  Le contenu du package natif final se trouve sous bin\\*arch*\\*config*\AppX. Il se trouve sous \bin\\*arch*\\*config*\AppX si vous avez déployé l’application.

- **Problématique** Votre application compilée par .NET Native lève des exceptions Runtime (généralement des exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md) ou [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ) qu’elle n’a pas levée lorsqu’elle est compilée sans .net native.

  **Résolution :** Les exceptions sont levées, car .NET Native n’a pas fourni les métadonnées ou le code d’implémentation qui est autrement disponible via la réflexion. (Pour plus d’informations, consultez [.NET Native et compilation](net-native-and-compilation.md).) Pour éliminer l’exception, vous devez ajouter une entrée à votre [fichier de directives d’exécution (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md) afin que la chaîne d’outils .NET natif puisse rendre les métadonnées ou le code d’implémentation disponibles lors de l’exécution. Deux utilitaires de résolution des problèmes sont disponibles, qui vont générer l'entrée nécessaire pour effectuer des ajouts à votre fichier de directives d'exécution :

  - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;

  - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.

  Pour plus d’informations, consultez [Réflexion et .NET Native](reflection-and-net-native.md).

## <a name="see-also"></a>Voir aussi

- [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md)
