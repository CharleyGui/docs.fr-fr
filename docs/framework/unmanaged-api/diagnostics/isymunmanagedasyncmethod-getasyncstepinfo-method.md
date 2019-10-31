---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: 5d3ee0d42773b70c8301260e5b4d6af1c7ceb938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139855"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="272d5-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="272d5-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="272d5-103">Consultez [méthode defineasyncstepinfo,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="272d5-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="272d5-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="272d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="272d5-105">Parameters</span></span>  
  
|<span data-ttu-id="272d5-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="272d5-106">Parameter</span></span>|<span data-ttu-id="272d5-107">Description</span><span class="sxs-lookup"><span data-stu-id="272d5-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="272d5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="272d5-108">Return Value</span></span>  
 <span data-ttu-id="272d5-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="272d5-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="272d5-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="272d5-110">Requirements</span></span>  
 <span data-ttu-id="272d5-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="272d5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272d5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="272d5-112">See also</span></span>

- [<span data-ttu-id="272d5-113">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="272d5-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
