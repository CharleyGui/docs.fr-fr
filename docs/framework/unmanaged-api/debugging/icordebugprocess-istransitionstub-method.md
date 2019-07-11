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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec29aa748c437199434fa1394e1a00c82154447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766878"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub, méthode
Obtient une valeur qui indique si une adresse est à l’intérieur d’un stub qui provoquera une transition vers du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 [in] Un `CORDB_ADDRESS` valeur qui spécifie l’adresse en question.  
  
 `pbTransitionStub`  
 [out] Un pointeur vers une valeur booléenne qui est `true` si l’adresse spécifiée est à l’intérieur d’un stub qui provoquera une transition vers du code managé ; sinon *`pbTransitionStub` est `false`.  
  
## <a name="remarks"></a>Notes  
 Le `IsTransitionStub` méthode peut être utilisée par le code pas à pas non managé pour décider du moment auquel le retourner le pas à pas de contrôle à l’exécution pas à pas géré.  
  
 Vous pouvez également les stubs de transition identité en examinant les informations contenues dans le fichier exécutable portable (PE).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
