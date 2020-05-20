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
ms.openlocfilehash: 8ee4c1bffccb44d15fa53eb3d4d6c0fcdc3e7697
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614966"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="6b634-102">ISymUnmanagedReader::GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="6b634-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="6b634-103">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6b634-103">Gets the method version.</span></span> <span data-ttu-id="6b634-104">La version de la méthode commence à 1 et est incrémentée chaque fois que la méthode est recompilée.</span><span class="sxs-lookup"><span data-stu-id="6b634-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="6b634-105">La recompilation peut se produire sans modification de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6b634-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b634-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b634-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b634-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b634-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="6b634-108">dans Méthode pour laquelle obtenir la version.</span><span class="sxs-lookup"><span data-stu-id="6b634-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="6b634-109">à Pointeur vers une variable qui reçoit la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6b634-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b634-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6b634-110">Return Value</span></span>  
 <span data-ttu-id="6b634-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6b634-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b634-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="6b634-112">Requirements</span></span>  
 <span data-ttu-id="6b634-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6b634-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b634-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b634-114">See also</span></span>

- [<span data-ttu-id="6b634-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="6b634-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
