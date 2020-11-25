---
title: ISymUnmanagedReader::GetUserEntryPoint, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
ms.openlocfilehash: f0a688aef9fbc6f7bfac85e06cbe7e76704d3230
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720529"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="a800e-102">ISymUnmanagedReader::GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="a800e-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>

<span data-ttu-id="a800e-103">Retourne la méthode spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="a800e-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="a800e-104">Par exemple, cette méthode peut être la méthode main de l’utilisateur plutôt que des stubs générés par le compilateur avant la méthode main.</span><span class="sxs-lookup"><span data-stu-id="a800e-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a800e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a800e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a800e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a800e-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="a800e-107">à Pointeur vers une variable qui reçoit le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a800e-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a800e-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a800e-108">Return Value</span></span>  

 <span data-ttu-id="a800e-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a800e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a800e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a800e-110">Requirements</span></span>  

 <span data-ttu-id="a800e-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a800e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a800e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a800e-112">See also</span></span>

- [<span data-ttu-id="a800e-113">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="a800e-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
