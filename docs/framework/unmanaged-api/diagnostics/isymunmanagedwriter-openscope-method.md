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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6d563873045b4b5b427f06f0caa5420d31590b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777210"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="ddf63-102">ISymUnmanagedWriter::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="ddf63-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="ddf63-103">Ouvre une nouvelle portée lexicale dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="ddf63-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="ddf63-104">La portée devient la nouvelle portée actuelle et est envoyée à une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="ddf63-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="ddf63-105">Les portées doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="ddf63-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="ddf63-106">Frères ne sont pas autorisées à chevaucher.</span><span class="sxs-lookup"><span data-stu-id="ddf63-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddf63-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddf63-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddf63-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ddf63-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="ddf63-109">[in] Le décalage de la première instruction dans la portée lexicale, en octets, à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ddf63-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ddf63-110">[out] Un pointeur vers un `ULONG32` qui reçoit l’identificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="ddf63-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddf63-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ddf63-111">Return Value</span></span>  
 <span data-ttu-id="ddf63-112">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ddf63-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddf63-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ddf63-113">Remarks</span></span>  
 <span data-ttu-id="ddf63-114">`ISymUnmanagedWriter::OpenScope` Retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir une étendue de démarrage et de fin de décalage à partir d’une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ddf63-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="ddf63-115">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ddf63-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="ddf63-116">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="ddf63-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddf63-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ddf63-117">Requirements</span></span>  
 <span data-ttu-id="ddf63-118">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddf63-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf63-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddf63-119">See also</span></span>

- [<span data-ttu-id="ddf63-120">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="ddf63-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
