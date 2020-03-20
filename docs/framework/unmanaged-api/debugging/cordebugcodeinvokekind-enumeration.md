---
title: CorDebugCodeInvokeKind, énumération
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179262"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind, énumération
Indique de quelle manière une fonction exportée appelle du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Si du code managé est appelé par cette méthode, il devra ensuite être localisé par des événements ou des points d'arrêt explicites.<br /><br /> – ou –<br /><br /> Une partie du code managé appelé par cette méthode risque d'être oubliée, car il n'existe pas de moyen simple d'arrêter son exécution.<br /><br /> – ou –<br /><br /> La méthode risque de ne jamais appeler le code managé.|  
|`CODE_INVOKE_KIND_RETURN`|Cette méthode appelle le code managé via une instruction de retour. Le pas à pas sortant doit normalement se produire dans le code managé suivant.|  
|`CODE_INVOKE_KIND_TAILCALL`|Cette méthode appelle le code managé via un appel tail. Le pas à pas détaillé et le pas à pas principal sur des instructions d'appel doivent normalement se produire dans le code managé.|  
  
## <a name="remarks"></a>Notes   
 Cette énumération est utilisée par la méthode [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) pour fournir des informations sur le passage du code géré.  
  
> [!NOTE]
> Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)
