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
ms.openlocfilehash: 6c98fc93fd659ccfc0ccd42eec7d95382cf342f8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860514"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="4f091-102">ICLRDataTarget::SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="4f091-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="4f091-103">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="4f091-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="4f091-104">Cette méthode est appelée par les services d’accès aux données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4f091-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f091-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f091-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f091-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f091-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4f091-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="4f091-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="4f091-108">dans Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="4f091-108">[in] The index of the location.</span></span> <span data-ttu-id="4f091-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="4f091-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="4f091-110">dans `CLRDATA_ADDRESS` Valeur qui spécifie la valeur à placer dans l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="4f091-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f091-111">Notes </span><span class="sxs-lookup"><span data-stu-id="4f091-111">Remarks</span></span>  
 <span data-ttu-id="4f091-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="4f091-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f091-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f091-113">Requirements</span></span>  
 <span data-ttu-id="4f091-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f091-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f091-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4f091-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4f091-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f091-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f091-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f091-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f091-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f091-118">See also</span></span>

- [<span data-ttu-id="4f091-119">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="4f091-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
