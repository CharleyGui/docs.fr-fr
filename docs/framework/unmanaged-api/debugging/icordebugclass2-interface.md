---
title: ICorDebugClass2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ff15297eb479f7474c9f07123a29263fb4da3205
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893974"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2, interface

Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>. Cette interface étend [ICorDebugClass](icordebugclass-interface.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetParameterizedType, méthode](icordebugclass2-getparameterizedtype-method.md)|Obtient la déclaration de type pour cette classe.|  
|[SetJMCStatus, méthode](icordebugclass2-setjmcstatus-method.md)|Pour chaque méthode de cette classe, définit une valeur qui indique si la méthode est du code défini par l’utilisateur.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugClass, interface](icordebugclass-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
