---
title: ICorDebugAppDomain::EnumerateAssemblies, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
ms.openlocfilehash: 386913f8c81ff3c8b98bb0cab4ffc101a4f6085f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723322"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="fb207-102">ICorDebugAppDomain::EnumerateAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="fb207-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>

<span data-ttu-id="fb207-103">Obtient un énumérateur pour les assemblys dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="fb207-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb207-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb207-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb207-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb207-105">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="fb207-106">à Pointeur vers l’adresse d’un objet ICorDebugAssemblyEnum qui est l’énumérateur pour les assemblys dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="fb207-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb207-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fb207-107">Requirements</span></span>  

 <span data-ttu-id="fb207-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb207-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb207-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb207-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb207-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb207-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb207-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb207-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
