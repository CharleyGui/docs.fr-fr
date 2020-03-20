---
title: CorBindToRuntime, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176511"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime, fonction
Permet aux hôtes non gérés de charger l’heure d’exécution de la langue commune (CLR) dans un processus.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszVersion`  
 [dans] Une chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*. La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").  
  
 Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée. Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de `STARTUP_LOADER_SAFEMODE` la `flags` politique et charger la version exacte spécifiée en passant une valeur de pour le paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie nulle pour `pwszVersion`, la dernière version de l’heure d’exécution est chargée. Passer nul ne donne à l’hôte aucun contrôle sur la version du temps d’exécution est chargée. Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 [dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR. Les valeurs valides sont `svr` et `wks`. La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.  
  
 S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée. Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à . Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `flags` concomitante (voir la description du paramètre), la construction du serveur est chargée.  
  
 `rclsid`  
 [dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [dans] L’interface `IID` demandée `rclsid`de . Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Le pointeur `riid`d’interface retourné à .  
  
## <a name="remarks"></a>Notes   
 Si `pwszVersion` spécifie une version de `CorBindToRuntimeEx` temps d’exécution qui n’existe pas, renvoie une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexte d’exécution et flux de l’identité de Windows  
 Dans la version 1 du <xref:System.Security.Principal.WindowsIdentity> CLR, l’objet ne circule pas à travers des points asynchrones tels que de nouveaux fils, des pools de threads ou des rappels de minuterie. Dans la version 2.0 du <xref:System.Threading.ExecutionContext> CLR, un objet enveloppe certaines informations sur le thread qui exécute actuellement et le fait couler à travers n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application. De même, l’objet <xref:System.Security.Principal.WindowsIdentity> s’écoule également à travers n’importe quel point asynchrone. Par conséquent, l’usurpation d’identité actuelle sur le fil, le cas échéant, coule aussi.  
  
 Vous pouvez modifier le flux de deux façons :  
  
1. En modifiant <xref:System.Threading.ExecutionContext> les paramètres pour supprimer le flux par <xref:System.Threading.ExecutionContext.SuppressFlow%2A>fil <xref:System.Security.SecurityContext.SuppressFlow%2A>(voir le , , et les <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).  
  
2. En changeant le mode par défaut de processus au <xref:System.Security.Principal.WindowsIdentity> mode de compatibilité de la version 1, lorsque l’objet ne circule pas sur un point asynchrone, indépendamment des <xref:System.Threading.ExecutionContext> paramètres du thread actuel. La façon dont vous modifiez le mode par défaut dépend si vous utilisez une interface d’hébergement exécutable gérée ou non gérée pour charger le CLR :  
  
    1. Pour les exécutables `enabled` gérés, vous devez définir l’attribut de [ \<l’héritageImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.  
  
    2. Pour les interfaces d’hébergement `STARTUP_LEGACY_IMPERSONATION` non gestion, définissez le drapeau dans le `flags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.  
  
     Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.  
  
## <a name="remarks"></a>Notes   
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` et effectuer la même `CorBindToRuntimeEx` opération, mais la fonction vous permet de définir des drapeaux pour spécifier le comportement du CLR.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
