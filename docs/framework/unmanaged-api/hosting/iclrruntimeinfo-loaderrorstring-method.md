---
title: ICLRRuntimeInfo::LoadErrorString, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd7bdcf891146a15953b7466e0f6dc680495bd5a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585057"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="f2661-102">ICLRRuntimeInfo::LoadErrorString, méthode</span><span class="sxs-lookup"><span data-stu-id="f2661-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="f2661-103">Traduit une valeur HRESULT dans un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2661-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="f2661-104">Cette méthode remplace les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2661-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="f2661-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="f2661-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="f2661-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="f2661-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="f2661-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2661-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2661-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2661-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="f2661-109">[in] HRESULT à traduire.</span><span class="sxs-lookup"><span data-stu-id="f2661-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f2661-110">[out] La chaîne de message associée à la valeur HRESULT donné.</span><span class="sxs-lookup"><span data-stu-id="f2661-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="f2661-111">[in, out] La taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f2661-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="f2661-112">Si `pwzbuffer` a la valeur null, `pcchBuffer` fournit la taille attendue de `pwzbuffer` pour autoriser la pré-allocation.</span><span class="sxs-lookup"><span data-stu-id="f2661-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="f2661-113">[in] L’identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="f2661-113">[in] The culture identifier.</span></span> <span data-ttu-id="f2661-114">Pour utiliser la culture par défaut, vous devez spécifier -1.</span><span class="sxs-lookup"><span data-stu-id="f2661-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2661-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f2661-115">Return Value</span></span>  
 <span data-ttu-id="f2661-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f2661-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f2661-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2661-117">HRESULT</span></span>|<span data-ttu-id="f2661-118">Description</span><span class="sxs-lookup"><span data-stu-id="f2661-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2661-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2661-119">S_OK</span></span>|<span data-ttu-id="f2661-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f2661-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="f2661-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f2661-121">E_POINTER</span></span>|<span data-ttu-id="f2661-122">`pcchBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="f2661-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="f2661-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f2661-123">E_INVALIDARG</span></span>|<span data-ttu-id="f2661-124">`pwzBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="f2661-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2661-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2661-125">Requirements</span></span>  
 <span data-ttu-id="f2661-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2661-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2661-127">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f2661-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f2661-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2661-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2661-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2661-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2661-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2661-130">See also</span></span>

- [<span data-ttu-id="f2661-131">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f2661-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f2661-132">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f2661-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f2661-133">Hébergement</span><span class="sxs-lookup"><span data-stu-id="f2661-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
