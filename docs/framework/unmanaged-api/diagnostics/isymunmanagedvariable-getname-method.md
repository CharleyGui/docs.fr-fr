---
title: ISymUnmanagedVariable::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726884"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="35e31-102">ISymUnmanagedVariable::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="35e31-102">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="35e31-103">Obtient le nom de cette variable.</span><span class="sxs-lookup"><span data-stu-id="35e31-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35e31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35e31-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35e31-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="35e31-106">dans Longueur de la mémoire tampon vers laquelle `pcchName` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="35e31-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="35e31-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris l’arrêt null.</span><span class="sxs-lookup"><span data-stu-id="35e31-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="35e31-108">à Mémoire tampon qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="35e31-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35e31-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="35e31-109">Return Value</span></span>  

 <span data-ttu-id="35e31-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="35e31-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e31-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35e31-111">Requirements</span></span>  

 <span data-ttu-id="35e31-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="35e31-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e31-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35e31-113">See also</span></span>

- [<span data-ttu-id="35e31-114">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="35e31-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
