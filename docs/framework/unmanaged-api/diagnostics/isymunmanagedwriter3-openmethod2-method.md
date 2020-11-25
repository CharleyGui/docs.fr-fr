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
ms.openlocfilehash: 39235c5c26cb168dfc995de97f72b80dccb6b818
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720293"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="2e722-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="2e722-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="2e722-103">Ouvre une méthode et fournit son décalage de section réel dans l’image.</span><span class="sxs-lookup"><span data-stu-id="2e722-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e722-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e722-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e722-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e722-105">Parameters</span></span>  

 `method`  
 <span data-ttu-id="2e722-106">dans Jeton de métadonnées de la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2e722-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="2e722-107">dans Décalage de la section dans l’image.</span><span class="sxs-lookup"><span data-stu-id="2e722-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="2e722-108">dans Décalage dans l’image.</span><span class="sxs-lookup"><span data-stu-id="2e722-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e722-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2e722-109">Return Value</span></span>  

 <span data-ttu-id="2e722-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e722-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e722-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e722-111">Requirements</span></span>  

 <span data-ttu-id="2e722-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2e722-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e722-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e722-113">See also</span></span>

- [<span data-ttu-id="2e722-114">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="2e722-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="2e722-115">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="2e722-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
