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
ms.openlocfilehash: 2cd2238ac67713564922be440ce64a2ebc4bbf44
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396335"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="bf9da-102">ICorPublish::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="bf9da-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="bf9da-103">Obtient une instance de [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf9da-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf9da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf9da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf9da-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="bf9da-106">dans Identificateur du processus.</span><span class="sxs-lookup"><span data-stu-id="bf9da-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="bf9da-107">à Pointeur vers l’adresse d’une `ICorPublishProcess` instance de qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="bf9da-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9da-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bf9da-108">Remarks</span></span>  
 <span data-ttu-id="bf9da-109">`GetProcess`échoue si le processus n’existe pas ou s’il ne s’agit pas d’un processus managé pouvant être débogué par l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bf9da-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf9da-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf9da-110">Requirements</span></span>  
 <span data-ttu-id="bf9da-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9da-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bf9da-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bf9da-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf9da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf9da-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9da-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf9da-115">See also</span></span>

- [<span data-ttu-id="bf9da-116">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="bf9da-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
