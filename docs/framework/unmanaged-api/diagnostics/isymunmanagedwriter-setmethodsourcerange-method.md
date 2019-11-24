---
title: ISymUnmanagedWriter::SetMethodSourceRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427865"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="2db63-102">ISymUnmanagedWriter::SetMethodSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="2db63-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="2db63-103">Specifies the true start and end of a method within a source file.</span><span class="sxs-lookup"><span data-stu-id="2db63-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="2db63-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span><span class="sxs-lookup"><span data-stu-id="2db63-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db63-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2db63-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2db63-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2db63-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="2db63-107">[in] A pointer to the document containing the starting position.</span><span class="sxs-lookup"><span data-stu-id="2db63-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="2db63-108">[in] The starting line number.</span><span class="sxs-lookup"><span data-stu-id="2db63-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="2db63-109">[in] The starting column.</span><span class="sxs-lookup"><span data-stu-id="2db63-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="2db63-110">[in] A pointer to the document containing the ending position.</span><span class="sxs-lookup"><span data-stu-id="2db63-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="2db63-111">[in] The ending line number.</span><span class="sxs-lookup"><span data-stu-id="2db63-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="2db63-112">[in] The ending column number.</span><span class="sxs-lookup"><span data-stu-id="2db63-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2db63-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2db63-113">Return Value</span></span>  
 <span data-ttu-id="2db63-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="2db63-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db63-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="2db63-115">Requirements</span></span>  
 <span data-ttu-id="2db63-116">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2db63-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db63-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db63-117">See also</span></span>

- [<span data-ttu-id="2db63-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="2db63-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
