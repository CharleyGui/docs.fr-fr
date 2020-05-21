---
title: ICLRRuntimeInfo::IsStarted, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762199"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="b46d8-102">ICLRRuntimeInfo::IsStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="b46d8-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="b46d8-103">Indique si le runtime a été démarré (c’est-à-dire, si la [méthode ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) a été appelée et a réussi).</span><span class="sxs-lookup"><span data-stu-id="b46d8-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b46d8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b46d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b46d8-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="b46d8-106">[out] `true` Si ce Runtime est démarré ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="b46d8-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="b46d8-107">à Retourne les indicateurs utilisés pour démarrer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b46d8-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b46d8-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b46d8-108">Return Value</span></span>  
 <span data-ttu-id="b46d8-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b46d8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b46d8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b46d8-110">HRESULT</span></span>|<span data-ttu-id="b46d8-111">Description</span><span class="sxs-lookup"><span data-stu-id="b46d8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b46d8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b46d8-112">S_OK</span></span>|<span data-ttu-id="b46d8-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="b46d8-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b46d8-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b46d8-114">E_NOTIMPL</span></span>|<span data-ttu-id="b46d8-115">La version du common language runtime (CLR) est antérieure à la version CLR du .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b46d8-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b46d8-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b46d8-116">Remarks</span></span>  
 <span data-ttu-id="b46d8-117">Cette méthode ne fonctionne pas avec les versions CLR antérieures à la version CLR du .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b46d8-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46d8-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b46d8-118">Requirements</span></span>  
 <span data-ttu-id="b46d8-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46d8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46d8-120">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="b46d8-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b46d8-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b46d8-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b46d8-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46d8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b46d8-123">See also</span></span>

- [<span data-ttu-id="b46d8-124">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="b46d8-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b46d8-125">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="b46d8-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b46d8-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="b46d8-126">Hosting</span></span>](index.md)
