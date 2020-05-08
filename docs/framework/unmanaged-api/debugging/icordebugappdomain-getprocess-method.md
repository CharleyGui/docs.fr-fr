---
title: ICorDebugAppDomain::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
ms.openlocfilehash: 90ac981f9b5ee71ca59f76823e7b796471571e4e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895202"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="c81b3-102">ICorDebugAppDomain::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="c81b3-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="c81b3-103">Obtient le processus qui contient le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c81b3-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c81b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c81b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c81b3-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="c81b3-106">à Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="c81b3-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81b3-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c81b3-107">Requirements</span></span>  
 <span data-ttu-id="c81b3-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81b3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81b3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c81b3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c81b3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c81b3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c81b3-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81b3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
