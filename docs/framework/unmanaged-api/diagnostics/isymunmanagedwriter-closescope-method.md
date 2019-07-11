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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9edfa2f8888480c72f290ee237972f3a0ed912
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778123"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="1232a-102">ISymUnmanagedWriter::CloseScope, méthode</span><span class="sxs-lookup"><span data-stu-id="1232a-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="1232a-103">Ferme la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="1232a-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1232a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1232a-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1232a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1232a-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="1232a-106">[in] Le décalage à partir du début de la méthode du point à la fin de la dernière instruction dans la portée lexicale, en octets.</span><span class="sxs-lookup"><span data-stu-id="1232a-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1232a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1232a-107">Return Value</span></span>  
 <span data-ttu-id="1232a-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1232a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1232a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1232a-109">Remarks</span></span>  
 <span data-ttu-id="1232a-110">Une fois qu’une portée est fermée, plus aucune variable ne peut être définie qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="1232a-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="1232a-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir ultérieurement une étendue de démarrage et de fin de décalage.</span><span class="sxs-lookup"><span data-stu-id="1232a-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="1232a-112">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et `ISymUnmanagedWriter::CloseScope` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="1232a-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="1232a-113">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="1232a-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1232a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1232a-114">Requirements</span></span>  
 <span data-ttu-id="1232a-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1232a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1232a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1232a-116">See also</span></span>

- [<span data-ttu-id="1232a-117">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="1232a-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
