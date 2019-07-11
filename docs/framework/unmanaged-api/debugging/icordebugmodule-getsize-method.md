---
title: ICorDebugModule::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ee21a9fd7b9267672a14107c1706af5d5cdcc5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763568"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="7fa33-102">ICorDebugModule::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="7fa33-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="7fa33-103">Obtient la taille, en octets, du module.</span><span class="sxs-lookup"><span data-stu-id="7fa33-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa33-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fa33-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7fa33-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="7fa33-106">[out] La taille du module en octets.</span><span class="sxs-lookup"><span data-stu-id="7fa33-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="7fa33-107">Si le module a été créé à partir du Générateur d’images natives (NGen.exe), la taille du module sera égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="7fa33-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fa33-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7fa33-108">Requirements</span></span>  
 <span data-ttu-id="7fa33-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa33-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa33-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fa33-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fa33-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fa33-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fa33-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fa33-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
