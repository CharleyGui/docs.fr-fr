---
title: Méthode ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784558"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>Méthode ICorDebugAssembly3::EnumerateContainedAssemblies
Obtient un énumérateur pour les assemblys contenus dans cet assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppAssemblies`  
 [out] Pointeur vers l'adresse d'un objet d'interface ICorDebugAssemblyEnum qui est l'énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si cet objet `ICorDebugAssembly3` est un conteneur ; sinon, `S_FALSE`, et l'énumération est vide.  
  
## <a name="remarks"></a>Notes  
 Des symboles doivent être utilisés pour énumérer les assemblys contenus dans l'assembly. S'ils ne sont pas présents, la méthode retourne `S_FALSE`, et aucun énumérateur valide n'est fourni.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAssembly3, interface](icordebugassembly3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
