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
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894933"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="36f05-102">ICorDebugAssembly::GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="36f05-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="36f05-103">Obtient un pointeur d’interface vers le domaine d’application qui `ICorDebugAssembly` contient cette instance.</span><span class="sxs-lookup"><span data-stu-id="36f05-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36f05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36f05-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36f05-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="36f05-106">à Pointeur vers l’adresse d’une interface ICorDebugAppDomain qui représente le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="36f05-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36f05-107">Notes </span><span class="sxs-lookup"><span data-stu-id="36f05-107">Remarks</span></span>  
 <span data-ttu-id="36f05-108">Si cet assembly est l’assembly `GetAppDomain` système, retourne la valeur null.</span><span class="sxs-lookup"><span data-stu-id="36f05-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36f05-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="36f05-109">Requirements</span></span>  
 <span data-ttu-id="36f05-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f05-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f05-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36f05-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36f05-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36f05-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36f05-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
