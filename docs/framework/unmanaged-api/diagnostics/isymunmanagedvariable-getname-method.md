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
ms.openlocfilehash: b48d131fa99b65d38856d2b635bf59145db9157e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615239"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="b232f-102">ISymUnmanagedVariable::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="b232f-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="b232f-103">Obtient le nom de cette variable.</span><span class="sxs-lookup"><span data-stu-id="b232f-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b232f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b232f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b232f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b232f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b232f-106">dans Longueur de la mémoire tampon vers laquelle `pcchName` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b232f-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b232f-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris l’arrêt null.</span><span class="sxs-lookup"><span data-stu-id="b232f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b232f-108">à Mémoire tampon qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="b232f-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b232f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b232f-109">Return Value</span></span>  
 <span data-ttu-id="b232f-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b232f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b232f-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b232f-111">Requirements</span></span>  
 <span data-ttu-id="b232f-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b232f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b232f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b232f-113">See also</span></span>

- [<span data-ttu-id="b232f-114">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="b232f-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
