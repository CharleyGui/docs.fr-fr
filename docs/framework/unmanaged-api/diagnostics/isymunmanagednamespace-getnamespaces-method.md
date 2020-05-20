---
title: ISymUnmanagedNamespace::GetNamespaces, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: 48c50ac6be6d525676d85578e5a55a27104c180a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615096"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="87f52-102">ISymUnmanagedNamespace::GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="87f52-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="87f52-103">Obtient les enfants de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="87f52-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87f52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f52-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87f52-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="87f52-106">dans `ULONG32`Qui indique la taille du `namespaces` tableau.</span><span class="sxs-lookup"><span data-stu-id="87f52-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="87f52-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="87f52-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="87f52-108">à Pointeur vers la mémoire tampon qui contient les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="87f52-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87f52-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="87f52-109">Return Value</span></span>  
 <span data-ttu-id="87f52-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="87f52-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f52-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="87f52-111">Requirements</span></span>  
 <span data-ttu-id="87f52-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="87f52-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f52-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87f52-113">See also</span></span>

- [<span data-ttu-id="87f52-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="87f52-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
