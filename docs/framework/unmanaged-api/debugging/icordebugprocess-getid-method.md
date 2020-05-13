---
title: ICorDebugProcess::GetID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: 8cd40ffb60bf837a9aa3b0db34892350a05964d7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213281"
---
# <a name="icordebugprocessgetid-method"></a>ICorDebugProcess::GetID, méthode
Obtient l’ID (se) du système d’exploitation du processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwProcessId`  
 à ID unique du processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
