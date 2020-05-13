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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213237"
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
  
## <a name="remarks"></a>Remarks  
 L' `ICorDebugFunction` interface ne représente pas une fonction avec des paramètres de type générique. Par exemple, une `ICorDebugFunction` instance de représente, `Func<T>` mais pas `Func<string>` . Appelez [ICorDebugILFrame2 :: EnumerateTypeParameters,](icordebugilframe2-enumeratetypeparameters-method.md) pour récupérer les paramètres de type générique.  
  
 La relation entre le jeton de métadonnées d’une méthode, `mdMethodDef` , et l’objet d’une méthode `ICorDebugFunction` dépend de l’autorisation de modifier & Continuer sur la fonction :  
  
- Si modifier & Continuer n’est pas autorisé sur la fonction, il existe une relation un-à-un entre l' `ICorDebugFunction` objet et le `mdMethodDef` jeton. Autrement dit, la fonction a un `ICorDebugFunction` objet et un `mdMethodDef` jeton.  
  
- Si modifier & Continuer est autorisé sur la fonction, il existe une relation plusieurs-à-un entre l' `ICorDebugFunction` objet et le `mdMethodDef` jeton. Autrement dit, la fonction peut avoir de nombreuses instances de `ICorDebugFunction` , une pour chaque version de la fonction, mais un seul `mdMethodDef` jeton.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :**  CorGuids. lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
