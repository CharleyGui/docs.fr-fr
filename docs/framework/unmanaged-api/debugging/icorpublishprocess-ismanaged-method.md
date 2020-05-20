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
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421096"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="29637-102">ICorPublishProcess::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="29637-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="29637-103">Obtient une valeur qui indique si le processus référencé par ce [ICorPublishProcess](icorpublishprocess-interface.md) est connu pour avoir du code managé.</span><span class="sxs-lookup"><span data-stu-id="29637-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29637-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29637-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29637-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29637-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="29637-106">à Pointeur vers une valeur booléenne qui indique si le processus a du code managé.</span><span class="sxs-lookup"><span data-stu-id="29637-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="29637-107">La valeur est `true` si le processus a du code managé ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="29637-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29637-108">Notes</span><span class="sxs-lookup"><span data-stu-id="29637-108">Remarks</span></span>  
 <span data-ttu-id="29637-109">Étant donné que la version actuelle de `ICorPublishProcess` autorise l’accès uniquement aux processus qui ont du code managé, `IsManaged` retourne toujours `true` .</span><span class="sxs-lookup"><span data-stu-id="29637-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29637-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="29637-110">Requirements</span></span>  
 <span data-ttu-id="29637-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29637-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29637-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="29637-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29637-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29637-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29637-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29637-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29637-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29637-115">See also</span></span>

- [<span data-ttu-id="29637-116">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="29637-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
