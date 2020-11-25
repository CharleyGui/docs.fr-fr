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
ms.openlocfilehash: 5484242562deaf463b7435ad4e54735a7abee45e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730485"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="6eb5f-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="6eb5f-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>

<span data-ttu-id="6eb5f-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="6eb5f-104">Les numéros de version commencent à 1 et sont incrémentés chaque fois que la méthode est modifiée à la suite d’une opération modifier & continuer.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb5f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb5f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6eb5f-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="6eb5f-107">dans Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="6eb5f-108">dans Version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6eb5f-109">à Pointeur vers l’interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eb5f-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6eb5f-110">Return Value</span></span>  

 <span data-ttu-id="6eb5f-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb5f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6eb5f-112">Requirements</span></span>  

 <span data-ttu-id="6eb5f-113">**En-tête :** CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="6eb5f-114">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6eb5f-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb5f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6eb5f-115">See also</span></span>

- [<span data-ttu-id="6eb5f-116">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="6eb5f-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
