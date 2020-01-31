---
title: ICorDebugFunction, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794501"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction, interface

Représente une fonction ou une méthode managée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](icordebugfunction-createbreakpoint-method.md)|Crée un point d’arrêt au début de cette fonction.|  
|[GetClass, méthode](icordebugfunction-getclass-method.md)|Obtient un objet ICorDebugClass qui représente la classe dont cette fonction est membre.|  
|[GetCurrentVersionNumber, méthode](icordebugfunction-getcurrentversionnumber-method.md)|Obtient le numéro de version de la dernière modification apportée à cette fonction.|  
|[GetILCode, méthode](icordebugfunction-getilcode-method.md)|Obtient le code MSIL (Microsoft Intermediate Language) pour cette fonction.|  
|[GetLocalVarSigToken, méthode](icordebugfunction-getlocalvarsigtoken-method.md)|Obtient le jeton de métadonnées pour la signature de variable locale de la fonction représentée par cette `ICorDebugFunction` instance.|  
|[GetModule, méthode](icordebugfunction-getmodule-method.md)|Obtient le module dans lequel cette fonction est définie.|  
|[GetNativeCode, méthode](icordebugfunction-getnativecode-method.md)|Obtient le code natif pour cette fonction.|  
|[GetToken, méthode](icordebugfunction-gettoken-method.md)|Obtient le jeton de métadonnées pour cette fonction.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugFunction` ne représente pas une fonction avec des paramètres de type générique. Par exemple, une instance de `ICorDebugFunction` représente `Func<T>` mais pas `Func<string>`. Appelez [ICorDebugILFrame2 :: EnumerateTypeParameters,](icordebugilframe2-enumeratetypeparameters-method.md) pour récupérer les paramètres de type générique.  
  
 La relation entre le jeton de métadonnées d’une méthode, `mdMethodDef`et l’objet `ICorDebugFunction` d’une méthode dépend de l’autorisation de modifier & Continuer sur la fonction :  
  
- Si modifier & Continuer n’est pas autorisé sur la fonction, il existe une relation un-à-un entre l’objet `ICorDebugFunction` et le jeton `mdMethodDef`. Autrement dit, la fonction a un objet `ICorDebugFunction` et un jeton `mdMethodDef`.  
  
- Si modifier & Continuer est autorisé sur la fonction, il existe une relation plusieurs-à-un entre l’objet `ICorDebugFunction` et le jeton `mdMethodDef`. Autrement dit, la fonction peut avoir de nombreuses instances de `ICorDebugFunction`, une pour chaque version de la fonction, mais un seul jeton `mdMethodDef`.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :**  CorGuids. lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
