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
ms.openlocfilehash: dcf2ce8bdb7cec1f567e548ff3314e160fffe9fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616630"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx, fonction
Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus. Les fonctions [CorBindToRuntime](corbindtoruntime-function.md) et `CorBindToRuntimeEx` effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
 Cette fonction prend un ensemble de paramètres qui permettent à un hôte d’effectuer les opérations suivantes :  
  
- Spécifiez la version du runtime qui sera chargée.  
  
- Indiquez si la build du serveur ou de la station de travail doit être chargée.  
  
- Contrôler si les garbage collection simultanées garbage collection ou non simultanées sont effectuées.  
  
> [!NOTE]
> Le garbage collection simultané n’est pas pris en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Contrôler si les assemblys sont chargés comme étant indépendants du domaine.  
  
- Obtenez un pointeur d’interface vers un [ICorRuntimeHost](icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.  
  
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
 dans Chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*. La chaîne transmise comme `pwszVersion` doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).  
  
 Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le shim de démarrage est évalué par `pwszVersion` rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée. Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la version exacte spécifiée dans `pwszVersion` en passant une valeur `STARTUP_LOADER_SAFEMODE` pour le `startupFlags` paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie null pour `pwszVersion` , `CorBindToRuntimeEx` identifie le jeu de runtimes installés dont les numéros de version sont inférieurs au Runtime .NET Framework 4 et charge la version la plus récente du runtime à partir de ce jeu. Il ne chargera pas le .NET Framework 4 ou version ultérieure et échouera si aucune version antérieure n’est installée. Notez que le passage de la valeur null donne à l’hôte aucun contrôle sur la version du runtime qui est chargée. Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR. Les valeurs valides sont `svr` et `wks`. La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.  
  
 Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée. Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr` . Toutefois, si `pwszBuildFlavor` a la valeur `svr` et que garbage collection simultané est spécifié (voir la description du `startupFlags` paramètre), la build du serveur est chargée.  
  
 `startupFlags`  
 dans Combinaison de valeurs de l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) . Ces indicateurs contrôlent les garbage collection simultanés, le code indépendant du domaine et le comportement du `pwszVersion` paramètre. La valeur par défaut est un domaine unique si aucun indicateur n’est défini. Les valeurs suivantes sont valides :  
  
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
  
 Pour obtenir une description de ces indicateurs, consultez l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) .  
  
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
  
    2. Pour les interfaces d’hébergement non managées, définissez l' `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `startupFlags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.  
  
     Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](corbindtocurrentruntime-function.md)
- [CorBindToRuntime, fonction](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, fonction](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost, fonction](corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
