---
title: ICLRDataTarget::ReadVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 0332fae46d6a65cfb7cc0b929cc2fd0d97e1790e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179155"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="be246-102">ICLRDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="be246-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="be246-103">Lit les données de l’adresse mémoire virtuelle spécifiée dans le tampon spécifié.</span><span class="sxs-lookup"><span data-stu-id="be246-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be246-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be246-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be246-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be246-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="be246-106">[dans] Une CLRDATA_ADDRESS qui stocke l’adresse mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="be246-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="be246-107">[out] Un pointeur vers un tampon qui reçoit les données.</span><span class="sxs-lookup"><span data-stu-id="be246-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="be246-108">[dans] La longueur du tampon.</span><span class="sxs-lookup"><span data-stu-id="be246-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="be246-109">[out] Un pointeur sur le nombre d’octets retournés.</span><span class="sxs-lookup"><span data-stu-id="be246-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be246-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="be246-110">Requirements</span></span>  
 <span data-ttu-id="be246-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be246-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be246-112">**En-tête:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="be246-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="be246-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be246-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be246-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be246-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be246-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be246-115">See also</span></span>

- [<span data-ttu-id="be246-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="be246-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
