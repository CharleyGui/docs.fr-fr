---
title: ISymUnmanagedNamespace::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: eca1137fb607d64e8645de5b0afc7ca391eac763
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699259"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="7d467-102">ISymUnmanagedNamespace::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="7d467-102">ISymUnmanagedNamespace::GetName Method</span></span>

<span data-ttu-id="7d467-103">Obtient le nom de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7d467-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d467-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d467-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d467-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d467-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="7d467-106">dans `ULONG32` Qui indique la taille de la `szName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7d467-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7d467-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom de l’espace de noms, y compris le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="7d467-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="7d467-108">à Pointeur vers une mémoire tampon qui contient le nom de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7d467-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d467-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="7d467-109">Return Value</span></span>  

 <span data-ttu-id="7d467-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7d467-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d467-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7d467-111">Requirements</span></span>  

 <span data-ttu-id="7d467-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7d467-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d467-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d467-113">See also</span></span>

- [<span data-ttu-id="7d467-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="7d467-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
