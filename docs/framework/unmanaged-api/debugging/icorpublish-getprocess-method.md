---
title: ICorPublish::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: a9d28243e9907fcc6320b2e09a49312bf35a70b4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121787"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="359ce-102">ICorPublish::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="359ce-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="359ce-103">Obtient une instance de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="359ce-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="359ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="359ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="359ce-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="359ce-106">dans Identificateur du processus.</span><span class="sxs-lookup"><span data-stu-id="359ce-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="359ce-107">à Pointeur vers l’adresse d’une instance de `ICorPublishProcess` qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="359ce-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="359ce-108">Notes</span><span class="sxs-lookup"><span data-stu-id="359ce-108">Remarks</span></span>  
 <span data-ttu-id="359ce-109">`GetProcess` échoue si le processus n’existe pas ou s’il ne s’agit pas d’un processus géré pouvant être débogué par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="359ce-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359ce-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="359ce-110">Requirements</span></span>  
 <span data-ttu-id="359ce-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359ce-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359ce-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="359ce-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="359ce-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="359ce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="359ce-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359ce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359ce-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="359ce-115">See also</span></span>

- [<span data-ttu-id="359ce-116">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="359ce-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
