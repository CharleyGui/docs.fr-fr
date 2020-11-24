---
title: ICorDebugEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 28e0cded33b49e3aadc0564bae3a60bee76c4396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677385"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="05876-102">ICorDebugEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="05876-102">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="05876-103">Crée une copie de cet objet ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="05876-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05876-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05876-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05876-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05876-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="05876-106">à Pointeur vers l’adresse d’un `ICorDebugEnum` objet qui est une copie de cet `ICorDebugEnum` objet.</span><span class="sxs-lookup"><span data-stu-id="05876-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05876-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05876-107">Requirements</span></span>  

 <span data-ttu-id="05876-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05876-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05876-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05876-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05876-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05876-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05876-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05876-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
