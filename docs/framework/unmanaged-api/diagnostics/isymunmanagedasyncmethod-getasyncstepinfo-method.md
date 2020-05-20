---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: e3c0d7b8eeded403ce8391cff00ee18dccc38ed5
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441888"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="4bd3a-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="4bd3a-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="4bd3a-103">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4bd3a-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd3a-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bd3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4bd3a-105">Parameters</span></span>  
  
|<span data-ttu-id="4bd3a-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4bd3a-106">Parameter</span></span>|<span data-ttu-id="4bd3a-107">Description</span><span class="sxs-lookup"><span data-stu-id="4bd3a-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4bd3a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4bd3a-108">Return Value</span></span>  
 <span data-ttu-id="4bd3a-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4bd3a-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd3a-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="4bd3a-110">Requirements</span></span>  
 <span data-ttu-id="4bd3a-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4bd3a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd3a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd3a-112">See also</span></span>

- [<span data-ttu-id="4bd3a-113">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="4bd3a-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
