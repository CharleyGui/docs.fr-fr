---
title: ICorDebugCode::CreateBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: ade428ce001a6b40e2fed67f4f23b12cef5ea30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717647"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint, méthode

Crée un point d’arrêt dans ce segment de code à l’offset spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `offset`  
 dans Offset à partir duquel créer le point d’arrêt.  
  
 `ppBreakpoint`  
 à Pointeur vers l’adresse d’un objet « ICorDebugFunctionBreakpoint » qui représente le point d’arrêt.  
  
## <a name="remarks"></a>Remarques  

 Avant que le point d’arrêt soit actif, il doit être ajouté à l’objet processus.  
  
 Si ce code est du code MSIL (Microsoft Intermediate Language), et qu’il existe une version native, compilée juste-à-temps (JIT), du code, le point d’arrêt est également appliqué dans le code compilé juste-à-temps. (C’est également le cas si le code est compilé juste-à-temps ultérieurement.)  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
