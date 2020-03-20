---
title: ISymUnmanagedWriter3::OpenMethod2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178318"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="fe6b9-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="fe6b9-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="fe6b9-103">Ouvre une méthode et fournit sa section réelle compensée dans l’image.</span><span class="sxs-lookup"><span data-stu-id="fe6b9-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe6b9-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe6b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe6b9-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="fe6b9-106">[dans] Les métadonnées symboliques pour l’ouverture de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fe6b9-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="fe6b9-107">[dans] La section compensée dans l’image.</span><span class="sxs-lookup"><span data-stu-id="fe6b9-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="fe6b9-108">[dans] Le décalage dans l’image.</span><span class="sxs-lookup"><span data-stu-id="fe6b9-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe6b9-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fe6b9-109">Return Value</span></span>  
 <span data-ttu-id="fe6b9-110">S_OK si la méthode réussit; autrement, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fe6b9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6b9-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fe6b9-111">Requirements</span></span>  
 <span data-ttu-id="fe6b9-112">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe6b9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6b9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe6b9-113">See also</span></span>

- [<span data-ttu-id="fe6b9-114">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="fe6b9-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="fe6b9-115">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="fe6b9-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
