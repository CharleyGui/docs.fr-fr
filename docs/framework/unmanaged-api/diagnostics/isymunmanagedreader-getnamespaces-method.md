---
title: ISymUnmanagedReader::GetNamespaces, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 44f9284f0a89f0941940cf379c48b2b138149122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614940"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="4aa61-102">ISymUnmanagedReader::GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="4aa61-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="4aa61-103">Obtient les espaces de noms définis au niveau de la portée globale dans ce magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="4aa61-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aa61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aa61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4aa61-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="4aa61-106">dans Taille du tableau d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="4aa61-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="4aa61-107">à Pointeur vers une variable qui reçoit la longueur de la liste d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="4aa61-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="4aa61-108">à Pointeur vers une variable qui reçoit la liste d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="4aa61-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aa61-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4aa61-109">Return Value</span></span>  
 <span data-ttu-id="4aa61-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4aa61-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa61-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="4aa61-111">Requirements</span></span>  
 <span data-ttu-id="4aa61-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4aa61-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa61-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4aa61-113">See also</span></span>

- [<span data-ttu-id="4aa61-114">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="4aa61-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
