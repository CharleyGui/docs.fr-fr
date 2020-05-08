---
title: ICorDebugAppDomain::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895214"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="58e50-102">ICorDebugAppDomain::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="58e50-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="58e50-103">Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="58e50-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58e50-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58e50-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="58e50-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le domaine d’application CLR.</span><span class="sxs-lookup"><span data-stu-id="58e50-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58e50-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="58e50-107">Return Value</span></span>  
 <span data-ttu-id="58e50-108">Si un objet <xref:System.AppDomain?displayProperty=nameWithType> managé n’a pas été construit pour ce domaine d’application, `S_FALSE` la méthode `NULL` retourne `*ppObject`et place dans.</span><span class="sxs-lookup"><span data-stu-id="58e50-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58e50-109">Notes </span><span class="sxs-lookup"><span data-stu-id="58e50-109">Remarks</span></span>  
 <span data-ttu-id="58e50-110">Chaque domaine d’application dans un processus peut avoir un <xref:System.AppDomain?displayProperty=nameWithType> objet managé dans le runtime qui le représente.</span><span class="sxs-lookup"><span data-stu-id="58e50-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="58e50-111">Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet <xref:System.AppDomain?displayProperty=nameWithType> objet managé.</span><span class="sxs-lookup"><span data-stu-id="58e50-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e50-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="58e50-112">Requirements</span></span>  
 <span data-ttu-id="58e50-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58e50-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e50-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58e50-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58e50-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58e50-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58e50-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e50-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
