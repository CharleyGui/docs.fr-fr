---
title: ICorDebugAssembly3, interface
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894827"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3, interface
Étend logiquement l'interface ICorDebugAssembly pour prendre en charge les assemblys conteneurs et les assemblys qu'ils contiennent.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateContainedAssemblies, méthode](icordebugassembly3-enumeratecontainedassemblies-method.md)|Obtient un énumérateur pour les assemblys contenus dans cet assembly.|  
|[GetContainerAssembly, méthode](icordebugassembly3-getcontainerassembly-method.md)|Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> L'interface est uniquement disponible avec .NET Native. Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
