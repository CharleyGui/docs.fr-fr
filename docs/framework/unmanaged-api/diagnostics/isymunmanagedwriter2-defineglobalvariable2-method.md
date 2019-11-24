---
title: ISymUnmanagedWriter2::DefineGlobalVariable2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: 12475b1ac8a1a81e565aa689eac2ae1a9b55e73a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438288"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="48367-102">ISymUnmanagedWriter2::DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="48367-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="48367-103">Defines a single global variable.</span><span class="sxs-lookup"><span data-stu-id="48367-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48367-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48367-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48367-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48367-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="48367-106">[in] The global variable name.</span><span class="sxs-lookup"><span data-stu-id="48367-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="48367-107">[in] The global variable attributes.</span><span class="sxs-lookup"><span data-stu-id="48367-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="48367-108">[in] The metadata token of the signature.</span><span class="sxs-lookup"><span data-stu-id="48367-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="48367-109">[in] The address type.</span><span class="sxs-lookup"><span data-stu-id="48367-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="48367-110">[in] The first address for the parameter specification.</span><span class="sxs-lookup"><span data-stu-id="48367-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="48367-111">[in] The second address for the parameter specification.</span><span class="sxs-lookup"><span data-stu-id="48367-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="48367-112">[in] The third address for the parameter specification.</span><span class="sxs-lookup"><span data-stu-id="48367-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48367-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="48367-113">Return Value</span></span>  
 <span data-ttu-id="48367-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="48367-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48367-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="48367-115">Requirements</span></span>  
 <span data-ttu-id="48367-116">**Header:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="48367-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48367-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48367-117">See also</span></span>

- [<span data-ttu-id="48367-118">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="48367-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="48367-119">DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="48367-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
