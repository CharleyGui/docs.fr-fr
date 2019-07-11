---
title: ICorDebugChain::EnumerateFrames, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc647805fcb7d8354a2540ac9424dc7155853444
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745038"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames, méthode
Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppFrames`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugFrameEnum qui est l’énumérateur pour les frames de pile.  
  
## <a name="remarks"></a>Notes  
 La chaîne représente la pile des appels physique pour le thread.  
  
 Le `EnumerateFrames` méthode doit être appelée uniquement pour les chaînes managées. L’API de débogage ne fournit pas de méthodes pour obtenir des images contenues dans les chaînes non managées. Le débogueur doit utiliser d’autres moyens d’obtenir ces informations.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
