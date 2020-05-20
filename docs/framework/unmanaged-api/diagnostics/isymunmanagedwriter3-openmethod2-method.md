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
ms.openlocfilehash: e88a844a7f79f14c717a5966b345588b3b3b9f81
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609415"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="ebbde-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="ebbde-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="ebbde-103">Ouvre une méthode et fournit son décalage de section réel dans l’image.</span><span class="sxs-lookup"><span data-stu-id="ebbde-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebbde-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebbde-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ebbde-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="ebbde-106">dans Jeton de métadonnées de la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="ebbde-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="ebbde-107">dans Décalage de la section dans l’image.</span><span class="sxs-lookup"><span data-stu-id="ebbde-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="ebbde-108">dans Décalage dans l’image.</span><span class="sxs-lookup"><span data-stu-id="ebbde-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebbde-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ebbde-109">Return Value</span></span>  
 <span data-ttu-id="ebbde-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ebbde-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbde-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ebbde-111">Requirements</span></span>  
 <span data-ttu-id="ebbde-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ebbde-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbde-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebbde-113">See also</span></span>

- [<span data-ttu-id="ebbde-114">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="ebbde-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="ebbde-115">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="ebbde-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
