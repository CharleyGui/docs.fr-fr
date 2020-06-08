---
title: ICLRMetaHostPolicy::GetRequestedRuntime, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 37167b7a9aefa6cd9d5e4df043e8bbc1b0514261
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504119"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime, méthode

Fournit une interface pour une version préférée du Common Language Runtime (CLR) basée sur une stratégie d'hébergement, un assembly managé, une chaîne de version et un flux de configuration. Cette méthode ne charge pas ou n’active pas le CLR, mais retourne simplement l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui représente le résultat de la stratégie. Cette méthode remplace les méthodes [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)et [GetCORRequiredVersion,](getcorrequiredversion-function.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a>Paramètres

|Nom|Description|
|----------|-----------------|
|`dwPolicyFlags`|[in] Obligatoire. Spécifie un membre de l’énumération [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , représentant une stratégie de liaison et un nombre quelconque de modificateurs. La seule stratégie actuellement disponible est [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).<br /><br /> Les modificateurs incluent [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)et [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] Facultatif. Spécifie le chemin d’accès de fichier d’assembly.|
|`pCfgStream`|[in] Facultatif. Spécifie le fichier de configuration en tant que <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[in, out] Facultatif. Spécifie ou retourne la version du CLR par défaut à charger.|
|`pcchVersion`|[in, out] Obligatoire. Spécifie la taille attendue de `pwzVersion` comme entrée, pour éviter les dépassements de mémoire tampon. Si `pwzVersion` a la valeur null, `pcchVersion` contient la taille attendue de `pwzVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation ; sinon, `pcchVersion` contient le nombre de caractères écrits dans `pwzVersion`.|
|`pwzImageVersion`|[out] Facultatif. Quand `GetRequestedRuntime` retourne la valeur, contient la version du CLR correspondant à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui est retournée.|
|`pcchImageVersion`|[in, out] Facultatif. Spécifie la taille de `pwzImageVersion` comme entrée pour éviter les dépassements de mémoire tampon. Si `pwzImageVersion` a la valeur null, `pcchImageVersion` contient la taille requise de `pwzImageVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation.|
|`pdwConfigFlags`|[out] Facultatif. Si `GetRequestedRuntime` utilise un fichier de configuration pendant le processus de liaison, quand il retourne, `pdwConfigFlags` contient une valeur [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) qui indique si l' [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) élément a l' `useLegacyV2RuntimeActivationPolicy` attribut défini et la valeur de l’attribut. Appliquez le masque [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) à `pdwConfigFlags` pour récupérer les valeurs correspondantes à `useLegacyV2RuntimeActivationPolicy` .|
|`riid`|dans Spécifie l’identificateur d’interface IID_ICLRRuntimeInfo pour l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) demandée.|
|`ppRuntime`|à Quand `GetRequestedRuntime` retourne une valeur, contient un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondante.|

## <a name="remarks"></a>Remarques

Quand cette méthode réussit, elle a comme effet secondaire de combiner des indicateurs supplémentaires avec les indicateurs de démarrage par défaut actuels de l'interface d'exécution retournée, si et seulement si un ou plusieurs des éléments suivants existent dans le flux de configuration dans la section `<configuration><runtime>` :

- `<gcServer enabled="true"/>` provoque la définition de `STARTUP_SERVER_GC`.

- `<etwEnable enabled="true"/>` provoque la définition de `STARTUP_ETW`.

- `<appDomainResourceMonitoring enabled="true"/>` provoque la définition de `STARTUP_ARM`.

La valeur par défaut `STARTUP_FLAGS` résultante est la combinaison OR au niveau du bit des valeurs qui sont définies à partir de la liste précédente avec les indicateurs de démarrage par défaut.

## <a name="return-value"></a>Valeur renvoyée

Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.

|HRESULT|Description|
|-------------|-----------------|
|S_OK|La commande s'est correctement terminée.|
|E_POINTER|`pwzVersion` n'est pas null et `pcchVersion` est null.<br /><br /> -ou-<br /><br /> `pwzImageVersion` n'est pas null et `pcchImageVersion` est null.|
|E_INVALIDARG|`dwPolicyFlags` ne spécifie pas `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|La mémoire allouée à `pwzVersion` est insuffisante.<br /><br /> -ou-<br /><br /> La mémoire allouée à `pwzImageVersion` est insuffisante.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` comprend METAHOST_POLICY_APPLY_UPGRADE_POLICY et `pwzVersion` et `pcchVersion` sont tous deux null.|

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Metahost. h

**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll

**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICLRMetaHostPolicy, interface](iclrmetahostpolicy-interface.md)
- [Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hosting](index.md)
