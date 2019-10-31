---
title: ICorDebugAppDomain::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134711"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject, méthode
Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppObject`  
 à Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le domaine d’application CLR.  
  
## <a name="return-value"></a>Valeur de retour  
 Si un objet <xref:System.AppDomain?displayProperty=nameWithType> managé n’a pas été construit pour ce domaine d’application, la méthode retourne `S_FALSE` et place `NULL` dans `*ppObject`.  
  
## <a name="remarks"></a>Notes  
 Chaque domaine d’application dans un processus peut avoir un objet <xref:System.AppDomain?displayProperty=nameWithType> managé dans le runtime qui le représente. Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet objet de <xref:System.AppDomain?displayProperty=nameWithType> managé.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
