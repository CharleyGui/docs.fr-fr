---
title: ICLRMetaHost::EnumerateLoadedRuntimes, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504171"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="26b8c-102">ICLRMetaHost::EnumerateLoadedRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="26b8c-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="26b8c-103">Retourne une énumération qui comprend un pointeur d’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) valide pour chaque version du Common Language Runtime (CLR) qui est chargé dans un processus donné.</span><span class="sxs-lookup"><span data-stu-id="26b8c-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="26b8c-104">Cette méthode remplace la fonction [GetVersionFromProcess](getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="26b8c-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26b8c-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26b8c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26b8c-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="26b8c-107">dans Handle du processus à examiner pour les runtimes chargés.</span><span class="sxs-lookup"><span data-stu-id="26b8c-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="26b8c-108">à <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>Énumération d’interfaces [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondant à chaque CLR chargé par le processus.</span><span class="sxs-lookup"><span data-stu-id="26b8c-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26b8c-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="26b8c-109">Return Value</span></span>  
 <span data-ttu-id="26b8c-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="26b8c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26b8c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26b8c-111">HRESULT</span></span>|<span data-ttu-id="26b8c-112">Description</span><span class="sxs-lookup"><span data-stu-id="26b8c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26b8c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="26b8c-113">S_OK</span></span>|<span data-ttu-id="26b8c-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="26b8c-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="26b8c-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="26b8c-115">E_POINTER</span></span>|<span data-ttu-id="26b8c-116">`ppEnumerator` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="26b8c-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26b8c-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="26b8c-117">Remarks</span></span>  
 <span data-ttu-id="26b8c-118">Cette méthode répertorie tous les runtimes chargés, même s’ils ont été chargés avec des fonctions déconseillées telles que [CorBindToRuntime](corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="26b8c-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b8c-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26b8c-119">Requirements</span></span>  
 <span data-ttu-id="26b8c-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b8c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b8c-121">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="26b8c-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="26b8c-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26b8c-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26b8c-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b8c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b8c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26b8c-124">See also</span></span>

- [<span data-ttu-id="26b8c-125">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="26b8c-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="26b8c-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="26b8c-126">Hosting</span></span>](index.md)
