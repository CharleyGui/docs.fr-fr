---
title: ISymUnmanagedWriter::SetScopeRange, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c13eb7ca16cdb7c70f3fef0dd4efcb9362cd3d87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776585"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="8bc3b-102">ISymUnmanagedWriter::SetScopeRange, méthode</span><span class="sxs-lookup"><span data-stu-id="8bc3b-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="8bc3b-103">Définit la plage d'offsets pour la portée lexicale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="8bc3b-104">La portée devient la nouvelle portée actuelle et est envoyée à une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="8bc3b-105">Les portées doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="8bc3b-106">Frères ne sont pas autorisées à chevaucher.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc3b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bc3b-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bc3b-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8bc3b-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="8bc3b-109">[in] L’identificateur de portée pour la portée.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="8bc3b-110">[in] Offset, en octets, de la première instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="8bc3b-111">[in] Offset, en octets, de la dernière instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc3b-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8bc3b-112">Return Value</span></span>  
 <span data-ttu-id="8bc3b-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bc3b-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8bc3b-114">Remarks</span></span>  
 <span data-ttu-id="8bc3b-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec `ISymUnmanagedWriter::SetScopeRange` pour définir une étendue de démarrage et de fin de décalage à partir d’une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="8bc3b-116">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="8bc3b-117">Identificateurs d’étendue sont uniquement valides dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="8bc3b-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc3b-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8bc3b-118">Requirements</span></span>  
 <span data-ttu-id="8bc3b-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8bc3b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc3b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bc3b-120">See also</span></span>

- [<span data-ttu-id="8bc3b-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="8bc3b-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
