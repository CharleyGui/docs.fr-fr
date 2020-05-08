---
title: ICorDebugEval2::CallParameterizedFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: 72bcc2479f7b6f41b384fc2517f0b04694663398
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976146"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction, méthode
Configure un appel au ICorDebugFunction spécifié, qui peut être imbriqué à l’intérieur d’une classe dont le <xref:System.Type> constructeur accepte des paramètres ou peut <xref:System.Type> prendre lui-même des paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pFunction`  
 dans Pointeur vers un `ICorDebugFunction` objet qui représente la fonction à appeler.  
  
 `nTypeArgs`  
 dans Nombre d’arguments que prend la fonction.  
  
 `ppTypeArgs`  
 dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de fonction.  
  
 `nArgs`  
 dans Nombre de valeurs passées dans la fonction.  
  
 `ppArgs`  
 dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui représente une valeur passée dans un argument de fonction.  
  
## <a name="remarks"></a>Notes   
 `CallParameterizedFunction`est semblable à [ICorDebugEval :: CallFunction](icordebugeval-callfunction-method.md) , sauf que la fonction peut être à l’intérieur d’une classe avec des paramètres de type, peut lui-même prendre des paramètres de type, ou les deux. Les arguments de type doivent être fournis en premier pour la classe, puis pour la fonction.  
  
 Si la fonction se trouve dans un domaine d’application différent, une transition est effectuée. Toutefois, tous les arguments de type et de valeur doivent être dans le domaine d’application cible.  
  
 L’évaluation de fonction ne peut être effectuée que dans des scénarios limités. Si `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` échoue, le HRESULT retourné indique la raison la plus générale possible de l’échec.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
