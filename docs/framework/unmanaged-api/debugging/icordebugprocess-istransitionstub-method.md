---
title: ICorDebugProcess::IsTransitionStub, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 2996c219ccf4e975c45fb531807abc4a608bae73
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694774"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub, méthode

Obtient une valeur qui indique si une adresse se trouve à l’intérieur d’un stub qui entraîne une transition vers du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Paramètres  

 `address`  
 dans `CORDB_ADDRESS` Valeur qui spécifie l’adresse en question.  
  
 `pbTransitionStub`  
 à Pointeur vers une valeur booléenne qui est `true` si l’adresse spécifiée se trouve à l’intérieur d’un stub qui provoque une transition vers du code managé ; sinon, * `pbTransitionStub` est `false` .  
  
## <a name="remarks"></a>Remarques  

 La `IsTransitionStub` méthode peut être utilisée par le code d’exécution non managé pour décider quand retourner le contrôle pas à pas à l’exécution pas à pas managée.  
  
 Vous pouvez également identifier des stubs de transition en examinant les informations contenues dans le fichier exécutable portable (PE).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
