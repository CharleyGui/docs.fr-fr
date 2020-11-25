---
title: ICorDebugFrame::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 0cfc734e3c2d250bba045a926f5b178b6cbc1ba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728197"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange, méthode

Obtient la plage d’adresses absolues de ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pStart`  
 à Pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de départ du frame de pile représenté par cet `ICorDebugFrame` objet.  
  
 `pEnd`  
 à Pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de fin du frame de pile représenté par cet `ICorDebugFrame` objet.  
  
## <a name="remarks"></a>Remarques  

 La plage d’adresses de la pile est utile pour accolant ensemble de traces de pile entrelacées rassemblées à partir de plusieurs moteurs de débogage. La plage numérique ne fournit aucune information sur le contenu du frame de pile. Elle est explicite uniquement pour la comparaison des emplacements de frame de pile.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
