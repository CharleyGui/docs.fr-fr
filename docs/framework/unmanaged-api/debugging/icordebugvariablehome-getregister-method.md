---
title: 'ICorDebugVariableHome :: GetRegister, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396831"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome :: GetRegister, méthode
Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pRegister`  
 à Valeur d’énumération CorDebugRegister qui indique le registre d’une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne les valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La variable se trouve dans le registre indiqué par l' `pRegister` argument.|  
|`E_FAIL`|La variable n’est pas dans un registre ou un emplacement relatif à un registre.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [VariableLocationType, énumération](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
