---
title: Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 6ee3b8cdf348a5eade3903e2d26b4f9b93886305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706812"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5

Cette section décrit les interfaces que les hôtes non gérés peuvent utiliser pour intégrer le common language runtime (CLR) des .NET Framework 4, .NET Framework 4,5 et versions ultérieures dans leurs applications. Ces interfaces fournissent des méthodes permettant à un hôte de configurer et de charger le runtime dans un processus.  
  
 À partir du .NET Framework 4, toutes les interfaces d’hébergement présentent les caractéristiques suivantes :  
  
- Ils utilisent la gestion de la durée de vie ( `AddRef` et `Release` ), l’encapsulation (contexte implicite) et `QueryInterface` à partir de com.  
  
- Ils n’utilisent pas les types COM tels que `BSTR` , `SAFEARRAY` ou `VARIANT` .  
  
- Il n’existe pas de modèles cloisonnés, d’agrégation ou d’activation du Registre qui utilisent la [fonction CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="in-this-section"></a>Dans cette section  

 [ICLRAppDomainResourceMonitor, interface](iclrappdomainresourcemonitor-interface.md)  
 Fournit des méthodes qui inspectent la mémoire et l’utilisation de l’UC d’un domaine d’application.  
  
 [ICLRDomainManager, interface](iclrdomainmanager-interface.md)  
 Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.  
  
 [ICLRGCManager2, interface](iclrgcmanager2-interface.md)  
 Fournit la méthode [setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) , qui permet à un hôte de définir la taille du segment garbage collection et la taille maximale de la génération 0 du système garbage collection à des valeurs supérieures à `DWORD` .  
  
 [ICLRMetaHost, interface](iclrmetahost-interface.md)  
 Fournit des méthodes qui retournent une version spécifique du CLR, répertorient tous les CLR installés, répertorient tous les runtimes in-process, retournent l’interface d’activation et découvrent la version CLR utilisée pour compiler un assembly.  
  
 [ICLRMetaHostPolicy, interface](iclrmetahostpolicy-interface.md)  
 Fournit la méthode [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) qui fournit une interface CLR basée sur des critères de stratégie, un assembly managé, une version et un fichier de configuration.  
  
 [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)  
 Fournit des méthodes qui retournent des informations sur un Runtime spécifique, y compris la version, le répertoire et l’état de chargement.  
  
 [ICLRStrongName, interface](iclrstrongname-interface.md)  
 Fournit des fonctions statiques globales de base pour la signature d’assemblys avec des noms forts. Toutes les méthodes [ICLRStrongName](iclrstrongname-interface.md) retournent des valeurs HRESULT com standard.  
  
 [ICLRStrongName2, interface](iclrstrongname2-interface.md)  
 Offre la possibilité de créer des noms forts à l’aide du groupe SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).  
  
 [ICLRTask2, interface](iclrtask2-interface.md)  
 Fournit toutes les fonctionnalités de l' [interface ICLRTask](iclrtask-interface.md); en outre, fournit des méthodes qui permettent de retarder les abandons de thread sur le thread actuel.  
  
## <a name="related-sections"></a>Sections connexes  

 [Interfaces d'hébergement du CLR et coclasses déconseillées](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Décrit les interfaces d’hébergement fournies avec les versions de .NET Framework 1,0 et 1,1.  
  
 [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)  
 Décrit les interfaces d’hébergement fournies avec les versions .NET Framework 2,0, 3,0 et 3,5.  
  
 [Hébergement](index.md)  
 Présente l’hébergement dans le .NET Framework.
