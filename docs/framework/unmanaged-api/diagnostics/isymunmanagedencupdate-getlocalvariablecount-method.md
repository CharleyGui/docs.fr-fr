---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d56785815105e2f4b06217d3375e2d1cfdf0494c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776908"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="e3477-102">ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="e3477-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="e3477-103">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="e3477-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3477-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3477-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3477-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3477-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="e3477-106">[in] Le jeton de métadonnées de méthodes.</span><span class="sxs-lookup"><span data-stu-id="e3477-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="e3477-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="e3477-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3477-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e3477-108">Return Value</span></span>  
 <span data-ttu-id="e3477-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e3477-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3477-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e3477-110">Requirements</span></span>  
 <span data-ttu-id="e3477-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3477-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3477-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3477-112">See also</span></span>

- [<span data-ttu-id="e3477-113">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="e3477-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
