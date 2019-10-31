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
ms.openlocfilehash: 1425d48bb18d4161a1c96239b76b8315ae258705
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112778"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="b6f7a-102">ICLRDataTarget::SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b6f7a-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="b6f7a-103">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="b6f7a-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b6f7a-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f7a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6f7a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6f7a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6f7a-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b6f7a-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="b6f7a-108">dans Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-108">[in] The index of the location.</span></span> <span data-ttu-id="b6f7a-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="b6f7a-110">dans Valeur `CLRDATA_ADDRESS` qui spécifie la valeur à placer dans l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6f7a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="b6f7a-111">Remarks</span></span>  
 <span data-ttu-id="b6f7a-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6f7a-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f7a-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="b6f7a-113">Requirements</span></span>  
 <span data-ttu-id="b6f7a-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f7a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f7a-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b6f7a-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b6f7a-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6f7a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6f7a-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f7a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f7a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6f7a-118">See also</span></span>

- [<span data-ttu-id="b6f7a-119">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="b6f7a-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
