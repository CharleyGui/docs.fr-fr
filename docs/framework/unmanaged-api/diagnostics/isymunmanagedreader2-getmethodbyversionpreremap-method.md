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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06b8ebf26794baa1d957cc47d1179283611b62d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736681"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="1135a-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="1135a-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="1135a-103">Obtient une méthode de lecteur de symboles, étant donné un jeton de méthode et un numéro de version modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="1135a-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="1135a-104">Numéros de version commencent à 1 et sont incrémentés à chaque fois que la méthode est modifiée suite à une opération modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="1135a-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1135a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1135a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1135a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1135a-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="1135a-107">[in] Le jeton de métadonnées de méthode.</span><span class="sxs-lookup"><span data-stu-id="1135a-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="1135a-108">[in] La version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1135a-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1135a-109">[out] Un pointeur vers le texte retourné [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1135a-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1135a-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1135a-110">Return Value</span></span>  
 <span data-ttu-id="1135a-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1135a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1135a-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1135a-112">Requirements</span></span>  
 <span data-ttu-id="1135a-113">**En-tête :** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="1135a-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="1135a-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1135a-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1135a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1135a-115">See also</span></span>

- [<span data-ttu-id="1135a-116">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="1135a-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
