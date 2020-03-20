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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179113"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="ffaff-102">ICLRDataTarget::Request, méthode</span><span class="sxs-lookup"><span data-stu-id="ffaff-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="ffaff-103">Appelés par les services d’accès aux données de l’heure courante (CLR) pour demander une opération, tel que défini par la mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="ffaff-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffaff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffaff-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ffaff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffaff-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="ffaff-106">[dans] Défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ffaff-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="ffaff-107">[dans] La taille du tampon d’entrée, qui est utilisé pour la demande entrante.</span><span class="sxs-lookup"><span data-stu-id="ffaff-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="ffaff-108">[dans] Un tampon contenant la demande.</span><span class="sxs-lookup"><span data-stu-id="ffaff-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="ffaff-109">[dans] La taille du tampon de sortie, qui est utilisé pour la réponse.</span><span class="sxs-lookup"><span data-stu-id="ffaff-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="ffaff-110">[out] Un tampon contenant la réponse.</span><span class="sxs-lookup"><span data-stu-id="ffaff-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffaff-111">Notes </span><span class="sxs-lookup"><span data-stu-id="ffaff-111">Remarks</span></span>  
 <span data-ttu-id="ffaff-112">La `Request` méthode facilite l’ajout d’opérations personnalisées non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ffaff-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="ffaff-113">C’est-à-dire que cette méthode fournit l’extéponsabilité sans nécessiter la révision de la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="ffaff-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="ffaff-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="ffaff-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffaff-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ffaff-115">Requirements</span></span>  
 <span data-ttu-id="ffaff-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffaff-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffaff-117">**En-tête:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ffaff-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ffaff-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffaff-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffaff-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffaff-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffaff-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffaff-120">See also</span></span>

- [<span data-ttu-id="ffaff-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="ffaff-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
