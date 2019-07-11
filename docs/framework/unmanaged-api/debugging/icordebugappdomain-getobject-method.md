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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1201ac0dca9cbd48c24b2621eba079ae672fd310
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737845"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="83dbf-102">ICorDebugAppDomain::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="83dbf-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="83dbf-103">Obtient un pointeur d’interface vers le domaine d’application du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="83dbf-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83dbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83dbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83dbf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83dbf-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="83dbf-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le domaine d’application CLR.</span><span class="sxs-lookup"><span data-stu-id="83dbf-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83dbf-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83dbf-107">Return Value</span></span>  
 <span data-ttu-id="83dbf-108">Si un géré <xref:System.AppDomain?displayProperty=nameWithType> objet n’a pas été construit pour ce domaine d’application, la méthode retourne `S_FALSE` et place `NULL` dans `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="83dbf-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83dbf-109">Notes</span><span class="sxs-lookup"><span data-stu-id="83dbf-109">Remarks</span></span>  
 <span data-ttu-id="83dbf-110">Chaque domaine d’application dans un processus peut avoir un géré <xref:System.AppDomain?displayProperty=nameWithType> objet dans le runtime qui le représente.</span><span class="sxs-lookup"><span data-stu-id="83dbf-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="83dbf-111">Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet gérés <xref:System.AppDomain?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="83dbf-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83dbf-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="83dbf-112">Requirements</span></span>  
 <span data-ttu-id="83dbf-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83dbf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83dbf-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83dbf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83dbf-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83dbf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83dbf-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83dbf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
