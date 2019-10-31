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
ms.openlocfilehash: 53042e722809a6574396648529c677d749154716
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132737"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="7cf8b-102">ICorDebugAssembly::GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="7cf8b-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="7cf8b-103">Obtient un pointeur d’interface vers le domaine d’application qui contient cette `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="7cf8b-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cf8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf8b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7cf8b-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="7cf8b-106">à Pointeur vers l’adresse d’une interface ICorDebugAppDomain qui représente le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7cf8b-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf8b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7cf8b-107">Remarks</span></span>  
 <span data-ttu-id="7cf8b-108">Si cet assembly est l’assembly système, `GetAppDomain` retourne la valeur null.</span><span class="sxs-lookup"><span data-stu-id="7cf8b-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf8b-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="7cf8b-109">Requirements</span></span>  
 <span data-ttu-id="7cf8b-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf8b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cf8b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cf8b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cf8b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf8b-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
