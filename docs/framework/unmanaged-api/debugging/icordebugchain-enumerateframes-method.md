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
ms.openlocfilehash: ae6d81e6fdab0f8e3346d8a08a3b5ebc329a542a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730147"
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
 à Pointeur vers l’adresse d’un objet ICorDebugFrameEnum qui est l’énumérateur des frames de pile.  
  
## <a name="remarks"></a>Remarques  

 La chaîne représente la pile d’appels physique du thread.  
  
 La `EnumerateFrames` méthode doit être appelée uniquement pour les chaînes managées. L’API de débogage ne fournit pas de méthodes permettant d’obtenir des frames contenus dans des chaînes non managées. Le débogueur doit utiliser d’autres moyens pour obtenir ces informations.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
