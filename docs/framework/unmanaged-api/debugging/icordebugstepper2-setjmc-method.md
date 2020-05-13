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
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379463"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="d74e2-102">ICorDebugStepper2::SetJMC, méthode</span><span class="sxs-lookup"><span data-stu-id="d74e2-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="d74e2-103">Définit une valeur qui spécifie si cet effectue des étapes uniquement par le biais du code créé par le développeur d’une application.</span><span class="sxs-lookup"><span data-stu-id="d74e2-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="d74e2-104">Ce processus est également appelé débogage uniquement mon code (uniquement mon code).</span><span class="sxs-lookup"><span data-stu-id="d74e2-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d74e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d74e2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d74e2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d74e2-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="d74e2-107">dans Affectez `true` la valeur pour effectuer un pas à pas détaillé dans le code créé par le développeur d’une application ; sinon, affectez à la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="d74e2-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74e2-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d74e2-108">Requirements</span></span>  
 <span data-ttu-id="d74e2-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d74e2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74e2-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d74e2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d74e2-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d74e2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d74e2-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d74e2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
