---
title: Fonction CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ab86277956469e558d20cea81174a7fdcc0020b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739324"
---
# <a name="createcordbobject-function"></a>Fonction CreateCordbObject
Crée une interface de débogueur ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) qui fournit des fonctionnalités d’instanciation d’une session de débogage managée sur un processus distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iDebuggerVersion`  
 [in] Version de débogage du processus cible. Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.  
  
 `ppCordb`  
 [out] Pointeur vers un pointeur vers un objet qui sera être casté en un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface et retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.  
  
 E_INVALIDARG  
 `ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppCordb`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Notes  
 Le [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface retournée dans `ppCordb` est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces.h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions du .NET framework :** 3.5 SP1
