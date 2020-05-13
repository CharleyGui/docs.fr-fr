---
title: ICorDebugThread::GetActiveChain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379693"
---
# <a name="icordebugthreadgetactivechain-method"></a>ICorDebugThread::GetActiveChain, méthode
Obtient un pointeur d’interface vers la chaîne de pile active (la plus récente) sur cet objet ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppChain`  
 à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne de pile.  
  
## <a name="remarks"></a>Remarks  
 Le `ppChain` paramètre a la valeur null si aucune chaîne de pile n’est actuellement active.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
