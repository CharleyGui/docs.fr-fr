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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7de415b998ef97e7500c289a1bca4402d203b152
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738691"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="3dce6-102">ICLRDataTarget::GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="3dce6-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="3dce6-103">Obtient une valeur à partir du stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="3dce6-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="3dce6-104">Cette méthode est appelée par les services d’accès de données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3dce6-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dce6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dce6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dce6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3dce6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="3dce6-107">[in] L’identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="3dce6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="3dce6-108">[in] Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="3dce6-108">[in] The index of the location.</span></span> <span data-ttu-id="3dce6-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="3dce6-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="3dce6-110">[out] Un pointeur vers un `CLRDATA_ADDRESS` valeur qui spécifie la valeur retournée à partir de l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="3dce6-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dce6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="3dce6-111">Remarks</span></span>  
 <span data-ttu-id="3dce6-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="3dce6-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dce6-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3dce6-113">Requirements</span></span>  
 <span data-ttu-id="3dce6-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dce6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dce6-115">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3dce6-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3dce6-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dce6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dce6-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dce6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dce6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dce6-118">See also</span></span>

- [<span data-ttu-id="3dce6-119">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="3dce6-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
