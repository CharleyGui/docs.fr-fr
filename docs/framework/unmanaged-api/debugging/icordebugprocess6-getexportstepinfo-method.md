---
title: ICorDebugProcess6::GetExportStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178530"
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
 [out] Un pointeur à un membre du [coscétation CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) qui décrit comment la fonction exportée invoquera le code géré.  
  
 invokePurpose  
 [out] Un pointeur à un membre du [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) énumération qui décrit pourquoi la fonction exportée appellera le code géré.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode peut retourner les valeurs répertoriées dans le tableau suivant.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|`S_OK`|L'appel de méthode a réussi.|  
|`E_POINTER`|`pInvokeKind`ou `pInvokePurpose` est **nul**.|  
|Autres valeurs `HRESULT` indiquant un échec.|Selon le cas|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](icordebugprocess6-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
