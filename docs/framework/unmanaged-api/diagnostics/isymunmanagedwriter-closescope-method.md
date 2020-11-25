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
ms.openlocfilehash: 561a6348b9976789b02961fadb37d9127f5a6a13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713039"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="1a882-102">ISymUnmanagedWriter::CloseScope, méthode</span><span class="sxs-lookup"><span data-stu-id="1a882-102">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="1a882-103">Ferme la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="1a882-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a882-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a882-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a882-105">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="1a882-106">dans Offset à partir du début de la méthode du point à la fin de la dernière instruction dans la portée lexicale, en octets.</span><span class="sxs-lookup"><span data-stu-id="1a882-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a882-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1a882-107">Return Value</span></span>  

 <span data-ttu-id="1a882-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1a882-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a882-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a882-109">Remarks</span></span>  

 <span data-ttu-id="1a882-110">Une fois qu’une étendue est fermée, aucune autre variable ne peut être définie dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="1a882-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="1a882-111">[ISymUnmanagedWriter :: OpenScope](isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter :: SetScopeRange,](isymunmanagedwriter-setscoperange-method.md) pour définir ultérieurement le décalage de début et de fin d’une portée.</span><span class="sxs-lookup"><span data-stu-id="1a882-111">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="1a882-112">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et `ISymUnmanagedWriter::CloseScope` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="1a882-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="1a882-113">Les identificateurs d’étendue sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="1a882-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a882-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a882-114">Requirements</span></span>  

 <span data-ttu-id="1a882-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1a882-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a882-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a882-116">See also</span></span>

- [<span data-ttu-id="1a882-117">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="1a882-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
