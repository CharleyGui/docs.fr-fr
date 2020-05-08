---
title: ICorDebugEval2::NewStringWithLength, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976068"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength, méthode
Crée une chaîne de la longueur spécifiée, avec le contenu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `string`  
 dans Pointeur vers la valeur de chaîne.  
  
 `uiLength`  
 dans Longueur de la chaîne.  
  
## <a name="remarks"></a>Notes   
 Si le caractère null de fin de la chaîne est supposé être dans la chaîne managée, l’appelant de `NewStringWithLength` la méthode doit s’assurer que la longueur de la chaîne comprend le caractère null de fin.  
  
 La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
