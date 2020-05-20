---
title: ISymUnmanagedScope::GetLocals, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: 0acd31d85504688427cace0222a657885035c537
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615382"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="4c566-102">ISymUnmanagedScope::GetLocals, méthode</span><span class="sxs-lookup"><span data-stu-id="4c566-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="4c566-103">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="4c566-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c566-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c566-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c566-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c566-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="4c566-106">dans `ULONG32`Qui indique la taille du `locals` tableau.</span><span class="sxs-lookup"><span data-stu-id="4c566-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="4c566-107">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les variables locales.</span><span class="sxs-lookup"><span data-stu-id="4c566-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="4c566-108">à Tableau qui reçoit les variables locales.</span><span class="sxs-lookup"><span data-stu-id="4c566-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c566-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c566-109">Return Value</span></span>  
 <span data-ttu-id="4c566-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4c566-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c566-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="4c566-111">Requirements</span></span>  
 <span data-ttu-id="4c566-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4c566-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c566-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c566-113">See also</span></span>

- [<span data-ttu-id="4c566-114">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="4c566-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
