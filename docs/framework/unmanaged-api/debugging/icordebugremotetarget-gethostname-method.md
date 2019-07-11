---
title: ICorDebugRemoteTarget::GetHostName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43a502682e6ccfc36931970d0121f91529f51711
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744727"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="e6174-102">ICorDebugRemoteTarget::GetHostName, méthode</span><span class="sxs-lookup"><span data-stu-id="e6174-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="e6174-103">Retourne le nom de domaine complet ou l’adresse IPv4 de l’ordinateur cible de débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e6174-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="e6174-104">IPv6 n’est pas pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="e6174-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6174-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6174-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6174-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6174-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="e6174-107">[in] La taille, en caractères, de la `szHostName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e6174-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="e6174-108">Si ce paramètre est 0 (zéro), `szHostName` doit être null.</span><span class="sxs-lookup"><span data-stu-id="e6174-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="e6174-109">[out] Le nombre de caractères, y compris une marque de fin null, dans le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="e6174-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="e6174-110">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="e6174-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="e6174-111">[out] Mémoire tampon qui contient le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="e6174-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6174-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e6174-112">Return Value</span></span>  
 <span data-ttu-id="e6174-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6174-113">S_OK</span></span>  
 <span data-ttu-id="e6174-114">Le nom d’hôte ou adresse IP a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="e6174-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="e6174-115">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="e6174-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e6174-116">Impossible de retourner le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="e6174-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6174-117">Notes</span><span class="sxs-lookup"><span data-stu-id="e6174-117">Remarks</span></span>  
 <span data-ttu-id="e6174-118">Cette méthode est implémentée par le writer de débogueur.</span><span class="sxs-lookup"><span data-stu-id="e6174-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="e6174-119">Il doit respecter le paradigme d’appel plusieurs : Lors du premier appel, l’appelant transmet null à la fois aux `cchHostName` et `szHostName`, et `pcchHostName` retourne la taille de la mémoire tampon requise.</span><span class="sxs-lookup"><span data-stu-id="e6174-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="e6174-120">Sur le deuxième appel, la taille qui a été retournée précédemment est passée dans `cchHostName`, et une taille de tampon appropriée est transmis en `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="e6174-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6174-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e6174-121">Requirements</span></span>  
 <span data-ttu-id="e6174-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6174-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6174-123">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e6174-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e6174-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6174-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6174-125">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e6174-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6174-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6174-126">See also</span></span>

- [<span data-ttu-id="e6174-127">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e6174-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="e6174-128">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="e6174-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
