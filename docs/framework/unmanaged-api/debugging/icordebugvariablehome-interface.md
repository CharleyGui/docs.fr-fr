---
title: ICorDebugVariableHome, interface
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: c347346c9157fea843527c662e26ffcfba22ace4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790955"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome, interface
Représente une variable locale ou un argument d’une fonction.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetArgumentIndex, méthode](icordebugvariablehome-getargumentindex-method.md)|Obtient l’index d’un argument de fonction.|  
|[GetCode, méthode](icordebugvariablehome-getcode-method.md)|Obtient l’instance « ICorDebugCode » qui contient cet objet `ICorDebugVariableHome`.|  
|[GetLiveRange, méthode](icordebugvariablehome-getliverange-method.md)|Obtient la plage native sur laquelle cette variable est active.|  
|[GetLocationType, méthode](icordebugvariablehome-getlocationtype-method.md)|Obtient le type de l’emplacement natif de la variable.|  
|[GetOffset, méthode](icordebugvariablehome-getoffset-method.md)|Obtient le décalage à partir du registre de base pour une variable.|  
|[GetRegister, méthode](icordebugvariablehome-getregister-method.md)|Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER`et le registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.|  
|[GetSlotIndex, méthode](icordebugvariablehome-getslotindex-method.md)|Obtient l’index d’emplacement managé d’une variable locale.|  
  
## <a name="example"></a>Exemple  
 Le fragment de code suivant utilise l’objet [ICorDebugCode4](icordebugcode4-interface.md) nommé `pCode4`.  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [ICorDebugVariableHomeEnum, interface](icordebugvariablehomeenum-interface.md)
