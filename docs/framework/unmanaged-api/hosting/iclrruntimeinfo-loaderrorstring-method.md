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
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762186"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="0c4e0-102">ICLRRuntimeInfo::LoadErrorString, méthode</span><span class="sxs-lookup"><span data-stu-id="0c4e0-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="0c4e0-103">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="0c4e0-104">Cette méthode remplace les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c4e0-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="0c4e0-105">LoadStringRC,</span><span class="sxs-lookup"><span data-stu-id="0c4e0-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="0c4e0-106">LoadStringRCEx,</span><span class="sxs-lookup"><span data-stu-id="0c4e0-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="0c4e0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c4e0-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c4e0-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c4e0-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="0c4e0-109">dans HRESULT à traduire.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="0c4e0-110">à Chaîne de message associée au HRESULT donné.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="0c4e0-111">[in, out] Taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="0c4e0-112">Si `pwzbuffer` a la valeur null, `pcchBuffer` fournit la taille attendue de `pwzbuffer` pour autoriser la préallocation.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="0c4e0-113">dans Identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-113">[in] The culture identifier.</span></span> <span data-ttu-id="0c4e0-114">Pour utiliser la culture par défaut, vous devez spécifier-1.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c4e0-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0c4e0-115">Return Value</span></span>  
 <span data-ttu-id="0c4e0-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0c4e0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c4e0-117">HRESULT</span></span>|<span data-ttu-id="0c4e0-118">Description</span><span class="sxs-lookup"><span data-stu-id="0c4e0-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c4e0-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c4e0-119">S_OK</span></span>|<span data-ttu-id="0c4e0-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="0c4e0-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0c4e0-121">E_POINTER</span></span>|<span data-ttu-id="0c4e0-122">`pcchBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="0c4e0-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0c4e0-123">E_INVALIDARG</span></span>|<span data-ttu-id="0c4e0-124">`pwzBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="0c4e0-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c4e0-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0c4e0-125">Requirements</span></span>  
 <span data-ttu-id="0c4e0-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c4e0-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c4e0-127">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="0c4e0-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0c4e0-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c4e0-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c4e0-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c4e0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c4e0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c4e0-130">See also</span></span>

- [<span data-ttu-id="0c4e0-131">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="0c4e0-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0c4e0-132">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="0c4e0-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0c4e0-133">Hébergement</span><span class="sxs-lookup"><span data-stu-id="0c4e0-133">Hosting</span></span>](index.md)
