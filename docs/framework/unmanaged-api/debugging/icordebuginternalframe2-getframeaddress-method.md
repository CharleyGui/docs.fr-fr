---
title: ICorDebugInternalFrame2::GetFrameAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 05a9ab58acb3bf5829fd231ae6d8bcc96ae06da6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724869"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="00604-102">ICorDebugInternalFrame2::GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="00604-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>

<span data-ttu-id="00604-103">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="00604-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00604-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00604-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00604-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00604-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="00604-106">à Pointeur vers le `CORDB_ADDRESS` pour le frame interne.</span><span class="sxs-lookup"><span data-stu-id="00604-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00604-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="00604-107">Return Value</span></span>  

 <span data-ttu-id="00604-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="00604-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="00604-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00604-109">HRESULT</span></span>|<span data-ttu-id="00604-110">Description</span><span class="sxs-lookup"><span data-stu-id="00604-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00604-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="00604-111">S_OK</span></span>|<span data-ttu-id="00604-112">L’adresse du frame interne a été correctement retournée.</span><span class="sxs-lookup"><span data-stu-id="00604-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="00604-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00604-113">E_FAIL</span></span>|<span data-ttu-id="00604-114">L’adresse du frame interne n’a pas pu être retournée.</span><span class="sxs-lookup"><span data-stu-id="00604-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="00604-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00604-115">E_INVALIDARG</span></span>|<span data-ttu-id="00604-116">`pAddress` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="00604-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00604-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="00604-117">Remarks</span></span>  

 <span data-ttu-id="00604-118">La valeur retournée dans `pAddress` peut être utilisée pour déterminer l’emplacement du frame interne par rapport à d’autres frames sur la pile.</span><span class="sxs-lookup"><span data-stu-id="00604-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="00604-119">Même sur les ordinateurs IA-64, le frame interne se trouve sur la pile uniquement et il n’y a aucun pointeur correspondant vers un magasin de stockage.</span><span class="sxs-lookup"><span data-stu-id="00604-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00604-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00604-120">Requirements</span></span>  

 <span data-ttu-id="00604-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00604-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00604-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00604-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00604-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00604-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00604-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00604-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00604-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00604-125">See also</span></span>

- [<span data-ttu-id="00604-126">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="00604-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="00604-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="00604-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00604-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="00604-128">Debugging</span></span>](index.md)
