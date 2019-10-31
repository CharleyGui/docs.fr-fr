---
title: ICLRDataTarget::GetTLSValue, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: 205ad3af81fb6fabda5cbe291536f8858999f831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113703"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="90119-102">ICLRDataTarget::GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="90119-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="90119-103">Obtient une valeur à partir du stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="90119-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="90119-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="90119-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90119-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90119-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90119-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90119-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="90119-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="90119-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="90119-108">dans Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="90119-108">[in] The index of the location.</span></span> <span data-ttu-id="90119-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="90119-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="90119-110">à Pointeur vers une valeur `CLRDATA_ADDRESS` qui spécifie la valeur retournée à partir de l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="90119-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90119-111">Notes</span><span class="sxs-lookup"><span data-stu-id="90119-111">Remarks</span></span>  
 <span data-ttu-id="90119-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="90119-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90119-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="90119-113">Requirements</span></span>  
 <span data-ttu-id="90119-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90119-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90119-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="90119-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="90119-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90119-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90119-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90119-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90119-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90119-118">See also</span></span>

- [<span data-ttu-id="90119-119">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="90119-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
