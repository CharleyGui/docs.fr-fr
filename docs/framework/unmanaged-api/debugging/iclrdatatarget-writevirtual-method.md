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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0ad4b7e907412aced911d7869ffce81eb867448
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738509"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="cb5ae-102">ICLRDataTarget::WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="cb5ae-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="cb5ae-103">Écrit des données à partir de la mémoire tampon spécifiée à l’adresse de mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cb5ae-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb5ae-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5ae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb5ae-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cb5ae-106">[in] CLRDATA_ADDRESS qui stocke l’adresse de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="cb5ae-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="cb5ae-107">[in] Pointeur vers une mémoire tampon qui stocke les données à écrire.</span><span class="sxs-lookup"><span data-stu-id="cb5ae-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="cb5ae-108">[in] Le nombre d’octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="cb5ae-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="cb5ae-109">[out] Pointeur vers le nombre réel d’octets qui ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="cb5ae-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5ae-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cb5ae-110">Requirements</span></span>  
 <span data-ttu-id="cb5ae-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5ae-112">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cb5ae-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cb5ae-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb5ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5ae-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5ae-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb5ae-115">See also</span></span>

- [<span data-ttu-id="cb5ae-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="cb5ae-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
