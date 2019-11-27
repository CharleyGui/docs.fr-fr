---
title: ISymUnmanagedWriter::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 915b05d0d2ac611678fdcc94dd42bbb1962e6ceb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427895"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="150d4-102">ISymUnmanagedWriter::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="150d4-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="150d4-103">Ouvre une nouvelle portée lexicale dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="150d4-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="150d4-104">La portée devient la nouvelle portée actuelle et fait l’objet d’un push dans une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="150d4-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="150d4-105">Les étendues doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="150d4-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="150d4-106">Les frères ne sont pas autorisés à se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="150d4-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150d4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="150d4-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="150d4-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="150d4-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="150d4-109">dans Offset de la première instruction dans la portée lexicale, en octets, à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="150d4-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="150d4-110">à Pointeur vers un `ULONG32` qui reçoit l’identificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="150d4-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="150d4-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="150d4-111">Return Value</span></span>  
 <span data-ttu-id="150d4-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="150d4-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="150d4-113">Notes</span><span class="sxs-lookup"><span data-stu-id="150d4-113">Remarks</span></span>  
 <span data-ttu-id="150d4-114">`ISymUnmanagedWriter::OpenScope` retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter :: SetScopeRange,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir ultérieurement le décalage de début et de fin d’une portée.</span><span class="sxs-lookup"><span data-stu-id="150d4-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="150d4-115">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter :: CloseScope,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="150d4-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="150d4-116">Les identificateurs d’étendue sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="150d4-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150d4-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="150d4-117">Requirements</span></span>  
 <span data-ttu-id="150d4-118">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="150d4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150d4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="150d4-119">See also</span></span>

- [<span data-ttu-id="150d4-120">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="150d4-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
