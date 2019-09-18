---
title: Exceptions du runtime dans les applications natives .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27a2e0906343d115c47230c726efb74cd51d4c93
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049162"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Exceptions du runtime dans les applications natives .NET
Il est important de tester les versions release de votre application de plateforme Windows universelle sur leurs plateformes cibles, car les configurations debug et release sont totalement différentes. Par défaut, la configuration debug utilise le runtime .NET Core pour compiler votre application, mais la configuration release utilise .NET Native pour compiler votre application en code natif.  
  
> [!IMPORTANT]
> Pour plus d’informations sur la gestion des exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)et [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) que vous pouvez rencontrer lors du test des versions release de votre application, consultez la section «étape 4 : Résoudre manuellement les métadonnées manquantes : dans la rubrique [prise en main](getting-started-with-net-native.md) , ainsi que la référence du fichier de configuration de la [réflexion et des .net Native](reflection-and-net-native.md) et des [directives Runtime (Rd. Xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Versions debug et release  
 Quand la version debug s’exécute sur le runtime .NET Core, elle n’a pas été compilée en code natif. Ainsi, tous les services normalement fournis par le runtime sont accessibles à votre application.  
  
 D’autre part, la version release est compilée en code natif pour ses plateformes cibles, elle supprime la plupart des dépendances vis-à-vis des runtimes et bibliothèques externes et elle optimise largement le code à des fins de performances maximales.  
  
 Quand vous déboguez des versions release qui sont compilées à l’aide de .NET Native :  
  
- Vous utilisez le moteur de débogage .NET Native, qui est différent des outils de débogage .NET normaux.  
  
- La taille de votre fichier exécutable est réduite autant que possible. L’une des façons employées par .NET Native pour réduire la taille d’un fichier exécutable est en filtrant considérablement les messages d’exception d’exécution, un sujet abordé de façon plus détaillée dans la section [Runtime exception messages](#Messages) .  
  
- Votre code est largement optimisé. Cela signifie que cette incorporation est utilisée dès que possible. (L’incorporation déplace le code depuis les routines externes vers la routine d’appel.)   Le fait que .NET Native fournisse un runtime spécialisé et implémente une incorporation agressive affecte la pile des appels qui s’affiche lors du débogage.  Pour plus d’informations, consultez la section [Runtime call stack](#CallStack) .  
  
> [!NOTE]
> Vous pouvez déterminer si les versions debug et release sont compilées avec la chaîne d’outils .NET Native en cochant ou non la case **Compiler avec la chaîne de l’outil du code natif .NET** .   Notez quand même que le Windows Store compile toujours la version de production de votre application avec la chaîne d’outils .NET Native.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Runtime exception messages  
 Pour réduire la taille de l’exécutable de l’application, .NET Native n’inclut pas le texte complet des messages d’exception. Ainsi, les exceptions du runtime levées dans les versions release risquent de ne pas afficher le texte complet des messages d’exception. Le texte peut plutôt consister en une sous-chaîne assortie d’un lien à suivre pour plus d’informations. Par exemple, les informations sur l’exception peuvent apparaître comme suit :  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Si vous avez besoin de consulter la totalité du message d’exception, exécutez plutôt la version debug. Par exemple, les informations sur l’exception précédente issues de la version release peuvent apparaître comme suit dans la version debug :  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Runtime call stack  
 Du fait de l’incorporation et des autres optimisations, la pile des appels affichée par une application compilée par la chaîne d’outils .NET Native risque de ne pas vous aider à identifier clairement le chemin vers une exception runtime.  
  
 Pour obtenir la pile complète, exécutez plutôt la version debug.  
  
## <a name="see-also"></a>Voir aussi

- [Débogage .NET Native des applications universelles Windows](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Prise en main](getting-started-with-net-native.md)
