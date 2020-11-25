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
ms.openlocfilehash: b0590f93c6a4c5ef28e03fc909c1f6a1474e5fad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720605"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="e6978-102">ISymUnmanagedReader::GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="e6978-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="e6978-103">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e6978-103">Gets the method version.</span></span> <span data-ttu-id="e6978-104">La version de la méthode commence à 1 et est incrémentée chaque fois que la méthode est recompilée.</span><span class="sxs-lookup"><span data-stu-id="e6978-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="e6978-105">La recompilation peut se produire sans modification de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e6978-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6978-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6978-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6978-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6978-107">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="e6978-108">dans Méthode pour laquelle obtenir la version.</span><span class="sxs-lookup"><span data-stu-id="e6978-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="e6978-109">à Pointeur vers une variable qui reçoit la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e6978-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6978-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e6978-110">Return Value</span></span>  

 <span data-ttu-id="e6978-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e6978-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6978-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e6978-112">Requirements</span></span>  

 <span data-ttu-id="e6978-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e6978-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6978-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6978-114">See also</span></span>

- [<span data-ttu-id="e6978-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="e6978-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
