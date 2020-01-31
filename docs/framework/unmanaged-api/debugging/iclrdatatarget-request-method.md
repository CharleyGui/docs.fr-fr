---
title: ICLRDataTarget::Request, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793703"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="af277-102">ICLRDataTarget::Request, méthode</span><span class="sxs-lookup"><span data-stu-id="af277-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="af277-103">Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="af277-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af277-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af277-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="af277-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="af277-106">dans Défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af277-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="af277-107">dans Taille de la mémoire tampon d’entrée utilisée pour la demande entrante.</span><span class="sxs-lookup"><span data-stu-id="af277-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="af277-108">dans Mémoire tampon contenant la demande.</span><span class="sxs-lookup"><span data-stu-id="af277-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="af277-109">dans Taille de la mémoire tampon de sortie, qui est utilisée pour la réponse.</span><span class="sxs-lookup"><span data-stu-id="af277-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="af277-110">à Mémoire tampon contenant la réponse.</span><span class="sxs-lookup"><span data-stu-id="af277-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af277-111">Notes</span><span class="sxs-lookup"><span data-stu-id="af277-111">Remarks</span></span>  
 <span data-ttu-id="af277-112">La méthode `Request` facilite l’ajout d’opérations personnalisées non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="af277-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="af277-113">Autrement dit, cette méthode fournit l’extensibilité sans nécessiter de révision de la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="af277-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="af277-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="af277-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af277-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="af277-115">Requirements</span></span>  
 <span data-ttu-id="af277-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af277-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af277-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="af277-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="af277-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af277-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af277-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af277-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af277-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af277-120">See also</span></span>

- [<span data-ttu-id="af277-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="af277-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
