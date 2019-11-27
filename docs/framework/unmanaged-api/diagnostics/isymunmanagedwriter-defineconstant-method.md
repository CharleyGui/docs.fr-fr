---
title: ISymUnmanagedWriter::DefineConstant, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: c8d0145b9dffe1c0ff6ed3281c90f3bcec082ab8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428063"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="bdb27-102">ISymUnmanagedWriter::DefineConstant, méthode</span><span class="sxs-lookup"><span data-stu-id="bdb27-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="bdb27-103">Définit un nom pour une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="bdb27-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb27-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdb27-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdb27-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bdb27-106">dans Pointeur vers un `WCHAR` qui définit le nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="bdb27-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="bdb27-107">dans Valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="bdb27-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="bdb27-108">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="bdb27-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="bdb27-109">dans Signature de type pour la constante.</span><span class="sxs-lookup"><span data-stu-id="bdb27-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdb27-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bdb27-110">Return Value</span></span>  
 <span data-ttu-id="bdb27-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bdb27-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb27-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdb27-112">Requirements</span></span>  
 <span data-ttu-id="bdb27-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bdb27-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb27-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdb27-114">See also</span></span>

- [<span data-ttu-id="bdb27-115">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="bdb27-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="bdb27-116">DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="bdb27-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
