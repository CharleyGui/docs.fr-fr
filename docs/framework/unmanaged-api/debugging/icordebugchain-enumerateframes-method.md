---
title: ICorDebugChain::EnumerateFrames, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: c8a62d8b4a4db0f36d991c32dbfc5bad68780f1b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894694"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="04111-102">ICorDebugChain::EnumerateFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="04111-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="04111-103">Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.</span><span class="sxs-lookup"><span data-stu-id="04111-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04111-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04111-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04111-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04111-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="04111-106">à Pointeur vers l’adresse d’un objet ICorDebugFrameEnum qui est l’énumérateur des frames de pile.</span><span class="sxs-lookup"><span data-stu-id="04111-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04111-107">Notes </span><span class="sxs-lookup"><span data-stu-id="04111-107">Remarks</span></span>  
 <span data-ttu-id="04111-108">La chaîne représente la pile d’appels physique du thread.</span><span class="sxs-lookup"><span data-stu-id="04111-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="04111-109">La `EnumerateFrames` méthode doit être appelée uniquement pour les chaînes managées.</span><span class="sxs-lookup"><span data-stu-id="04111-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="04111-110">L’API de débogage ne fournit pas de méthodes permettant d’obtenir des frames contenus dans des chaînes non managées.</span><span class="sxs-lookup"><span data-stu-id="04111-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="04111-111">Le débogueur doit utiliser d’autres moyens pour obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="04111-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04111-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04111-112">Requirements</span></span>  
 <span data-ttu-id="04111-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04111-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04111-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04111-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04111-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04111-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04111-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04111-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
