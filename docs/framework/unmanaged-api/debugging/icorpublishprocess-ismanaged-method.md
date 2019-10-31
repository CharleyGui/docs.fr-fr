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
ms.openlocfilehash: ad3a357a98cb5ed28a34e4076b5e145903ceaf91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103497"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="bcce6-102">ICorPublishProcess::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="bcce6-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="bcce6-103">Obtient une valeur qui indique si le processus référencé par ce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) est connu pour avoir du code managé.</span><span class="sxs-lookup"><span data-stu-id="bcce6-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcce6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcce6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcce6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcce6-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="bcce6-106">à Pointeur vers une valeur booléenne qui indique si le processus a du code managé.</span><span class="sxs-lookup"><span data-stu-id="bcce6-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="bcce6-107">La valeur est `true` si le processus a du code managé ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="bcce6-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcce6-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bcce6-108">Remarks</span></span>  
 <span data-ttu-id="bcce6-109">Étant donné que la version actuelle de `ICorPublishProcess` autorise l’accès uniquement aux processus qui ont du code managé, `IsManaged` retourne toujours `true`.</span><span class="sxs-lookup"><span data-stu-id="bcce6-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcce6-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="bcce6-110">Requirements</span></span>  
 <span data-ttu-id="bcce6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcce6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcce6-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bcce6-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bcce6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcce6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcce6-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcce6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcce6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcce6-115">See also</span></span>

- [<span data-ttu-id="bcce6-116">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="bcce6-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
