---
title: ICorDebugStepper::SetUnmappedStopMask, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ef458fda8e8b7e75f92a4b3c06eabec106180d23
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379259"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask, méthode
Définit une valeur qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mask`  
 dans Valeur de l’énumération CorDebugUnmappedStop, qui spécifie le type de code non mappé dans lequel le débogueur arrêtera l’exécution.  
  
 La valeur par défaut est STOP_OTHER_UNMAPPED. La valeur STOP_UNMANAGED est valide uniquement avec le débogage d’interopérabilité.  
  
## <a name="remarks"></a>Remarks  
 Quand le débogueur trouve une compilation juste-à-temps (JIT) qui n’a pas de mappage correspondant au langage MSIL (Microsoft Intermediate Language), il interrompt l’exécution si l’indicateur spécifiant ce type de code non mappé a été défini ; dans le cas contraire, l’exécution pas à pas se poursuit en toute transparence.  
  
 Si le débogueur n’utilise pas de pas à pas pour entrer dans une méthode, il n’effectuera pas nécessairement un pas à pas principal dans le code non mappé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
