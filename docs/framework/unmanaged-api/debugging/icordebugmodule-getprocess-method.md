---
title: ICorDebugModule::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
ms.openlocfilehash: 50722bb855c8bc8bcfdc1b405a5bbc2fa057c52c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129520"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="67a6c-102">ICorDebugModule::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="67a6c-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="67a6c-103">Obtient le processus conteneur de ce module.</span><span class="sxs-lookup"><span data-stu-id="67a6c-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67a6c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a6c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67a6c-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="67a6c-106">à Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus contenant ce module.</span><span class="sxs-lookup"><span data-stu-id="67a6c-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a6c-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="67a6c-107">Requirements</span></span>  
 <span data-ttu-id="67a6c-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a6c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a6c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67a6c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67a6c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67a6c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a6c-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a6c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
