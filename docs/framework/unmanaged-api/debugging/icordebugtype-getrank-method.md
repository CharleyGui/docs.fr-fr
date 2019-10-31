---
title: ICorDebugType::GetRank, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
ms.openlocfilehash: 9a00177faabfcad56d70ec5c64328c90675c1532
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138759"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="fa76a-102">ICorDebugType::GetRank, méthode</span><span class="sxs-lookup"><span data-stu-id="fa76a-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="fa76a-103">Obtient le nombre de dimensions dans un type de tableau.</span><span class="sxs-lookup"><span data-stu-id="fa76a-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa76a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa76a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa76a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa76a-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="fa76a-106">à Pointeur vers le nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="fa76a-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa76a-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="fa76a-107">Requirements</span></span>  
 <span data-ttu-id="fa76a-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa76a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa76a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa76a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa76a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa76a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa76a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa76a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
