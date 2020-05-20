---
title: ISymUnmanagedNamespace::GetVariables, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 091f497024b48589953456e1ea6daf6635738240
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615083"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="2f9aa-102">ISymUnmanagedNamespace::GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="2f9aa-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="2f9aa-103">Retourne toutes les variables définies au niveau de la portée globale au sein de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f9aa-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f9aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f9aa-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="2f9aa-106">dans `ULONG32`Qui indique la taille du `pVars` tableau.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="2f9aa-107">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="2f9aa-108">à Pointeur vers une mémoire tampon qui contient les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f9aa-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2f9aa-109">Return Value</span></span>  
 <span data-ttu-id="2f9aa-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2f9aa-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f9aa-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="2f9aa-111">Requirements</span></span>  
 <span data-ttu-id="2f9aa-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f9aa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9aa-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f9aa-113">See also</span></span>

- [<span data-ttu-id="2f9aa-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="2f9aa-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
