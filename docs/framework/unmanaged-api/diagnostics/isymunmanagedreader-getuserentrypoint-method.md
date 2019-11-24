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
ms.openlocfilehash: 50f41bb55b7c3dc45646a465032074ce90be0abf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444508"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="3fe0d-102">ISymUnmanagedReader::GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="3fe0d-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="3fe0d-103">Returns the method that was specified as the user entry point for the module, if any.</span><span class="sxs-lookup"><span data-stu-id="3fe0d-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="3fe0d-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span><span class="sxs-lookup"><span data-stu-id="3fe0d-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe0d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fe0d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fe0d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fe0d-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="3fe0d-107">[out] A pointer to a variable that receives the entry point.</span><span class="sxs-lookup"><span data-stu-id="3fe0d-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fe0d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3fe0d-108">Return Value</span></span>  
 <span data-ttu-id="3fe0d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="3fe0d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe0d-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="3fe0d-110">Requirements</span></span>  
 <span data-ttu-id="3fe0d-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3fe0d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe0d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fe0d-112">See also</span></span>

- [<span data-ttu-id="3fe0d-113">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="3fe0d-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
