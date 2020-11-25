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
ms.openlocfilehash: eccdfcb60b2d2b5d652ccac948c01c16e7cb828d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725974"
---
# <a name="createcordbobject-function"></a>Fonction CreateCordbObject

Crée une interface de débogueur[ICorDebug](icordebug-interface.md)qui fournit des fonctionnalités pour instancier une session de débogage managée sur un processus distant.  
  
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
 à Pointeur vers un pointeur vers un objet qui sera casté en interface [ICorDebug](icordebug-interface.md) et retourné.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK  
 Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.  
  
 E_INVALIDARG  
 `ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppCordb`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Remarques  

 L’interface [ICorDebug](icordebug-interface.md) qui est retournée dans `ppCordb` est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces. h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions de .NET Framework :** 3,5 SP1
