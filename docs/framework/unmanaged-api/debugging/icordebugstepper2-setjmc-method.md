---
title: ICorDebugStepper2::SetJMC, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 6c076dd2912a22e4f9492492a2d7a9fb73db88e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139038"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="b0d17-102">ICorDebugStepper2::SetJMC, méthode</span><span class="sxs-lookup"><span data-stu-id="b0d17-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="b0d17-103">Définit une valeur qui spécifie si cet effectue des étapes uniquement par le biais du code créé par le développeur d’une application.</span><span class="sxs-lookup"><span data-stu-id="b0d17-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="b0d17-104">Ce processus est également appelé débogage uniquement mon code (uniquement mon code).</span><span class="sxs-lookup"><span data-stu-id="b0d17-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0d17-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0d17-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0d17-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="b0d17-107">dans Affectez la valeur `true` pour effectuer un pas à pas détaillé dans le code créé par le développeur d’une application ; Sinon, affectez la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="b0d17-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0d17-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="b0d17-108">Requirements</span></span>  
 <span data-ttu-id="b0d17-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0d17-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0d17-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0d17-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0d17-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0d17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0d17-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0d17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
