---
title: ISymUnmanagedENCUpdate::UpdateMethodLines, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 9a490299c24f44b59da682f714f4b696fde3cba5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614511"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="efb73-102">ISymUnmanagedENCUpdate::UpdateMethodLines, méthode</span><span class="sxs-lookup"><span data-stu-id="efb73-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="efb73-103">Autorise la mise à jour des informations de ligne pour une méthode qui n’a pas été recompilée, mais dont les lignes ont été déplacées indépendamment.</span><span class="sxs-lookup"><span data-stu-id="efb73-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="efb73-104">Un Delta est autorisé pour chaque instruction.</span><span class="sxs-lookup"><span data-stu-id="efb73-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb73-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efb73-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efb73-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efb73-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="efb73-107">dans Métadonnées du jeton de la méthode.</span><span class="sxs-lookup"><span data-stu-id="efb73-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="efb73-108">dans Tableau de `INT32` valeurs qui indique des deltas pour chaque point de séquence dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="efb73-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="efb73-109">dans `ULONG`Contenant la taille du `pDeltas` paramètre.</span><span class="sxs-lookup"><span data-stu-id="efb73-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efb73-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="efb73-110">Return Value</span></span>  
 <span data-ttu-id="efb73-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="efb73-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efb73-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="efb73-112">Requirements</span></span>  
 <span data-ttu-id="efb73-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="efb73-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb73-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efb73-114">See also</span></span>

- [<span data-ttu-id="efb73-115">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="efb73-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
