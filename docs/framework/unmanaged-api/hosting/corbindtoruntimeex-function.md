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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490584"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx, fonction
Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus. Le [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` fonctions effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
 Cette fonction accepte un ensemble de paramètres qui permettent à un hôte effectuer les opérations suivantes :  
  
- Spécifiez la version du runtime qui est chargée.  
  
- Indiquer si la build du serveur ou station de travail doit être chargée.  
  
- Contrôler si le garbage collection simultané ou le garbage collection non simultané est effectué.  
  
> [!NOTE]
>  Le garbage collection simultané n’est pas pris en charge dans les applications en cours d’exécution WOW64 x86 émulateur sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [Applications en cours d’exécution de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Contrôler si les assemblys sont chargés comme indépendants du domaine.  
  
- Obtenir un pointeur d’interface vers un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Une chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*. La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).  
  
 Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le shim de démarrage évalue `pwszVersion` contre les instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée. Un hôte peut obliger le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en transmettant une valeur de `STARTUP_LOADER_SAFEMODE` pour le `startupFlags` paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie null pour `pwszVersion`, `CorBindToRuntimeEx` identifie l’ensemble des runtimes installés, dont les numéros de version sont inférieurs à ceux de l’exécution de .NET Framework 4 et chargement la dernière version du runtime à partir de cet ensemble. Il ne charge pas le .NET Framework 4 ou version ultérieure et échoue si aucune version antérieure n’est installée. Notez que passer une valeur null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée. Bien que cette approche peut être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 [in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR. Les valeurs valides sont `svr` et `wks`. La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.  
  
 Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée. Lors de l’exécution sur un ordinateur monoprocesseur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` est défini sur `svr`. Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `startupFlags` paramètre), la build du serveur est chargée.  
  
 `startupFlags`  
 [in] Une combinaison de valeurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération. Ces indicateurs contrôlent le garbage collection simultané, code indépendant du domaine et le comportement de le `pwszVersion` paramètre. La valeur par défaut est le domaine unique si aucun indicateur n’est défini. Les valeurs suivantes sont valides :  
  
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
  
 Pour obtenir une description de ces indicateurs, consultez la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération.  
  
 `rclsid`  
 [in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] Le `IID` de l’interface demandée à partir de `rclsid`. Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Le pointeur d’interface retourné à `riid`.  
  
## <a name="remarks"></a>Notes  
 Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexte d’exécution et les flux d’identité de Windows  
 Dans la version 1 du CLR, le <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmise entre des points asynchrones telles que les nouveaux threads, pools de threads ou rappels de la minuterie. Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et il transite d’un point asynchrone, mais pas entre les limites du domaine d’application. De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone. Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.  
  
 Vous pouvez modifier le flux de deux manières :  
  
1. En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur un thread par thread (voir la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).  
  
2. En modifiant le mode par défaut de processus en mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel. Comment vous modifier le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :  
  
    1. Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.  
  
    2. Pour les interfaces d’hébergement non managées, définissez le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `startupFlags` paramètre lors de l’appel le `CorBindToRuntimeEx` (fonction).  
  
     Le mode de compatibilité de version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
