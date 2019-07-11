---
title: ICorDebugEval2::NewParameterizedObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753585"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject, méthode
Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pConstructor`  
 [in] Pointeur vers un objet ICorDebugFunction qui représente le constructeur de l’objet à instancier.  
  
 `nTypeArgs`  
 [in] Nombre d’arguments de type passés.  
  
 `ppTypeArgs`  
 [in] Tableau de pointeurs, chacun pointant vers un objet de ICorDebugType qui représente un argument de type pour l’objet qui est en cours d’instanciation.  
  
 `nArgs`  
 [in] Le nombre d’arguments passés au constructeur.  
  
 `ppArgs`  
 [in] Tableau de pointeurs, chacun d’eux pointe vers un objet ICorDebugValue qui représente une valeur d’argument est passée au constructeur.  
  
## <a name="remarks"></a>Notes  
 Constructeur de l’objet peut prendre <xref:System.Type> paramètres.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
