---
title: ICorDebugFunction2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: 611091d39da6d7f646457457f20ce1eaf37db361
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213203"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2, interface

Étend logiquement l’interface ICorDebugFunction pour assurer la prise en charge de Uniquement mon code le débogage pas à pas, ce qui ignore le code non-utilisateur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateNativeCode, méthode](icordebugfunction2-enumeratenativecode-method.md)|(Pas encore implémenté.) Obtient un pointeur d’interface vers un ICorDebugCodeEnum qui contient les instructions de code natif dans la fonction référencée par cet objet ICorDebugFunction2.|  
|[GetJMCStatus, méthode](icordebugfunction2-getjmcstatus-method.md)|Obtient une valeur qui indique si cette fonction est marquée en tant que code utilisateur.|  
|[GetVersionNumber, méthode](icordebugfunction2-getversionnumber-method.md)|Obtient la version modifier & continuer de cette fonction.|  
|[SetJMCStatus, méthode](icordebugfunction2-setjmcstatus-method.md)|Marque cette fonction pour Uniquement mon code pas à pas.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
