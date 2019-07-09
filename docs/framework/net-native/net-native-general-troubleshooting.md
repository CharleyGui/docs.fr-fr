---
title: Résolution des problèmes généraux liés à .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9599ee25e77bf6f44e5c6733deed8dc23fc0d022
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662323"
---
# <a name="net-native-general-troubleshooting"></a>Résolution des problèmes généraux liés à .NET Native

Cette rubrique décrit comment résoudre les problèmes potentiels que vous pouvez rencontrer lors du développement d’applications avec .NET Native.

- **Problème :** La fenêtre de sortie de génération n’est pas correctement mis à jour.

  **Résolution :** La fenêtre de sortie de build n’est pas mis à jour jusqu'à ce que la génération terminée. La génération pouvant prendre plusieurs minutes, les mises à jour peuvent mettre du temps à apparaître.

- **Problème :** Temps de génération de vente au détail de votre application pour ARM a augmenté.

  **Résolution :** Lorsque vous déployez une application sur votre appareil ARM, l’infrastructure .NET Native est appelé. Cette compilation effectue un grand nombre d'optimisations tout en garantissant que la sémantique non statique telle que la réflexion continue de fonctionner. En outre, la partie du .NET Framework que l'application utilise est liée de manière statique pour optimiser les performances et doit être compilée en code natif également. C'est pourquoi la compilation prend plus de temps.

  Toutefois, les temps de compilation ne dépassent pas de plus d'une minute la compilation standard de la plupart des applications sur un ordinateur de développement ordinaire.  En règle générale, la seule génération d'images natives pour le .NET Framework sur un ordinateur de développement standard prend plusieurs minutes.  Même avec le .NET Framework et toutes les optimisations visant à améliorer le code généré, la génération des applications dure généralement une ou deux minutes.

  Nous allons continuer à travailler sur l'amélioration des performances de la compilation en nous penchant sur la compilation multithread et sur d'autres optimisations.

- **Problème :** Vous ne savez pas si votre application a été compilée à l’aide de .NET Native.

  **Résolution :** Si le compilateur .NET Native est appelé, vous remarquerez que les durées de génération plus de temps et le Gestionnaire des tâches affiche divers processus de composant .NET Native, comme ILC.exe et nutc_driver.exe.

  Une fois que vous avez correctement généré votre projet avec .NET Native, vous trouverez la sortie sous obj\\*config*\ *arch*\\*nom_projet*. ilc\out.  Le contenu du package natif final se trouve sous bin\\*arch*\\*config*\AppX. Il se trouve sous \bin\\*arch*\\*config*\AppX si vous avez déployé l’application.

- **Problème :** Votre application .NET natif lève des exceptions runtime (généralement [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ou [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions) qu’il n’a pas levé lorsque compilé sans. NET Native.

  **Résolution :** Les exceptions sont levées, car .NET Native n’a pas fourni les métadonnées ou le code d’implémentation qui est normalement disponible via la réflexion. (Pour plus d’informations, consultez [.NET Native et compilation](../../../docs/framework/net-native/net-native-and-compilation.md).) Pour éliminer l’exception, vous devez ajouter une entrée à votre [fichier de directives d’exécution (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) afin que la chaîne d’outils .NET natif puisse rendre les métadonnées ou le code d’implémentation disponibles lors de l’exécution. Deux utilitaires de résolution des problèmes sont disponibles, qui vont générer l'entrée nécessaire pour effectuer des ajouts à votre fichier de directives d'exécution :

  - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;

  - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.

  Pour plus d’informations, consultez [Réflexion et .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).

## <a name="see-also"></a>Voir aussi

- [Migration de votre application du Windows Store vers .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
