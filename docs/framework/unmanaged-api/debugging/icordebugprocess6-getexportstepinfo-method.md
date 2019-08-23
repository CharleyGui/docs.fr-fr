---
title: ICorDebugProcess6::GetExportStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18af0dde2d1acc65003558a04789de027bb9209f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967399"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo, méthode
Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Paramètres  
 pszExportName  
 [in] Nom d'une fonction exportée du runtime tel qu'écrit dans la table d'exportation PE.  
  
 invokeKind  
 à Pointeur vers un membre de l’énumération [cordebugcodeinvokekind,](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) qui décrit comment la fonction exportée appellera le code managé.  
  
 invokePurpose  
 à Pointeur vers un membre de l’énumération [cordebugcodeinvokepurpose,](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) qui décrit la raison pour laquelle la fonction exportée appellera du code managé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode peut retourner les valeurs répertoriées dans le tableau suivant.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`S_OK`|L'appel de méthode a réussi.|  
|`E_POINTER`|`pInvokeKind`ou `pInvokePurpose` a la **valeur null**.|  
|Autres valeurs `HRESULT` indiquant un échec.|Selon le cas|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
