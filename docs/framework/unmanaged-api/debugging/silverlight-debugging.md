---
title: Débogage Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 49f026b8e1a3dd78a62091e77a5aba0c9a2e09d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671835"
---
# <a name="silverlight-debugging"></a>Débogage Silverlight

Les rubriques de cette section décrivent l'environnement et les interfaces fournis par le Common Language Runtime (CLR) pour prendre en charge le débogage des applications Silverlight qui s'exécutent sur le système d'exploitation Windows ou sur la plateforme Macintosh.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Fonction EnumerateCLRs](enumerateclrs-function.md)  
 Fournit un mécanisme pour énumérer les CLR dans un processus.  
  
 [Fonction CloseCLREnumeration](closeclrenumeration-function.md)  
 Ferme tous les événements continue-Startup valides du CLR situés dans un tableau de handles retournés par la [fonction EnumerateCLRs](enumerateclrs-function.md)et libère la mémoire pour les tableaux de handles et de chemins d’accès de chaîne.  
  
 [Fonction CreateCoreClrDebugTarget](createcoreclrdebugtarget-function.md)  
 Crée une connexion à une cible distante pour l'énumération des processus et du runtime.  
  
 [Fonction CreateCordbObject](createcordbobject-function.md)  
 Crée une interface de débogueur qui fournit les fonctionnalités d'instanciation d'une session de débogage managée sur un processus distant.  
  
 [Fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)  
 Crée une chaîne de version à partir d'un chemin d'accès au CLR dans un processus cible.  
  
 [CreateDebuggingInterfaceFromVersion, fonction](createdebugginginterfacefromversion-function-for-silverlight.md)  
 Accepte une chaîne de version CLR retournée par la fonction de [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante.  
  
 [Structure CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)  
 Représente un processus qui s'exécute sur un ordinateur distant.  
  
 [Structure CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md)  
 Représente une instance du CLR qui est chargée dans un processus sur un ordinateur distant.  
  
 [Fonction GetStartupNotificationEvent](getstartupnotificationevent-function.md)  
 Crée ou ouvre un gestionnaire d'événements qui sera signalé par un Common Language Runtime (CLR) qui est chargé dans le processus cible spécifié.  
  
 [Interface ICorDebugDataTarget](icoreclrdebugtarget-interface.md)  
 Crée une connexion à une cible distante pour l'énumération des processus et du runtime.  
  
 [Fonction InitDbgTransportManager](initdbgtransportmanager-function.md)  
 Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.  
  
 [Fonction ShutdownDbgTransportManager](shutdowndbgtransportmanager-function.md)  
 Arrête le gestionnaire de transport pour une connexion à un ordinateur cible distant.  
  
## <a name="see-also"></a>Voir aussi

- [Débogage des coclasses](debugging-coclasses.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Fonctions statiques globales du débogage](debugging-global-static-functions.md)
- [Énumérations de débogage](debugging-enumerations.md)
- [Structures de débogage](debugging-structures.md)
