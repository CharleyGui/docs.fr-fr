---
title: 'ICorDebugCode4 :: EnumerateVariableHomes, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 6d58efa5629bb02158a275dec61c0313bca821a1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720749"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4 :: EnumerateVariableHomes, méthode

Obtient un énumérateur pour les variables locales et les arguments dans une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppEnum`  
 Pointeur vers l’adresse d’un objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) qui est un énumérateur pour les variables locales et les arguments dans une fonction.  
  
## <a name="remarks"></a>Remarques  

 L’objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) est un énumérateur standard dérivé de l’interface « ICorDebugEnum » qui vous permet d’énumérer des objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) . La collection peut inclure plusieurs objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) pour le même emplacement ou index d’argument s’ils ont des maisons différentes à des points différents dans la fonction.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugCode4, interface](icordebugcode4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
