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
ms.openlocfilehash: 4382d3c9f69df2808f8cd0aaf7f8eaf19bc9891e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793674"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="ce9a1-102">ICLRDataTarget::WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="ce9a1-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="ce9a1-103">Écrit des données à partir de la mémoire tampon spécifiée dans l’adresse mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ce9a1-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce9a1-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9a1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="ce9a1-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ce9a1-106">dans CLRDATA_ADDRESS qui stocke l’adresse mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ce9a1-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ce9a1-107">dans Pointeur vers une mémoire tampon qui stocke les données à écrire.</span><span class="sxs-lookup"><span data-stu-id="ce9a1-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="ce9a1-108">dans Nombre d’octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="ce9a1-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="ce9a1-109">à Pointeur vers le nombre réel d’octets qui ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="ce9a1-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9a1-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ce9a1-110">Requirements</span></span>  
 <span data-ttu-id="ce9a1-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9a1-112">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ce9a1-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ce9a1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce9a1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce9a1-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9a1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce9a1-115">See also</span></span>

- [<span data-ttu-id="ce9a1-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="ce9a1-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
