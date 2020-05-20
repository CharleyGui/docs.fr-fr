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
ms.openlocfilehash: 0bcfe42a70d64c091851a1eec81d03e49dbde52b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616660"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime, fonction
Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
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
 dans Chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*. La chaîne transmise comme `pwszVersion` doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).  
  
 Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le shim de démarrage est évalué par `pwszVersion` rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée. Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la version exacte spécifiée dans `pwszVersion` en passant une valeur `STARTUP_LOADER_SAFEMODE` pour le `flags` paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie null pour `pwszVersion` , la version la plus récente du runtime est chargée. Le passage de la valeur null donne à l’hôte aucun contrôle sur la version du runtime qui est chargée. Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR. Les valeurs valides sont `svr` et `wks`. La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.  
  
 Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée. Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr` . Toutefois, si `pwszBuildFlavor` a la valeur `svr` et que garbage collection simultané est spécifié (voir la description du `flags` paramètre), la build du serveur est chargée.  
  
 `rclsid`  
 dans `CLSID`De la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) . Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 dans `IID`De l’interface demandée à partir de `rclsid` . Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 à Pointeur d’interface retourné à `riid` .  
  
## <a name="remarks"></a>Notes  
 Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexte d’exécution et le workflow de l’identité Windows  
 Dans la version 1 du CLR, l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones tels que les nouveaux threads, les pools de threads ou les rappels de minuterie. Dans la version 2,0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et le transmet sur n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application. De même, l' <xref:System.Security.Principal.WindowsIdentity> objet circule également sur n’importe quel point asynchrone. Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.  
  
 Vous pouvez modifier le Flow de deux manières :  
  
1. En modifiant les <xref:System.Threading.ExecutionContext> paramètres pour supprimer le workflow pour chaque thread (consultez les <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> méthodes, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).  
  
2. En remplaçant le mode de traitement par défaut par le mode de compatibilité de la version 1, où l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis sur un point asynchrone, quels que soient les <xref:System.Threading.ExecutionContext> paramètres du thread en cours. La façon dont vous modifiez le mode par défaut varie selon que vous utilisez un exécutable managé ou une interface d’hébergement non managée pour charger le CLR :  
  
    1. Pour les exécutables managés, vous devez affecter la valeur `enabled` à l’attribut de l’élément [ \< legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .  
  
    2. Pour les interfaces d’hébergement non managées, définissez l' `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `flags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.  
  
     Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.  
  
## <a name="remarks"></a>Notes  
 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) et `CorBindToRuntime` effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, fonction](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, fonction](corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
