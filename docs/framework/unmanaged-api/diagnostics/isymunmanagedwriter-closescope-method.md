---
title: ISymUnmanagedWriter::CloseScope, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 264b4487483ed5439a9809feefcdc1b20af402dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428080"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="b8e9f-102">ISymUnmanagedWriter::CloseScope, méthode</span><span class="sxs-lookup"><span data-stu-id="b8e9f-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="b8e9f-103">Ferme la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8e9f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8e9f-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="b8e9f-106">dans Offset à partir du début de la méthode du point à la fin de la dernière instruction dans la portée lexicale, en octets.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8e9f-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b8e9f-107">Return Value</span></span>  
 <span data-ttu-id="b8e9f-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e9f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b8e9f-109">Remarks</span></span>  
 <span data-ttu-id="b8e9f-110">Une fois qu’une étendue est fermée, aucune autre variable ne peut être définie dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="b8e9f-111">[ISymUnmanagedWriter :: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter :: SetScopeRange,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir ultérieurement le décalage de début et de fin d’une portée.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="b8e9f-112">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et `ISymUnmanagedWriter::CloseScope` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="b8e9f-113">Les identificateurs d’étendue sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="b8e9f-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e9f-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8e9f-114">Requirements</span></span>  
 <span data-ttu-id="b8e9f-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b8e9f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e9f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8e9f-116">See also</span></span>

- [<span data-ttu-id="b8e9f-117">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="b8e9f-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
