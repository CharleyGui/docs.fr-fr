---
title: 'ICorDebugVariableHome :: GetLocationType, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 8874deede8b46b93df0e298fb3970fa153b51415
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396572"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="ba6fe-102">ICorDebugVariableHome :: GetLocationType, méthode</span><span class="sxs-lookup"><span data-stu-id="ba6fe-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="ba6fe-103">Obtient le type de l’emplacement natif de la variable.</span><span class="sxs-lookup"><span data-stu-id="ba6fe-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba6fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba6fe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba6fe-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="ba6fe-106">à Pointeur vers le type de l’emplacement natif de la variable.</span><span class="sxs-lookup"><span data-stu-id="ba6fe-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="ba6fe-107">Pour plus d’informations, consultez l’énumération [VariableLocationType](variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ba6fe-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba6fe-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba6fe-108">Requirements</span></span>  
 <span data-ttu-id="ba6fe-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba6fe-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba6fe-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba6fe-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba6fe-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba6fe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba6fe-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba6fe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6fe-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba6fe-113">See also</span></span>

- [<span data-ttu-id="ba6fe-114">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="ba6fe-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="ba6fe-115">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="ba6fe-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
