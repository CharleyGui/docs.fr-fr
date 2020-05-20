---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b12ecfdaf7c90589ce2e96b39f7437444cb91b09
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615421"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="59cb4-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="59cb4-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="59cb4-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="59cb4-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="59cb4-104">Les numéros de version commencent à 1 et sont incrémentés chaque fois que la méthode est modifiée à la suite d’une opération modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="59cb4-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cb4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59cb4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59cb4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59cb4-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="59cb4-107">dans Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="59cb4-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="59cb4-108">dans Version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="59cb4-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="59cb4-109">à Pointeur vers l’interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="59cb4-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59cb4-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="59cb4-110">Return Value</span></span>  
 <span data-ttu-id="59cb4-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="59cb4-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cb4-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="59cb4-112">Requirements</span></span>  
 <span data-ttu-id="59cb4-113">**En-tête :** CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="59cb4-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="59cb4-114">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="59cb4-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cb4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59cb4-115">See also</span></span>

- [<span data-ttu-id="59cb4-116">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="59cb4-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
