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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895214"
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
 Si un objet <xref:System.AppDomain?displayProperty=nameWithType> managé n’a pas été construit pour ce domaine d’application, `S_FALSE` la méthode `NULL` retourne `*ppObject`et place dans.  
  
## <a name="remarks"></a>Notes   
 Chaque domaine d’application dans un processus peut avoir un <xref:System.AppDomain?displayProperty=nameWithType> objet managé dans le runtime qui le représente. Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet <xref:System.AppDomain?displayProperty=nameWithType> objet managé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
