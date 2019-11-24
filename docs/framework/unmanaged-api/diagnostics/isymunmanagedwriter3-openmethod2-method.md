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
ms.openlocfilehash: 3a628aec0823c5db07d31d33813a020606906163
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438124"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="a1982-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="a1982-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="a1982-103">Ouvre une méthode et fournit son décalage de section réel dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a1982-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1982-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1982-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1982-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1982-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="a1982-106">dans Jeton de métadonnées de la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="a1982-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="a1982-107">dans Décalage de la section dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a1982-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="a1982-108">dans Décalage dans l’image.</span><span class="sxs-lookup"><span data-stu-id="a1982-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1982-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1982-109">Return Value</span></span>  
 <span data-ttu-id="a1982-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a1982-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1982-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1982-111">Requirements</span></span>  
 <span data-ttu-id="a1982-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a1982-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1982-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1982-113">See also</span></span>

- [<span data-ttu-id="a1982-114">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="a1982-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="a1982-115">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="a1982-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
