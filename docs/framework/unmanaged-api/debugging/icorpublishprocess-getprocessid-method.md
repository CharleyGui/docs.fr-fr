---
title: ICorPublishProcess::GetProcessID, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 4cc6bbde2c7367c1109ca73e66f2670a56b2cdbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790556"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="bf6cb-102">ICorPublishProcess::GetProcessID, méthode</span><span class="sxs-lookup"><span data-stu-id="bf6cb-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="bf6cb-103">Obtient l’identificateur de système d’exploitation pour ce processus.</span><span class="sxs-lookup"><span data-stu-id="bf6cb-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf6cb-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="bf6cb-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="bf6cb-106">à Pointeur vers l’identificateur du processus représenté par cet objet [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bf6cb-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6cb-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="bf6cb-107">Requirements</span></span>  
 <span data-ttu-id="bf6cb-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6cb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6cb-109">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bf6cb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bf6cb-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf6cb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf6cb-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6cb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf6cb-112">See also</span></span>

- [<span data-ttu-id="bf6cb-113">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="bf6cb-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
