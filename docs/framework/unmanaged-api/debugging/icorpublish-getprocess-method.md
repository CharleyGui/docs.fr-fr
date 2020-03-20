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
ms.openlocfilehash: 46f047dbec7ff008873540806b76ffe7085086b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178421"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="c7385-102">ICorPublish::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="c7385-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="c7385-103">Obtient une instance [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identifiant spécifié.</span><span class="sxs-lookup"><span data-stu-id="c7385-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7385-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7385-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7385-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7385-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="c7385-106">[dans] L’identifiant du processus.</span><span class="sxs-lookup"><span data-stu-id="c7385-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c7385-107">[out] Un pointeur à `ICorPublishProcess` l’adresse d’une instance qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="c7385-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7385-108">Notes </span><span class="sxs-lookup"><span data-stu-id="c7385-108">Remarks</span></span>  
 <span data-ttu-id="c7385-109">`GetProcess`échoue si le processus n’existe pas, ou n’est pas un processus géré qui peut être débogé par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c7385-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7385-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7385-110">Requirements</span></span>  
 <span data-ttu-id="c7385-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7385-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7385-112">**En-tête:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c7385-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c7385-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7385-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7385-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7385-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7385-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7385-115">See also</span></span>

- [<span data-ttu-id="c7385-116">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="c7385-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
