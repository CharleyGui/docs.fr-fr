---
title: ICorDebugModule::EnableJITDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212930"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="2df98-102">ICorDebugModule::EnableJITDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="2df98-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="2df98-103">Contrôle si le compilateur juste-à-temps (JIT) préserve les informations de débogage pour les méthodes dans ce module.</span><span class="sxs-lookup"><span data-stu-id="2df98-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2df98-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2df98-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2df98-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="2df98-106">dans Définissez cette valeur sur `true` pour permettre au compilateur JIT de conserver les informations de mappage entre la version du langage MSIL (Microsoft Intermediate Language) et la version compilée juste-à-temps de chaque méthode de ce module.</span><span class="sxs-lookup"><span data-stu-id="2df98-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="2df98-107">dans Définissez cette valeur sur `true` pour permettre au compilateur JIT de générer du code avec certaines optimisations spécifiques au JIT pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="2df98-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df98-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="2df98-108">Remarks</span></span>  
 <span data-ttu-id="2df98-109">Le débogage juste-à-temps est activé par défaut pour tous les modules qui sont chargés lorsque le débogueur est actif.</span><span class="sxs-lookup"><span data-stu-id="2df98-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="2df98-110">L’activation ou la désactivation par programmation des paramètres remplace les paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="2df98-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df98-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2df98-111">Requirements</span></span>  
 <span data-ttu-id="2df98-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df98-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df98-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2df98-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2df98-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df98-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df98-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
