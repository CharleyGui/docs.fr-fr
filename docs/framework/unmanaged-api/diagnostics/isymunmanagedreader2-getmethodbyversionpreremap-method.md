---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: 2063856389b122b150a2d2744169a4a567592287
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446453"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="5e8b3-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="5e8b3-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="5e8b3-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="5e8b3-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e8b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e8b3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e8b3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e8b3-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="5e8b3-107">[in] The method metadata token.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="5e8b3-108">[in] The method version.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5e8b3-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e8b3-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5e8b3-110">Return Value</span></span>  
 <span data-ttu-id="5e8b3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e8b3-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="5e8b3-112">Requirements</span></span>  
 <span data-ttu-id="5e8b3-113">**Header:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="5e8b3-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="5e8b3-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e8b3-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8b3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e8b3-115">See also</span></span>

- [<span data-ttu-id="5e8b3-116">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="5e8b3-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
