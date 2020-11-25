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
ms.openlocfilehash: 88866d75cc97d40c827359450e8e7bdbe13ef3ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715886"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="b4953-102">ICorDebugAppDomain::GetId, méthode</span><span class="sxs-lookup"><span data-stu-id="b4953-102">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="b4953-103">Obtient l’identificateur unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b4953-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4953-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4953-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4953-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4953-105">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="b4953-106">à Identificateur unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b4953-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4953-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="b4953-107">Remarks</span></span>  

 <span data-ttu-id="b4953-108">L’identificateur du domaine d’application est unique au sein du processus conteneur.</span><span class="sxs-lookup"><span data-stu-id="b4953-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4953-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4953-109">Requirements</span></span>  

 <span data-ttu-id="b4953-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4953-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4953-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4953-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4953-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4953-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4953-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4953-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
