---
title: ISymUnmanagedMethod::GetOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: f7993ebc15f95df97a9b45523717f318d8c435ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448949"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="0cfc2-102">ISymUnmanagedMethod::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0cfc2-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="0cfc2-103">Returns the offset within this method that corresponds to a given position within a document.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cfc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cfc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cfc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0cfc2-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="0cfc2-106">[in] A pointer to the document for which the offset is requested.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="0cfc2-107">[in] The document line for which the offset is requested.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="0cfc2-108">[in] The document column for which the offset is requested.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0cfc2-109">[out] A pointer to a `ULONG32` that receives the offsets.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cfc2-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0cfc2-110">Return Value</span></span>  
 <span data-ttu-id="0cfc2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="0cfc2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cfc2-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="0cfc2-112">Requirements</span></span>  
 <span data-ttu-id="0cfc2-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0cfc2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cfc2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cfc2-114">See also</span></span>

- [<span data-ttu-id="0cfc2-115">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="0cfc2-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
