---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137220"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle, méthode
Obtient un pointeur de référence vers l’objet managé spécifié qui a un handle de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `handle`  
 dans Pointeur vers un objet managé qui a un handle de garbage collection. Cette valeur est un objet <xref:System.IntPtr> et peut être récupérée à partir de la <xref:System.Runtime.InteropServices.GCHandle> pour l’objet managé.  
  
 `pOutValue`  
 à Pointeur vers l’adresse d’un objet ICorDebugReferenceValue qui représente une référence à l’objet managé spécifié.  
  
## <a name="remarks"></a>Notes  
 Ne confondez pas la valeur de référence retournée avec une garbage collection valeur de référence.  
  
 La référence retournée se comporte comme une référence normale. Elle est désactivée lorsque l’exécution du code se poursuit après un point d’arrêt. La durée de vie de l’objet cible n’est pas affectée par la durée de vie de la valeur de référence.  
  
> [!NOTE]
> La méthode `GetReferenceValueFromGCHandle` ne valide pas le handle. Par conséquent, la méthode `GetReferenceValueFromGCHandle` peut potentiellement endommager le débogueur et le code en cours de débogage si un handle non valide est passé.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
