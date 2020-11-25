---
title: CLRCreateInstance, fonction
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 3c7a14f828e55310435a99693c1195f2f0dd40c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711674"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="74f1a-102">CLRCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="74f1a-102">CLRCreateInstance Function</span></span>

<span data-ttu-id="74f1a-103">Fournit l’une des trois interfaces suivantes : [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)ou [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="74f1a-103">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74f1a-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74f1a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74f1a-105">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="74f1a-106">dans Un des trois identificateurs de classe : CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="74f1a-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="74f1a-107">dans Un des trois identificateurs d’interface (IID) : IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="74f1a-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="74f1a-108">à Une des trois interfaces : [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)ou [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="74f1a-108">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74f1a-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="74f1a-109">Return Value</span></span>  

 <span data-ttu-id="74f1a-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="74f1a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="74f1a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74f1a-111">HRESULT</span></span>|<span data-ttu-id="74f1a-112">Description</span><span class="sxs-lookup"><span data-stu-id="74f1a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74f1a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="74f1a-113">S_OK</span></span>|<span data-ttu-id="74f1a-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="74f1a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="74f1a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="74f1a-115">E_POINTER</span></span>|<span data-ttu-id="74f1a-116">`ppInterface` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="74f1a-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74f1a-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="74f1a-117">Remarks</span></span>  

 <span data-ttu-id="74f1a-118">Le tableau suivant indique les combinaisons prises en charge pour `clsid` et `riid` .</span><span class="sxs-lookup"><span data-stu-id="74f1a-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="74f1a-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="74f1a-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="74f1a-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="74f1a-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="74f1a-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="74f1a-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="74f1a-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="74f1a-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="74f1a-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="74f1a-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="74f1a-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="74f1a-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="74f1a-125">Le code suivant montre comment utiliser `CLRCreateInstance` pour récupérer les trois interfaces :</span><span class="sxs-lookup"><span data-stu-id="74f1a-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="74f1a-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74f1a-126">Requirements</span></span>  

 <span data-ttu-id="74f1a-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f1a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f1a-128">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="74f1a-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="74f1a-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74f1a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74f1a-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f1a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f1a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74f1a-131">See also</span></span>

- [<span data-ttu-id="74f1a-132">Hébergement</span><span class="sxs-lookup"><span data-stu-id="74f1a-132">Hosting</span></span>](index.md)
