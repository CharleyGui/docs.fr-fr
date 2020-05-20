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
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614719"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="f9e29-102">ISymUnmanagedWriter2::DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="f9e29-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="f9e29-103">Définit un nom pour une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="f9e29-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9e29-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9e29-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9e29-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f9e29-106">dans Nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="f9e29-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="f9e29-107">dans Valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="f9e29-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="f9e29-108">dans Jeton de métadonnées de la constante.</span><span class="sxs-lookup"><span data-stu-id="f9e29-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e29-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f9e29-109">Return Value</span></span>  
 <span data-ttu-id="f9e29-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f9e29-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e29-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f9e29-111">Requirements</span></span>  
 <span data-ttu-id="f9e29-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9e29-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e29-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9e29-113">See also</span></span>

- [<span data-ttu-id="f9e29-114">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="f9e29-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="f9e29-115">DefineConstant, méthode</span><span class="sxs-lookup"><span data-stu-id="f9e29-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
