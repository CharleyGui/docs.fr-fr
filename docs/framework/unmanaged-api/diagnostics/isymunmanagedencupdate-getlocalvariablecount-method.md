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
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614576"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="8e5d7-102">ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="8e5d7-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="8e5d7-103">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="8e5d7-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e5d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e5d7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e5d7-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="8e5d7-106">dans Jeton de métadonnées des méthodes.</span><span class="sxs-lookup"><span data-stu-id="8e5d7-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="8e5d7-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="8e5d7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e5d7-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8e5d7-108">Return Value</span></span>  
 <span data-ttu-id="8e5d7-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8e5d7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e5d7-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="8e5d7-110">Requirements</span></span>  
 <span data-ttu-id="8e5d7-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8e5d7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5d7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e5d7-112">See also</span></span>

- [<span data-ttu-id="8e5d7-113">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="8e5d7-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
