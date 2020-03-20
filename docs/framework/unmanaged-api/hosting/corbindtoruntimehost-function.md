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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176485"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost, fonction
Permet aux hôtes de charger une version spécifiée de l’heure d’exécution de la langue commune (CLR) dans un processus.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
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
 [dans] Une chaîne qui décrit la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*. La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").  
  
 Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée. Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de la politique et `startupFlags` charger la version exacte spécifiée en passant une valeur de STARTUP_LOADER_SAFEMODE pour le paramètre.  
  
 Si `pwszVersion` `null,` c’est la méthode ne charge aucune version du CLR. Au lieu de cela, il retourne CLR_E_SHIM_RUNTIMELOAD, ce qui indique qu’il n’a pas réussi à charger le temps d’exécution.  
  
 `pwszBuildFlavor`  
 [dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR. Les valeurs valides sont `svr` et `wks`. La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.  
  
 S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée. Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à . Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `startupFlags` concomitante (voir la description du paramètre), la construction du serveur est chargée.  
  
> [!NOTE]
> La collecte simultanée des ordures n’est pas prise en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, voir [Exécution des applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [dans] Le nom d’un fichier de configuration hôte qui spécifie la version du CLR à charger. Si le nom du fichier n’inclut pas un chemin entièrement qualifié, le fichier est supposé être dans le même répertoire que l’exécutable qui fait l’appel.  
  
 `pReserved`  
 [dans] Réservé à l’extensibility future.  
  
 `startupFlags`  
 [dans] Un ensemble de drapeaux qui contrôle la collecte simultanée des `pwszVersion` ordures, le code neutre sur le domaine et le comportement du paramètre. La valeur par défaut est un domaine unique si aucun indicateur n’est défini. Pour une liste de valeurs soutenues, voir le [STARTUP_FLAGS énumération](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [dans] L’interface `IID` que vous demandez. Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Un pointeur d’interface à la version du temps d’exécution qui a été chargé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.idl MSCorEE.idl  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
