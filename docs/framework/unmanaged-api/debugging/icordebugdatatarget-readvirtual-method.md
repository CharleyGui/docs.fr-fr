---
title: ICorDebugDataTarget::ReadVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 87316b20c5835d9b887355a1f9374fa5f2156e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122169"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="fcfa4-102">ICorDebugDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="fcfa4-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="fcfa4-103">Obtient un bloc de mémoire contiguë commençant à l’adresse spécifiée et le retourne dans la mémoire tampon fournie.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfa4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcfa4-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcfa4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcfa4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="fcfa4-106">dans Adresse de début de la mémoire demandée.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="fcfa4-107">à Mémoire tampon dans laquelle la mémoire sera stockée.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="fcfa4-108">dans Nombre d’octets à récupérer à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="fcfa4-109">à Nombre d’octets lus réellement à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="fcfa4-110">Ce nombre peut être inférieur à `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="fcfa4-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcfa4-111">Notes</span><span class="sxs-lookup"><span data-stu-id="fcfa4-111">Remarks</span></span>  
 <span data-ttu-id="fcfa4-112">Si le premier octet (à l’adresse de début spécifiée) peut être lu, l’appel doit retourner Success (pour prendre en charge la lecture efficace des structures de données avec une longueur autodescriptive, comme les chaînes terminées par le caractère null).</span><span class="sxs-lookup"><span data-stu-id="fcfa4-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfa4-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="fcfa4-113">Requirements</span></span>  
 <span data-ttu-id="fcfa4-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfa4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfa4-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcfa4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcfa4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcfa4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcfa4-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfa4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfa4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcfa4-118">See also</span></span>

- [<span data-ttu-id="fcfa4-119">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="fcfa4-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="fcfa4-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fcfa4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fcfa4-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="fcfa4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
