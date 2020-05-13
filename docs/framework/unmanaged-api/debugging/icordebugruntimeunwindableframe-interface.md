---
title: ICorDebugRuntimeUnwindableFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379389"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame, interface
Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugRuntimeUnwindableFrame`est une version spécialisée de l’interface ICorDebugFrame. Elle est utilisée par les méthodes non managées qui requièrent que le runtime déroule un frame sur la pile active. Les conventions de déroulement existantes ne fonctionnent pas, car elles n’utilisent pas de code compilé juste-à-temps. Quand le débogueur voit un frame déroulable, il doit utiliser la méthode [ICorDebugStackWalk :: Next](icordebugstackwalk-next-method.md) pour le dérouler, mais il doit effectuer l’inspection elle-même. Quand le débogueur reçoit un `ICorDebugRuntimeUnwindableFrame` , il peut appeler la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) pour récupérer le contexte du frame.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
