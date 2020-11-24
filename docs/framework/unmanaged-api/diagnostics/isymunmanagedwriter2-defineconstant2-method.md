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
ms.openlocfilehash: d45ab56f081bf0a8802b17e338f7b404809f0f16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683470"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="f7652-102">ISymUnmanagedWriter2::DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="f7652-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>

<span data-ttu-id="f7652-103">Définit un nom pour une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="f7652-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7652-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7652-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7652-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7652-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="f7652-106">dans Nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="f7652-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="f7652-107">dans Valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="f7652-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="f7652-108">dans Jeton de métadonnées de la constante.</span><span class="sxs-lookup"><span data-stu-id="f7652-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7652-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f7652-109">Return Value</span></span>  

 <span data-ttu-id="f7652-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f7652-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7652-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7652-111">Requirements</span></span>  

 <span data-ttu-id="f7652-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f7652-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7652-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7652-113">See also</span></span>

- [<span data-ttu-id="f7652-114">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="f7652-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="f7652-115">DefineConstant, méthode</span><span class="sxs-lookup"><span data-stu-id="f7652-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
