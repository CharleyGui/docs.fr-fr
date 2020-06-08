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
ms.openlocfilehash: a1da070f261f224d212d1fba81c287285a54d0d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501690"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="9d08e-102">ISymUnmanagedWriter::SetScopeRange, méthode</span><span class="sxs-lookup"><span data-stu-id="9d08e-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="9d08e-103">Définit la plage d'offsets pour la portée lexicale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9d08e-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="9d08e-104">La portée devient la nouvelle portée actuelle et fait l’objet d’un push dans une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="9d08e-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="9d08e-105">Les étendues doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="9d08e-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="9d08e-106">Les frères ne sont pas autorisés à se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="9d08e-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d08e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d08e-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d08e-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d08e-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="9d08e-109">dans Identificateur de portée de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="9d08e-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="9d08e-110">dans Offset, en octets, de la première instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9d08e-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="9d08e-111">dans Offset, en octets, de la dernière instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9d08e-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d08e-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9d08e-112">Return Value</span></span>  
 <span data-ttu-id="9d08e-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9d08e-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d08e-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d08e-114">Remarks</span></span>  
 <span data-ttu-id="9d08e-115">[ISymUnmanagedWriter :: OpenScope](isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec `ISymUnmanagedWriter::SetScopeRange` pour définir les offsets de début et de fin d’une portée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9d08e-115">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="9d08e-116">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter :: CloseScope,](isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="9d08e-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="9d08e-117">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d08e-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d08e-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d08e-118">Requirements</span></span>  
 <span data-ttu-id="9d08e-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9d08e-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d08e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d08e-120">See also</span></span>

- [<span data-ttu-id="9d08e-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="9d08e-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
