---
title: ICLRDataTarget::GetPointerSize, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: 7a274aaec4919b86f32f98e4d8278dc12748fb2b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785480"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="293eb-102">ICLRDataTarget::GetPointerSize, méthode</span><span class="sxs-lookup"><span data-stu-id="293eb-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="293eb-103">Obtient la taille, en octets, du type pointeur utilisé par le processus cible.</span><span class="sxs-lookup"><span data-stu-id="293eb-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="293eb-104">Cette méthode est appelée par les services d’accès aux données common language runtime.</span><span class="sxs-lookup"><span data-stu-id="293eb-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="293eb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="293eb-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="293eb-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="293eb-107">à Pointeur vers une valeur entière qui spécifie la taille, en octets, d’un pointeur sur le processus cible.</span><span class="sxs-lookup"><span data-stu-id="293eb-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="293eb-108">Notes</span><span class="sxs-lookup"><span data-stu-id="293eb-108">Remarks</span></span>  
 <span data-ttu-id="293eb-109">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="293eb-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="293eb-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="293eb-110">Requirements</span></span>  
 <span data-ttu-id="293eb-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="293eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="293eb-112">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="293eb-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="293eb-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="293eb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="293eb-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="293eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293eb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="293eb-115">See also</span></span>

- [<span data-ttu-id="293eb-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="293eb-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
