---
title: ICorPublish::EnumProcesses, méthode
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121793"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="fa669-102">ICorPublish::EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="fa669-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="fa669-103">Obtient un énumérateur pour les processus managés qui s’exécutent sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa669-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa669-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa669-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa669-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa669-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="fa669-106">Valeur de l’énumération [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) qui spécifie le type de processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fa669-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="fa669-107">Dans la version actuelle, seul COR_PUB_MANAGEDONLY est valide.</span><span class="sxs-lookup"><span data-stu-id="fa669-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="fa669-108">Pointeur vers l’adresse d’une instance [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) qui est l’énumérateur des processus.</span><span class="sxs-lookup"><span data-stu-id="fa669-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa669-109">Notes</span><span class="sxs-lookup"><span data-stu-id="fa669-109">Remarks</span></span>  
 <span data-ttu-id="fa669-110">La collection de processus de l’énumérateur est basée sur un instantané des processus en cours d’exécution lorsque la méthode `EnumProcesses` est appelée.</span><span class="sxs-lookup"><span data-stu-id="fa669-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="fa669-111">L’énumérateur n’inclut pas les processus qui se terminent avant ou commencent après l’appel de `EnumProcesses`.</span><span class="sxs-lookup"><span data-stu-id="fa669-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="fa669-112">La méthode `EnumProcesses` peut être appelée plusieurs fois sur cette instance [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) pour créer une nouvelle collection à jour de processus.</span><span class="sxs-lookup"><span data-stu-id="fa669-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="fa669-113">Les collections existantes ne seront pas affectées par les appels ultérieurs de la méthode `EnumProcesses`.</span><span class="sxs-lookup"><span data-stu-id="fa669-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa669-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="fa669-114">Requirements</span></span>  
 <span data-ttu-id="fa669-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa669-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa669-116">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="fa669-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fa669-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa669-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa669-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa669-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa669-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa669-119">See also</span></span>

- [<span data-ttu-id="fa669-120">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="fa669-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
