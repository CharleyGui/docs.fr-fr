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
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="8ef68-102">ICLRMetaHostPolicy::GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="8ef68-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="8ef68-103">Fournit une interface pour une version préférée du Common Language Runtime (CLR) basée sur une stratégie d'hébergement, un assembly managé, une chaîne de version et un flux de configuration.</span><span class="sxs-lookup"><span data-stu-id="8ef68-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="8ef68-104">Cette méthode ne charge pas ou n’active pas le CLR, mais retourne simplement l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui représente le résultat de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ef68-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="8ef68-105">Cette méthode remplace les méthodes [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)et [GetCORRequiredVersion,](getcorrequiredversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8ef68-105">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ef68-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef68-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="8ef68-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ef68-107">Parameters</span></span>

|<span data-ttu-id="8ef68-108">Nom</span><span class="sxs-lookup"><span data-stu-id="8ef68-108">Name</span></span>|<span data-ttu-id="8ef68-109">Description</span><span class="sxs-lookup"><span data-stu-id="8ef68-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="8ef68-110">[in] Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ef68-110">[in] Required.</span></span> <span data-ttu-id="8ef68-111">Spécifie un membre de l’énumération [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , représentant une stratégie de liaison et un nombre quelconque de modificateurs.</span><span class="sxs-lookup"><span data-stu-id="8ef68-111">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="8ef68-112">La seule stratégie actuellement disponible est [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8ef68-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="8ef68-113">Les modificateurs incluent [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)et [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8ef68-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="8ef68-114">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-114">[in] Optional.</span></span> <span data-ttu-id="8ef68-115">Spécifie le chemin d’accès de fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="8ef68-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="8ef68-116">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-116">[in] Optional.</span></span> <span data-ttu-id="8ef68-117">Spécifie le fichier de configuration en tant que <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ef68-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="8ef68-118">[in, out] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-118">[in, out] Optional.</span></span> <span data-ttu-id="8ef68-119">Spécifie ou retourne la version du CLR par défaut à charger.</span><span class="sxs-lookup"><span data-stu-id="8ef68-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="8ef68-120">[in, out] Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ef68-120">[in, out] Required.</span></span> <span data-ttu-id="8ef68-121">Spécifie la taille attendue de `pwzVersion` comme entrée, pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8ef68-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="8ef68-122">Si `pwzVersion` a la valeur null, `pcchVersion` contient la taille attendue de `pwzVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation ; sinon, `pcchVersion` contient le nombre de caractères écrits dans `pwzVersion`.</span><span class="sxs-lookup"><span data-stu-id="8ef68-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="8ef68-123">[out] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-123">[out] Optional.</span></span> <span data-ttu-id="8ef68-124">Quand `GetRequestedRuntime` retourne la valeur, contient la version du CLR correspondant à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui est retournée.</span><span class="sxs-lookup"><span data-stu-id="8ef68-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="8ef68-125">[in, out] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-125">[in, out] Optional.</span></span> <span data-ttu-id="8ef68-126">Spécifie la taille de `pwzImageVersion` comme entrée pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8ef68-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="8ef68-127">Si `pwzImageVersion` a la valeur null, `pcchImageVersion` contient la taille requise de `pwzImageVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation.</span><span class="sxs-lookup"><span data-stu-id="8ef68-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="8ef68-128">[out] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8ef68-128">[out] Optional.</span></span> <span data-ttu-id="8ef68-129">Si `GetRequestedRuntime` utilise un fichier de configuration pendant le processus de liaison, quand il retourne, `pdwConfigFlags` contient une valeur [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) qui indique si l' [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) élément a l' `useLegacyV2RuntimeActivationPolicy` attribut défini et la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="8ef68-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="8ef68-130">Appliquez le masque [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) à `pdwConfigFlags` pour récupérer les valeurs correspondantes à `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="8ef68-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="8ef68-131">dans Spécifie l’identificateur d’interface IID_ICLRRuntimeInfo pour l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) demandée.</span><span class="sxs-lookup"><span data-stu-id="8ef68-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="8ef68-132">à Quand `GetRequestedRuntime` retourne une valeur, contient un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondante.</span><span class="sxs-lookup"><span data-stu-id="8ef68-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ef68-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ef68-133">Remarks</span></span>

<span data-ttu-id="8ef68-134">Quand cette méthode réussit, elle a comme effet secondaire de combiner des indicateurs supplémentaires avec les indicateurs de démarrage par défaut actuels de l'interface d'exécution retournée, si et seulement si un ou plusieurs des éléments suivants existent dans le flux de configuration dans la section `<configuration><runtime>` :</span><span class="sxs-lookup"><span data-stu-id="8ef68-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="8ef68-135">`<gcServer enabled="true"/>` provoque la définition de `STARTUP_SERVER_GC`.</span><span class="sxs-lookup"><span data-stu-id="8ef68-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="8ef68-136">`<etwEnable enabled="true"/>` provoque la définition de `STARTUP_ETW`.</span><span class="sxs-lookup"><span data-stu-id="8ef68-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="8ef68-137">`<appDomainResourceMonitoring enabled="true"/>` provoque la définition de `STARTUP_ARM`.</span><span class="sxs-lookup"><span data-stu-id="8ef68-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="8ef68-138">La valeur par défaut `STARTUP_FLAGS` résultante est la combinaison OR au niveau du bit des valeurs qui sont définies à partir de la liste précédente avec les indicateurs de démarrage par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ef68-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ef68-139">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8ef68-139">Return Value</span></span>

<span data-ttu-id="8ef68-140">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8ef68-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="8ef68-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ef68-141">HRESULT</span></span>|<span data-ttu-id="8ef68-142">Description</span><span class="sxs-lookup"><span data-stu-id="8ef68-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="8ef68-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ef68-143">S_OK</span></span>|<span data-ttu-id="8ef68-144">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="8ef68-144">The method completed successfully.</span></span>|
|<span data-ttu-id="8ef68-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8ef68-145">E_POINTER</span></span>|<span data-ttu-id="8ef68-146">`pwzVersion` n'est pas null et `pcchVersion` est null.</span><span class="sxs-lookup"><span data-stu-id="8ef68-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="8ef68-147">-ou-</span><span class="sxs-lookup"><span data-stu-id="8ef68-147">-or-</span></span><br /><br /> <span data-ttu-id="8ef68-148">`pwzImageVersion` n'est pas null et `pcchImageVersion` est null.</span><span class="sxs-lookup"><span data-stu-id="8ef68-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="8ef68-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8ef68-149">E_INVALIDARG</span></span>|<span data-ttu-id="8ef68-150">`dwPolicyFlags` ne spécifie pas `METAHOST_POLICY_HIGHCOMPAT`.</span><span class="sxs-lookup"><span data-stu-id="8ef68-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="8ef68-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8ef68-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8ef68-152">La mémoire allouée à `pwzVersion` est insuffisante.</span><span class="sxs-lookup"><span data-stu-id="8ef68-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="8ef68-153">-ou-</span><span class="sxs-lookup"><span data-stu-id="8ef68-153">-or-</span></span><br /><br /> <span data-ttu-id="8ef68-154">La mémoire allouée à `pwzImageVersion` est insuffisante.</span><span class="sxs-lookup"><span data-stu-id="8ef68-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="8ef68-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="8ef68-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="8ef68-156">`dwPolicyFlags` comprend METAHOST_POLICY_APPLY_UPGRADE_POLICY et `pwzVersion` et `pcchVersion` sont tous deux null.</span><span class="sxs-lookup"><span data-stu-id="8ef68-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="8ef68-157">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ef68-157">Requirements</span></span>

<span data-ttu-id="8ef68-158">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef68-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8ef68-159">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="8ef68-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="8ef68-160">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ef68-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="8ef68-161">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef68-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8ef68-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ef68-162">See also</span></span>

- [<span data-ttu-id="8ef68-163">ICLRMetaHostPolicy, interface</span><span class="sxs-lookup"><span data-stu-id="8ef68-163">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="8ef68-164">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="8ef68-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="8ef68-165">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="8ef68-165">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="8ef68-166">Hosting</span><span class="sxs-lookup"><span data-stu-id="8ef68-166">Hosting</span></span>](index.md)
