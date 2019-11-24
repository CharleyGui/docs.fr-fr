---
title: ISymUnmanagedMethod::GetSourceStartEnd, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 01ab69b73a7bc4929e2ebd49b3847f8d7c4646a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448866"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="ef329-102">ISymUnmanagedMethod::GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="ef329-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="ef329-103">Gets the start and end document positions for the source of this method.</span><span class="sxs-lookup"><span data-stu-id="ef329-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="ef329-104">The first array position is the start, and the second array position is the end.</span><span class="sxs-lookup"><span data-stu-id="ef329-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef329-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef329-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef329-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef329-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="ef329-107">[in] The starting and ending source documents.</span><span class="sxs-lookup"><span data-stu-id="ef329-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="ef329-108">[in] The starting and ending lines in the corresponding source documents.</span><span class="sxs-lookup"><span data-stu-id="ef329-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="ef329-109">[in] The starting and ending columns in the corresponding source documents.</span><span class="sxs-lookup"><span data-stu-id="ef329-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ef329-110">[out] `true` if positions were defined; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="ef329-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef329-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ef329-111">Return Value</span></span>  
 <span data-ttu-id="ef329-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="ef329-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef329-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="ef329-113">Requirements</span></span>  
 <span data-ttu-id="ef329-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef329-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef329-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef329-115">See also</span></span>

- [<span data-ttu-id="ef329-116">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="ef329-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
