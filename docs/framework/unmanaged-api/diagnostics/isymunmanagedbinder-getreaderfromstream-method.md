---
title: ISymUnmanagedBinder::GetReaderFromStream, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: b1cb2bf3aa021ed738f7fad93fc4b86d97baf1e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449379"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="2dc95-102">ISymUnmanagedBinder::GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="2dc95-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="2dc95-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span><span class="sxs-lookup"><span data-stu-id="2dc95-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dc95-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc95-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2dc95-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2dc95-106">[in] A pointer to the metadata import interface.</span><span class="sxs-lookup"><span data-stu-id="2dc95-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="2dc95-107">[in] A pointer to the stream that contains the symbol store.</span><span class="sxs-lookup"><span data-stu-id="2dc95-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2dc95-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2dc95-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dc95-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2dc95-109">Return Value</span></span>  
 <span data-ttu-id="2dc95-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="2dc95-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc95-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="2dc95-111">Requirements</span></span>  
 <span data-ttu-id="2dc95-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2dc95-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc95-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dc95-113">See also</span></span>

- [<span data-ttu-id="2dc95-114">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="2dc95-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
