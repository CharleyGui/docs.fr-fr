---
title: CorBindToRuntimeHost, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1965917e8a1c5ae07cf119df3664b969a979be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969249"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost, fonction
Permet aux hôtes de charger une version spécifiée du common language runtime (CLR) dans un processus.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszVersion`  
 dans Chaîne qui décrit la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*. La chaîne transmise `pwszVersion` comme doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).  
  
 Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le shim de démarrage est `pwszVersion` évalué par rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée. Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la `pwszVersion` version exacte spécifiée dans en passant une valeur `startupFlags` de STARTUP_LOADER_SAFEMODE pour le paramètre.  
  
 Si `pwszVersion` est`null,` , la méthode ne charge aucune version du CLR. Au lieu de cela, elle retourne CLR_E_SHIM_RUNTIMELOAD, ce qui indique qu’elle n’a pas pu charger le Runtime.  
  
 `pwszBuildFlavor`  
 dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR. Les valeurs valides sont `svr` et `wks`. La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.  
  
 Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée. Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail `pwszBuildFlavor` est toujours chargée `svr`, même si a la valeur. Toutefois, si `pwszBuildFlavor` a la `svr` valeur et que garbage collection simultané est spécifié ( `startupFlags` Voir la description du paramètre), la build du serveur est chargée.  
  
> [!NOTE]
> Le garbage collection simultané n’est pas pris en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 dans Nom d’un fichier de configuration d’hôte qui spécifie la version du CLR à charger. Si le nom de fichier n’inclut pas de chemin d’accès qualifié complet, le fichier est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.  
  
 `pReserved`  
 dans Réservé pour une future extensibilité.  
  
 `startupFlags`  
 dans Jeu d’indicateurs qui contrôle les garbage collection simultanées, le code indépendant du domaine et le comportement du `pwszVersion` paramètre. La valeur par défaut est un domaine unique si aucun indicateur n’est défini. Pour obtenir la liste des valeurs prises en charge, consultez l' [énumération STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] `CLSID` de la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md). Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 dans `IID` De l’interface que vous demandez. Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 à Pointeur d’interface vers la version du runtime qui a été chargée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.idl  
  
 **Bibliothèque** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
