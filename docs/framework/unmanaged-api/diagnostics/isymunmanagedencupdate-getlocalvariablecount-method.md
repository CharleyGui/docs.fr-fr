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
ms.openlocfilehash: 19e07fb181f631335a0c56bd59b6fc8e14e2f36d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726923"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="dbf90-102">ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="dbf90-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>

<span data-ttu-id="dbf90-103">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="dbf90-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbf90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbf90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbf90-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbf90-105">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="dbf90-106">dans Jeton de métadonnées des méthodes.</span><span class="sxs-lookup"><span data-stu-id="dbf90-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="dbf90-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="dbf90-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbf90-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="dbf90-108">Return Value</span></span>  

 <span data-ttu-id="dbf90-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="dbf90-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbf90-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dbf90-110">Requirements</span></span>  

 <span data-ttu-id="dbf90-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dbf90-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf90-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbf90-112">See also</span></span>

- [<span data-ttu-id="dbf90-113">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="dbf90-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
