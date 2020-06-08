---
title: ICLRRuntimeInfo::GetInterface, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 9cf9d48bf50ffc1fc56270c13215acfef6d9c3af
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504054"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="9da6b-102">ICLRRuntimeInfo::GetInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="9da6b-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="9da6b-103">Charge le CLR dans le processus en cours et retourne des pointeurs d’interface de Runtime, tels que [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md)et [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9da6b-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="9da6b-104">Cette méthode remplace toutes les `CorBindTo` fonctions \* dans la section [fonctions d’hébergement CLR déconseillées](deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="9da6b-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da6b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9da6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9da6b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9da6b-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="9da6b-107">dans Interface CLSID de la coclasse.</span><span class="sxs-lookup"><span data-stu-id="9da6b-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="9da6b-108">dans IID de l’interface demandée `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="9da6b-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="9da6b-109">à Pointeur vers l’interface interrogée.</span><span class="sxs-lookup"><span data-stu-id="9da6b-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9da6b-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9da6b-110">Return Value</span></span>  
 <span data-ttu-id="9da6b-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9da6b-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9da6b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9da6b-112">HRESULT</span></span>|<span data-ttu-id="9da6b-113">Description</span><span class="sxs-lookup"><span data-stu-id="9da6b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9da6b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9da6b-114">S_OK</span></span>|<span data-ttu-id="9da6b-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="9da6b-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="9da6b-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9da6b-116">E_POINTER</span></span>|<span data-ttu-id="9da6b-117">`ppUnk` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="9da6b-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="9da6b-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9da6b-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9da6b-119">Mémoire disponible insuffisante pour traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="9da6b-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="9da6b-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="9da6b-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="9da6b-121">Un Runtime différent était déjà lié à la stratégie d’activation héritée du CLR version 2.</span><span class="sxs-lookup"><span data-stu-id="9da6b-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9da6b-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="9da6b-122">Remarks</span></span>  
 <span data-ttu-id="9da6b-123">Cette méthode provoque le chargement du CLR mais pas son initialisation.</span><span class="sxs-lookup"><span data-stu-id="9da6b-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="9da6b-124">Le tableau suivant indique les combinaisons prises en charge pour `rclsid` et `riid` .</span><span class="sxs-lookup"><span data-stu-id="9da6b-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="9da6b-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="9da6b-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="9da6b-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9da6b-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="9da6b-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="9da6b-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="9da6b-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9da6b-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="9da6b-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9da6b-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="9da6b-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9da6b-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="9da6b-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9da6b-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="9da6b-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9da6b-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="9da6b-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="9da6b-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="9da6b-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="9da6b-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="9da6b-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="9da6b-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="9da6b-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9da6b-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="9da6b-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9da6b-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="9da6b-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9da6b-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9da6b-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9da6b-139">Requirements</span></span>  
 <span data-ttu-id="9da6b-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9da6b-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9da6b-141">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="9da6b-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9da6b-142">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9da6b-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9da6b-143">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da6b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da6b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9da6b-144">See also</span></span>

- [<span data-ttu-id="9da6b-145">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="9da6b-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9da6b-146">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="9da6b-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9da6b-147">Hosting</span><span class="sxs-lookup"><span data-stu-id="9da6b-147">Hosting</span></span>](index.md)
