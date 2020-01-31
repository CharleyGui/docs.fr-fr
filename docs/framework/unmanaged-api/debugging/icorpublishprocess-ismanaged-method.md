---
title: ICorPublishProcess::IsManaged, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790524"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="d7fab-102">ICorPublishProcess::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="d7fab-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="d7fab-103">Obtient une valeur qui indique si le processus référencé par ce [ICorPublishProcess](icorpublishprocess-interface.md) est connu pour avoir du code managé.</span><span class="sxs-lookup"><span data-stu-id="d7fab-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7fab-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7fab-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d7fab-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="d7fab-106">à Pointeur vers une valeur booléenne qui indique si le processus a du code managé.</span><span class="sxs-lookup"><span data-stu-id="d7fab-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="d7fab-107">La valeur est `true` si le processus a du code managé ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d7fab-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7fab-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d7fab-108">Remarks</span></span>  
 <span data-ttu-id="d7fab-109">Étant donné que la version actuelle de `ICorPublishProcess` autorise l’accès uniquement aux processus qui ont du code managé, `IsManaged` retourne toujours `true`.</span><span class="sxs-lookup"><span data-stu-id="d7fab-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7fab-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d7fab-110">Requirements</span></span>  
 <span data-ttu-id="d7fab-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7fab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7fab-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d7fab-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d7fab-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7fab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7fab-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7fab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fab-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7fab-115">See also</span></span>

- [<span data-ttu-id="d7fab-116">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="d7fab-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
