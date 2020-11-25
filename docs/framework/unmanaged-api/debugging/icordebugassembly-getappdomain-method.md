---
title: ICorDebugAssembly::GetAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 55a798bcc575aee3f309c35eb454a0675e0cbd97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734073"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="25644-102">ICorDebugAssembly::GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="25644-102">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="25644-103">Obtient un pointeur d’interface vers le domaine d’application qui contient cette `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="25644-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25644-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25644-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25644-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25644-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="25644-106">à Pointeur vers l’adresse d’une interface ICorDebugAppDomain qui représente le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="25644-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25644-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="25644-107">Remarks</span></span>  

 <span data-ttu-id="25644-108">Si cet assembly est l’assembly système, `GetAppDomain` retourne la valeur null.</span><span class="sxs-lookup"><span data-stu-id="25644-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25644-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25644-109">Requirements</span></span>  

 <span data-ttu-id="25644-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25644-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25644-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25644-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25644-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25644-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25644-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25644-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
