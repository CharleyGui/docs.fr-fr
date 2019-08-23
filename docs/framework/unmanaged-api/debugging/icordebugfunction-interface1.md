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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917203"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction, interface

Représente une fonction ou une méthode managée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Crée un point d’arrêt au début de cette fonction.|  
|[GetClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Obtient un objet ICorDebugClass qui représente la classe dont cette fonction est membre.|  
|[GetCurrentVersionNumber, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Obtient le numéro de version de la dernière modification apportée à cette fonction.|  
|[GetILCode, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Obtient le code MSIL (Microsoft Intermediate Language) pour cette fonction.|  
|[GetLocalVarSigToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Obtient le jeton de métadonnées pour la signature de variable locale de la fonction représentée par `ICorDebugFunction` cette instance.|  
|[GetModule, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Obtient le module dans lequel cette fonction est définie.|  
|[GetNativeCode, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Obtient le code natif pour cette fonction.|  
|[GetToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Obtient le jeton de métadonnées pour cette fonction.|  
  
## <a name="remarks"></a>Notes  
 L' `ICorDebugFunction` interface ne représente pas une fonction avec des paramètres de type générique. Par exemple, une `ICorDebugFunction` instance de représente `Func<T>` , mais `Func<string>`pas. Appelez [ICorDebugILFrame2:: EnumerateTypeParameters,](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) pour récupérer les paramètres de type générique.  
  
 La relation entre le jeton de métadonnées d' `mdMethodDef`une méthode,, et `ICorDebugFunction` l’objet d’une méthode dépend de l’autorisation de modifier & Continuer sur la fonction:  
  
- Si modifier & Continuer n’est pas autorisé sur la fonction, il existe une relation un-à-un `ICorDebugFunction` entre l’objet `mdMethodDef` et le jeton. Autrement dit, la fonction a un `ICorDebugFunction` objet et un `mdMethodDef` jeton.  
  
- Si modifier & Continuer est autorisé sur la fonction, il existe une relation plusieurs-à-un entre `ICorDebugFunction` l’objet et `mdMethodDef` le jeton. Autrement dit, la fonction peut avoir de nombreuses instances `ICorDebugFunction`de, une pour chaque version de la fonction, mais un `mdMethodDef` seul jeton.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque**  CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
