---
title: Fournisseurs ETW du CLR
description: 'Passez en revue les détails sur les deux fournisseurs d’événements ETW (Event Tracing for Windows) common language runtime (CLR) : le fournisseur runtimne et le fournisseur d’arrêt.'
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 9f86e8334482880c4f7cb23ec93a3c826c083389
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309649"
---
# <a name="clr-etw-providers"></a>Fournisseurs ETW du CLR
Le Common Language Runtime (CLR) a deux fournisseurs : le fournisseur de runtime et le fournisseur d’arrêt.  
  
 Le fournisseur de runtime déclenche des événements en fonction des mots clés (catégories d’événements) activés. Par exemple, vous pouvez collecter des événements de chargeur en activant le mot clé `LoaderKeyword`.  
  
 Les événements de Suivi d’v nements pour Windows (ETW) sont enregistrés dans un fichier qui a une extension. etl, qui peut être postérieurement traité dans des fichiers de valeurs séparées par des virgules (. csv) si nécessaire. Pour plus d’informations sur la façon de convertir le fichier .etl en fichier .csv, consultez [Controlling .NET Framework Logging](controlling-logging.md) (Contrôle de la journalisation du .NET Framework).  
  
## <a name="the-runtime-provider"></a>Fournisseur de runtime  
 Le fournisseur de runtime est le principal fournisseur ETW du CLR.  
  
 Le GUID du fournisseur de runtime du CLR est e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Pour obtenir des exemples de journalisation et d’affichage des événements ETW du CLR à l’aide d’outils courants, consultez [Contrôle de la journalisation du .NET Framework](controlling-logging.md).  
  
 En plus des mots clés tels que `LoaderKeyword`, vous devrez éventuellement activer des mots clés pour la journalisation des événements qui se déclenchent trop fréquemment. Les mots clés `StartEnumerationKeyword` et `EndEnumerationKeyword` activent ces événements et sont résumés dans [Mots clés et niveaux CLR ETW](clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Fournisseur d’arrêt  
 Le fournisseur d’arrêt doit être activé dans certains cas bien précis. Toutefois, pour la plupart des utilisateurs, le fournisseur de runtime est tout à fait suffisant.  
  
 Le GUID du fournisseur d’arrêt du CLR est A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Normalement, la journalisation ETW est activée avant le lancement d’un processus et désactivée une fois ce processus arrêté. Toutefois, si la journalisation ETW est activée pendant l’exécution du processus, des informations supplémentaires sur celui-ci sont demandées. Par exemple, pour la résolution des symboles, vous devez journaliser les événements de méthode pour les méthodes qui ont été chargées avant l’activation de la journalisation.  
  
 Les événements `DCStart` et `DCEnd` capturent l’état du processus au moment où la collecte de données a commencé et où elle s’est arrêtée. (L’État fait référence à des informations à un niveau élevé, y compris les méthodes qui étaient déjà compilées juste-à-temps (JIT) et les assemblys qui ont été chargés.) Ces deux événements peuvent fournir des informations sur ce qui s’est déjà produit dans le processus. par exemple, les méthodes qui ont été compilées juste-à-temps, et ainsi de suite.  
  
 Seuls les événements dont le nom contient `DC`, `DCStart`, `DCEnd` ou `DCInit` sont déclenchés sous le fournisseur d’arrêt. Par ailleurs, ces événements sont déclenchés uniquement sous ce fournisseur.  
  
 En plus des filtres par mots clés d’événement, le fournisseur d’arrêt prend en charge les mots clés `StartRundownKeyword` et `EndRundownKeyword` pour permettre un filtrage ciblé.  
  
### <a name="start-rundown"></a>Arrêt de début  
 Un arrêt de début est déclenché quand la journalisation sous le fournisseur d’arrêt est activée avec le mot clé `StartRundownKeyword`. Cela entraîne le déclenchement de l’événement `DCStart` et la capture de l’état du système. Avant le démarrage de l’énumération, l’événement `DCStartInit` est déclenché. À la fin de l’énumération, l’événement `DCStartComplete` est déclenché pour indiquer au contrôleur que la collecte de données s’est terminée normalement.  
  
### <a name="end-rundown"></a>Arrêt de fin  
 Un arrêt de fin est déclenché quand la journalisation sous le fournisseur d’arrêt est activée avec le mot clé `EndRundownKeyword`. L’arrêt de fin arrête le profilage sur un processus qui continue de s’exécuter. Les événements `DCEnd` capturent l’état du système quand le profilage est arrêté.  
  
 Avant le démarrage de l’énumération, l’événement `DCEndInit` est déclenché. À la fin de l’énumération, l’événement `DCEndComplete` est déclenché pour indiquer au consommateur que la collecte de données s’est terminée normalement. Les arrêts de début et de fin sont principalement utilisés pour la résolution de symboles managés. L’arrêt de début peut fournir des informations sur les plages d’adresses des méthodes qui ont été compilées juste-à-temps (JIT) avant le début de la session de profilage. L’arrêt de fin peut fournir des informations sur les plages d’adresses de toutes les méthodes qui ont été compilées juste-à-temps (JIT) quand le profilage est sur le point d’être désactivé.  
  
 L’arrêt de fin ne se produit pas automatiquement quand une session de profilage est arrêtée. Au lieu de cela, un outil qui cherche à exécuter la résolution de symboles managés doit appeler explicitement une session du fournisseur d’arrêt du CLR avec le mot clé `EndRundownKeyword` activé, juste avant l’arrêt du profilage.  
  
 Bien que l’arrêt de début ou de fin puisse fournir des informations de plage d’adresses de méthodes pour la résolution de symboles managés, nous vous recommandons d’utiliser le mot clé `EndRundownKeyword` (qui fournit des événements `DCEnd`) plutôt que le mot clé `StartRundownKeyword` (qui fournit des événements `DCStart`). L’utilisation de `StartRundownKeyword` entraîne l’arrêt de la session de profilage, ce qui peut perturber le scénario profilé.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Collecte de données ETW à l’aide des fournisseurs de runtime et d’arrêt  
 L’exemple suivant montre comment utiliser le fournisseur d’arrêt du CLR d’une façon qui autorise la résolution des symboles des processus managés avec un impact minimal, indépendamment du fait que les processus démarrent ou se terminent à l’intérieur ou à l’extérieur de la fenêtre profilée.  
  
1. Activez la journalisation ETW à l’aide du fournisseur de runtime du CLR :  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     Le journal sera enregistré dans le fichier clr1.etl.  
  
2. Pour arrêter le profilage alors que le processus continue à s’exécuter, démarrez le fournisseur d’arrêt pour capturer les événements `DCEnd` :  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     Cela permet à la collecte d’événements `DCEnd` de démarrer une session d’arrêt. Vous devrez peut-être patienter 30 à 60 secondes pour que tous les événements soient collectés. Le journal sera enregistré dans le fichier clr1.et2.  
  
3. Désactivez tout le profilage ETW :  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. Fusionnez les profils pour créer un fichier journal :  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Le fichier merged.etl contient les événements des sessions des fournisseurs de runtime et d’arrêt.  
  
 Un outil peut exécuter les étapes 2 et 3 (démarrage d’une session d’arrêt, puis arrêt du profilage) au lieu de désactiver immédiatement le profilage quand un utilisateur demande son arrêt. Un outil peut également exécuter l’étape 4.  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW dans le Common Language Runtime](etw-events-in-the-common-language-runtime.md)
