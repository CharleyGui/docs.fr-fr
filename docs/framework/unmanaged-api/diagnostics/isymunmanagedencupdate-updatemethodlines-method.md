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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54789003f7454a65449e55ea4d990edd672d9c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774683"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="d44ad-102">ISymUnmanagedENCUpdate::UpdateMethodLines, méthode</span><span class="sxs-lookup"><span data-stu-id="d44ad-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="d44ad-103">Permet la mise à jour les informations de ligne pour une méthode qui n’a pas été compilé, mais dont les lignes ont été déplacées indépendamment.</span><span class="sxs-lookup"><span data-stu-id="d44ad-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d44ad-104">Un delta pour chaque instruction est autorisé.</span><span class="sxs-lookup"><span data-stu-id="d44ad-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d44ad-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d44ad-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d44ad-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="d44ad-107">[in] Les métadonnées du jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="d44ad-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="d44ad-108">[in] Un tableau de `INT32` les valeurs qui indiquent les deltas pour chaque point de séquence dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="d44ad-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="d44ad-109">[in] Un `ULONG` contenant la taille de la `pDeltas` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d44ad-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d44ad-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d44ad-110">Return Value</span></span>  
 <span data-ttu-id="d44ad-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d44ad-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44ad-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d44ad-112">Requirements</span></span>  
 <span data-ttu-id="d44ad-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d44ad-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44ad-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d44ad-114">See also</span></span>

- [<span data-ttu-id="d44ad-115">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="d44ad-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
