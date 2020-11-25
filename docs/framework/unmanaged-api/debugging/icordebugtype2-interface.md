---
title: ICorDebugType2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0d5fffe4350cc1f58acf588f288db3bdb7e213d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725666"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2, interface

Étend l’interface ICorDebugType pour récupérer l’identificateur de type d’un type de base ou un type complexe (défini par l’utilisateur).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode||  
|------------|-|  
|[GetTypeID, méthode](icordebugtype2-gettypeid-method.md)|Obtient une [COR_TYPEID](cor-typeid-structure.md) pour ce type.|  
  
## <a name="remarks"></a>Remarques  

 Cette interface est une extension logique de l’interface ICorDebugType.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="example"></a>Exemple  

 Le fragment de code suivant illustre l’utilisation de la méthode [méthode icordebugtype2 :: GetTypeID](icordebugtype2-gettypeid-method.md) .  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
