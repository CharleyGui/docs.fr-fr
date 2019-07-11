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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 995c7edf99c917b8bcdc1d51dcc0bf50868e4f35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777056"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="19b72-102">ISymUnmanagedReader::GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="19b72-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="19b72-103">Retourne la méthode qui a été spécifiée comme point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="19b72-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="19b72-104">Par exemple, cette méthode peut être la méthode de l’utilisateur principal plutôt que les stubs générés par le compilateur avant la méthode principale.</span><span class="sxs-lookup"><span data-stu-id="19b72-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b72-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19b72-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19b72-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19b72-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="19b72-107">[out] Pointeur vers une variable qui reçoit le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="19b72-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19b72-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="19b72-108">Return Value</span></span>  
 <span data-ttu-id="19b72-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="19b72-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19b72-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="19b72-110">Requirements</span></span>  
 <span data-ttu-id="19b72-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="19b72-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b72-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19b72-112">See also</span></span>

- [<span data-ttu-id="19b72-113">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="19b72-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
