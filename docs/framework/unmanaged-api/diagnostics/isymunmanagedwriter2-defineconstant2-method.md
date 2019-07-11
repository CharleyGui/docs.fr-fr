---
title: ISymUnmanagedWriter2::DefineConstant2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c194cea21901015153626dc5aead49ed1b2c3df7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755111"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="b5b1b-102">ISymUnmanagedWriter2::DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="b5b1b-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="b5b1b-103">Définit un nom pour une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="b5b1b-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5b1b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5b1b-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b5b1b-106">[in] Le nom de constante.</span><span class="sxs-lookup"><span data-stu-id="b5b1b-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="b5b1b-107">[in] La valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="b5b1b-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b5b1b-108">[in] Le jeton de métadonnées de la constante.</span><span class="sxs-lookup"><span data-stu-id="b5b1b-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5b1b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b5b1b-109">Return Value</span></span>  
 <span data-ttu-id="b5b1b-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b5b1b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5b1b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5b1b-111">Requirements</span></span>  
 <span data-ttu-id="b5b1b-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5b1b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b1b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5b1b-113">See also</span></span>

- [<span data-ttu-id="b5b1b-114">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="b5b1b-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="b5b1b-115">DefineConstant, méthode</span><span class="sxs-lookup"><span data-stu-id="b5b1b-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
