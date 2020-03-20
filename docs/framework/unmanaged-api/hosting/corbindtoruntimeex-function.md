---
title: CorBindToRuntimeEx, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176498"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx, fonction
Permet aux hôtes non gérés de charger l’heure d’exécution de la langue commune (CLR) dans un processus. Le [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` les fonctions effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des drapeaux pour spécifier le comportement du CLR.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
 Cette fonction prend un ensemble de paramètres qui permettent à un hôte de faire ce qui suit:  
  
- Spécifier la version de l’exécution qui sera chargée.  
  
- Indiquez si la construction du serveur ou du poste de travail doit être chargée.  
  
- Contrôlez si la collecte simultanée des ordures ou la collecte non simultanée des ordures est effectuée.  
  
> [!NOTE]
> La collecte simultanée des ordures n’est pas prise en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, voir [Exécution des applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Contrôlez si les assemblages sont chargés comme neutres sur le plan de domaine.  
  
- Obtenez un pointeur d’interface à un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant qu’il ne soit commencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszVersion`  
 [dans] Une chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*. La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").  
  
 Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée. Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de `STARTUP_LOADER_SAFEMODE` la `startupFlags` politique et charger la version exacte spécifiée en passant une valeur de pour le paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie nulle pour `pwszVersion`, `CorBindToRuntimeEx` identifie l’ensemble de temps d’exécution installés dont les numéros de version sont inférieurs à la .NET Framework 4 runtime, et charge la dernière version de l’exécution de cet ensemble. Il ne chargera pas le cadre .NET 4 ou plus tard, et échoue si aucune version antérieure n’est installée. Notez que le passage nul ne donne à l’hôte aucun contrôle sur la version du temps d’exécution est chargée. Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 [dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR. Les valeurs valides sont `svr` et `wks`. La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.  
  
 S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée. Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à . Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `startupFlags` concomitante (voir la description du paramètre), la construction du serveur est chargée.  
  
 `startupFlags`  
 [dans] Une combinaison de valeurs de [l’STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) de l’énumération. Ces drapeaux contrôlent la collecte simultanée des ordures, le code neutre en matière de domaine et le comportement du `pwszVersion` paramètre. La valeur par défaut est un domaine unique si aucun indicateur n’est défini. Les valeurs suivantes sont valides :  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Pour les descriptions de ces drapeaux, voir le [recensement STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
  
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
  
    2. Pour les interfaces d’hébergement `STARTUP_LEGACY_IMPERSONATION` non gestion, définissez le drapeau dans le `startupFlags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.  
  
     Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
