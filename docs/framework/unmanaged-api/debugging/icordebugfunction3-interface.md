---
title: ICorDebugFunction3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213164"
---
# <a name="icordebugfunction3-interface"></a>ICorDebugFunction3, interface
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Étend logiquement l’interface ICorDebugFunction pour fournir un accès au code d’une demande ReJIT.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode, méthode](icordebugfunction3-getactiverejitrequestilcode-method.md)|Obtient un pointeur d’interface vers un [ICorDebugILCode](icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
- [ReJIT : Guide pratique](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
