---
title: ISymUnmanagedENCUpdate::GetLocalVariables, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 5e5bf097a4b1e366fff807595b22c4696a91cf43
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614550"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="bf482-102">ISymUnmanagedENCUpdate::GetLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="bf482-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="bf482-103">Obtient les variables locales.</span><span class="sxs-lookup"><span data-stu-id="bf482-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf482-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf482-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf482-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf482-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="bf482-106">dans Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bf482-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="bf482-107">dans `ULONG`Qui indique la taille du `rgLocals` paramètre.</span><span class="sxs-lookup"><span data-stu-id="bf482-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="bf482-108">à Tableau retourné d’instances [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bf482-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bf482-109">à Pointeur vers un `ULONG` qui reçoit la taille de la `rgLocals` mémoire tampon requise pour contenir les variables locales.</span><span class="sxs-lookup"><span data-stu-id="bf482-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf482-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bf482-110">Return Value</span></span>  
 <span data-ttu-id="bf482-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bf482-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf482-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="bf482-112">Requirements</span></span>  
 <span data-ttu-id="bf482-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bf482-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf482-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf482-114">See also</span></span>

- [<span data-ttu-id="bf482-115">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="bf482-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
