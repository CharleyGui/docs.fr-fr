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
ms.openlocfilehash: b913affb4728dc80ba67438384cbeac87265f76d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860540"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="42c3a-102">ICLRDataTarget::Request, méthode</span><span class="sxs-lookup"><span data-stu-id="42c3a-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="42c3a-103">Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="42c3a-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c3a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="42c3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42c3a-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="42c3a-106">dans Défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42c3a-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="42c3a-107">dans Taille de la mémoire tampon d’entrée utilisée pour la demande entrante.</span><span class="sxs-lookup"><span data-stu-id="42c3a-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="42c3a-108">dans Mémoire tampon contenant la demande.</span><span class="sxs-lookup"><span data-stu-id="42c3a-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="42c3a-109">dans Taille de la mémoire tampon de sortie, qui est utilisée pour la réponse.</span><span class="sxs-lookup"><span data-stu-id="42c3a-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="42c3a-110">à Mémoire tampon contenant la réponse.</span><span class="sxs-lookup"><span data-stu-id="42c3a-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c3a-111">Notes </span><span class="sxs-lookup"><span data-stu-id="42c3a-111">Remarks</span></span>  
 <span data-ttu-id="42c3a-112">La `Request` méthode facilite l’ajout d’opérations personnalisées non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="42c3a-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="42c3a-113">Autrement dit, cette méthode fournit l’extensibilité sans nécessiter de révision de la définition de l’interface.</span><span class="sxs-lookup"><span data-stu-id="42c3a-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="42c3a-114">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="42c3a-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c3a-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42c3a-115">Requirements</span></span>  
 <span data-ttu-id="42c3a-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c3a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c3a-117">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="42c3a-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="42c3a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42c3a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42c3a-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c3a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c3a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42c3a-120">See also</span></span>

- [<span data-ttu-id="42c3a-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="42c3a-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
