---
title: ICorDebugMDA::GetXML, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: 9a088c7e4e9c72c8247ccdd384bc724587210c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710868"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML, méthode

Obtient le flux de données XML complet associé à l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cchName`  
 [in] Taille du tableau `szName`.  
  
 `pcchName`  
 à Pointeur vers la longueur du flux XML.  
  
 `szName`  
 à Tableau dans lequel stocker le flux XML. Le tableau peut être vide.  
  
## <a name="remarks"></a>Remarques  

 La `GetXML` méthode peut potentiellement affecter les performances, en fonction de la taille du flux XML associé.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMDA, interface](icordebugmda-interface.md)
- [Diagnostic d'erreurs avec les Assistants de débogage managés](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
