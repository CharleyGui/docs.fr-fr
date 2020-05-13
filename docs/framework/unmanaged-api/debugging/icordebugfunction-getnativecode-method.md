---
title: ICorDebugFunction::GetNativeCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213268"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode, méthode
Obtient le code natif pour la fonction qui est représentée par cette instance ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppCode`  
 à Pointeur vers l’instance de ICorDebugCode qui représente le code natif pour cette fonction, ou null si cette fonction est du code MSIL (Microsoft Intermediate Language) qui n’a pas été compilé juste-à-temps (JIT).  
  
## <a name="remarks"></a>Remarks  
 Si la fonction représentée par cette `ICorDebugFunction` instance a été compilée juste-à-temps (JIT) plusieurs fois, comme dans le cas de types génériques, `GetNativeCode` retourne un objet de code natif aléatoire.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
