---
title: ICorDebugAppDomain::GetId, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: 63346c679efc083dea9ab0eaa4f983a5308695f8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895250"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="35c22-102">ICorDebugAppDomain::GetId, méthode</span><span class="sxs-lookup"><span data-stu-id="35c22-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="35c22-103">Obtient l’identificateur unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="35c22-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35c22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35c22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35c22-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="35c22-106">à Identificateur unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="35c22-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35c22-107">Notes </span><span class="sxs-lookup"><span data-stu-id="35c22-107">Remarks</span></span>  
 <span data-ttu-id="35c22-108">L’identificateur du domaine d’application est unique au sein du processus conteneur.</span><span class="sxs-lookup"><span data-stu-id="35c22-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c22-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35c22-109">Requirements</span></span>  
 <span data-ttu-id="35c22-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35c22-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c22-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35c22-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35c22-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35c22-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35c22-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
