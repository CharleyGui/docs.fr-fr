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
ms.openlocfilehash: 8fb0cfc72867653eaff65f3183dacf9191604290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679726"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="e5961-102">ICorDebugDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="e5961-102">ICorDebugDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="e5961-103">Obtient un bloc de mémoire contiguë commençant à l’adresse spécifiée et le retourne dans la mémoire tampon fournie.</span><span class="sxs-lookup"><span data-stu-id="e5961-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5961-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5961-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5961-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5961-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e5961-106">dans Adresse de début de la mémoire demandée.</span><span class="sxs-lookup"><span data-stu-id="e5961-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="e5961-107">à Mémoire tampon dans laquelle la mémoire sera stockée.</span><span class="sxs-lookup"><span data-stu-id="e5961-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="e5961-108">dans Nombre d’octets à récupérer à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="e5961-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="e5961-109">à Nombre d’octets lus réellement à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="e5961-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="e5961-110">Ce nombre peut être inférieur à `bytesRequested` .</span><span class="sxs-lookup"><span data-stu-id="e5961-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5961-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5961-111">Remarks</span></span>  

 <span data-ttu-id="e5961-112">Si le premier octet (à l’adresse de début spécifiée) peut être lu, l’appel doit retourner Success (pour prendre en charge la lecture efficace des structures de données avec une longueur autodescriptive, comme les chaînes terminées par le caractère null).</span><span class="sxs-lookup"><span data-stu-id="e5961-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5961-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5961-113">Requirements</span></span>  

 <span data-ttu-id="e5961-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5961-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5961-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5961-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5961-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5961-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5961-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5961-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5961-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5961-118">See also</span></span>

- [<span data-ttu-id="e5961-119">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e5961-119">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="e5961-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e5961-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e5961-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="e5961-121">Debugging</span></span>](index.md)
