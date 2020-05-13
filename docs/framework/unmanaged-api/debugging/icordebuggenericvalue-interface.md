---
title: ICorDebugGenericValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209784"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue, interface

Sous-classe de « ICorDebugValue » qui s’applique à toutes les valeurs. Cette interface fournit les méthodes Get et Set pour la valeur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetValue, méthode](icordebuggenericvalue-getvalue-method.md)|Copie la valeur dans la mémoire tampon spécifiée.|  
|[Méthode SetValue](icordebuggenericvalue-setvalue-method.md)|Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugGenericValue`est une sous-interface, car elle n’est pas accessible à distance.  
  
 Pour les types référence, la valeur est la référence plutôt que le contenu de la référence.  
  
 Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
