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
ms.openlocfilehash: e285df37d83ff73fe29fe293380a4053cb5a9eea
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860557"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="49497-102">ICLRDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="49497-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="49497-103">Lit les données à partir de l’adresse mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="49497-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49497-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49497-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49497-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49497-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="49497-106">dans CLRDATA_ADDRESS qui stocke l’adresse mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="49497-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="49497-107">à Pointeur vers une mémoire tampon qui reçoit les données.</span><span class="sxs-lookup"><span data-stu-id="49497-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="49497-108">dans Longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="49497-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="49497-109">à Pointeur vers le nombre d’octets retournés.</span><span class="sxs-lookup"><span data-stu-id="49497-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49497-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49497-110">Requirements</span></span>  
 <span data-ttu-id="49497-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49497-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49497-112">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="49497-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="49497-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49497-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49497-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49497-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49497-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49497-115">See also</span></span>

- [<span data-ttu-id="49497-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="49497-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
