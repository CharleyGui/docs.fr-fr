---
title: ISymUnmanagedReader::GetMethodVersion, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f45423bb0ff4c755e657729c5725c8d9a22bde3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746767"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="3c163-102">ISymUnmanagedReader::GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="3c163-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="3c163-103">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3c163-103">Gets the method version.</span></span> <span data-ttu-id="3c163-104">La version de la méthode commence à 1 et est incrémentée chaque fois que la méthode est recompilé.</span><span class="sxs-lookup"><span data-stu-id="3c163-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="3c163-105">Recompilation peut se produire sans modification à la méthode.</span><span class="sxs-lookup"><span data-stu-id="3c163-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c163-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c163-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c163-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c163-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="3c163-108">[in] La méthode pour laquelle obtenir la version.</span><span class="sxs-lookup"><span data-stu-id="3c163-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="3c163-109">[out] Pointeur vers une variable qui reçoit la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3c163-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c163-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3c163-110">Return Value</span></span>  
 <span data-ttu-id="3c163-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3c163-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c163-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c163-112">Requirements</span></span>  
 <span data-ttu-id="3c163-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3c163-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c163-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c163-114">See also</span></span>

- [<span data-ttu-id="3c163-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="3c163-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
