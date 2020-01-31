---
title: CreateCordbObject, fonction
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
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793858"
---
# <a name="createcordbobject-function"></a>CreateCordbObject, fonction
Crée une interface de débogueur[ICorDebug](icordebug-interface.md)qui fournit des fonctionnalités pour instancier une session de débogage managée sur un processus distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `iDebuggerVersion`  
 [in] Version de débogage du processus cible. Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.  
  
 `ppCordb`  
 à Pointeur vers un pointeur vers un objet qui sera casté en interface [ICorDebug](icordebug-interface.md) et retourné.  
  
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
 L’interface [ICorDebug](icordebug-interface.md) qui est retournée dans `ppCordb` est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86. dll  
  
 **Versions de .NET Framework :** 3,5 SP1
