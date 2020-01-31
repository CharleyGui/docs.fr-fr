---
title: ICLRDataTarget::SetTLSValue, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793692"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="9f085-102">ICLRDataTarget::SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="9f085-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="9f085-103">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="9f085-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="9f085-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9f085-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f085-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f085-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f085-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9f085-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="9f085-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="9f085-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="9f085-108">dans Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="9f085-108">[in] The index of the location.</span></span> <span data-ttu-id="9f085-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f085-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="9f085-110">dans Valeur `CLRDATA_ADDRESS` qui spécifie la valeur à placer dans l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="9f085-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f085-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9f085-111">Remarks</span></span>  
 <span data-ttu-id="9f085-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="9f085-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f085-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9f085-113">Requirements</span></span>  
 <span data-ttu-id="9f085-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f085-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f085-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9f085-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9f085-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f085-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f085-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f085-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f085-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f085-118">See also</span></span>

- [<span data-ttu-id="9f085-119">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="9f085-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
