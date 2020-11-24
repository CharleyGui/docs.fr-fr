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
ms.openlocfilehash: a163667ea7eca1ed817d642efdb8fc4efa2a0651
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676060"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="fcbcb-102">ICorDebugAppDomain::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="fcbcb-102">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="fcbcb-103">Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fcbcb-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcbcb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcbcb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcbcb-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="fcbcb-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le domaine d’application CLR.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcbcb-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="fcbcb-107">Return Value</span></span>  

 <span data-ttu-id="fcbcb-108">Si un <xref:System.AppDomain?displayProperty=nameWithType> objet managé n’a pas été construit pour ce domaine d’application, la méthode retourne `S_FALSE` et place `NULL` dans `*ppObject` .</span><span class="sxs-lookup"><span data-stu-id="fcbcb-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcbcb-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="fcbcb-109">Remarks</span></span>  

 <span data-ttu-id="fcbcb-110">Chaque domaine d’application dans un processus peut avoir un <xref:System.AppDomain?displayProperty=nameWithType> objet managé dans le runtime qui le représente.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="fcbcb-111">Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet <xref:System.AppDomain?displayProperty=nameWithType> objet managé.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbcb-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fcbcb-112">Requirements</span></span>  

 <span data-ttu-id="fcbcb-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbcb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbcb-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcbcb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcbcb-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcbcb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcbcb-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbcb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
