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
ms.openlocfilehash: 4f9818137016dc3e0522ed516c52df2550ffdfca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212514"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="3bdfa-102">ICorDebugModule::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="3bdfa-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="3bdfa-103">Obtient la taille, en octets, du module.</span><span class="sxs-lookup"><span data-stu-id="3bdfa-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bdfa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bdfa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bdfa-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="3bdfa-106">à Taille du module en octets.</span><span class="sxs-lookup"><span data-stu-id="3bdfa-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="3bdfa-107">Si le module a été généré à partir du générateur d’images natives (NGen. exe), la taille du module sera égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="3bdfa-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdfa-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3bdfa-108">Requirements</span></span>  
 <span data-ttu-id="3bdfa-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bdfa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bdfa-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bdfa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bdfa-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bdfa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bdfa-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bdfa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
