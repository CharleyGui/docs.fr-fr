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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f38f9a3ebd88e0a5abb7a6bc8cb4026dc7d0f068
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736938"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle, méthode
Obtient un pointeur de référence vers l’objet managé spécifié qui a un garbage collection à gérer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `handle`  
 [in] Pointeur vers un objet managé qui a un handle de garbage collection. Cette valeur est un <xref:System.IntPtr> de l’objet et peuvent être récupérées à partir de la <xref:System.Runtime.InteropServices.GCHandle> pour l’objet managé.  
  
 `pOutValue`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugReferenceValue qui représente une référence à l’objet managé spécifié.  
  
## <a name="remarks"></a>Notes  
 Ne confondez pas la valeur de la référence retournée avec une valeur de référence de garbage collection.  
  
 La référence retournée se comporte comme une référence normale. Il est désactivé lors de l’exécution de code se poursuit après un point d’arrêt. La durée de vie de l’objet cible n’est pas affectée par la durée de vie de la valeur de référence.  
  
> [!NOTE]
>  Le `GetReferenceValueFromGCHandle` méthode ne valide pas le handle. Par conséquent, le `GetReferenceValueFromGCHandle` méthode peut potentiellement endommager le débogueur et le code en cours de débogage si un handle non valide est passé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
