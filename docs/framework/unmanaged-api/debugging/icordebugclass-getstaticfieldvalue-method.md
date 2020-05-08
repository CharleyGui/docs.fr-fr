---
title: ICorDebugClass::GetStaticFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: d4a254853256e1a1440f5588418b94e39eabcc9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894112"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue, méthode
Obtient la valeur du champ statique spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fieldDef`  
 dans Jeton de `Def` champ qui référence le champ à récupérer.  
  
 `pFrame`  
 dans Pointeur vers un objet ICorDebugFrame qui représente le frame à utiliser pour lever l’ambiguïté entre les threads, le contexte ou les statiques de domaine d’application.  
  
 Si le champ statique est relatif à un thread, à un contexte ou à un domaine d’application, le frame détermine la valeur appropriée.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur du champ statique.  
  
## <a name="remarks"></a>Notes   
 Pour les types paramétrables, la valeur d’un champ statique est relative à l’instanciation particulière. Par conséquent, si le constructeur de classe accepte des <xref:System.Type>paramètres de type, appelez [ICorDebugType :: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) au lieu de `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
