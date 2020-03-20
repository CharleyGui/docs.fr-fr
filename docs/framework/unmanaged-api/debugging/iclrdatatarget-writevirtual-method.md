---
title: ICLRDataTarget::WriteVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: bd2f67c2d7230d3873b4dc0df73ac1be778a0828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179098"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="4d20c-102">ICLRDataTarget::WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="4d20c-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="4d20c-103">Rédige les données du tampon spécifié à l’adresse de mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4d20c-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d20c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d20c-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d20c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d20c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4d20c-106">[dans] Une CLRDATA_ADDRESS qui stocke l’adresse mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="4d20c-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4d20c-107">[dans] Un pointeur vers un tampon qui stocke les données à écrire.</span><span class="sxs-lookup"><span data-stu-id="4d20c-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="4d20c-108">[dans] Le nombre d’octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="4d20c-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="4d20c-109">[out] Un pointeur sur le nombre réel d’octets qui ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="4d20c-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d20c-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4d20c-110">Requirements</span></span>  
 <span data-ttu-id="4d20c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d20c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d20c-112">**En-tête:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4d20c-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4d20c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d20c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d20c-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d20c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d20c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d20c-115">See also</span></span>

- [<span data-ttu-id="4d20c-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="4d20c-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
