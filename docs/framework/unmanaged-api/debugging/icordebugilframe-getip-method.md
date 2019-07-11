---
title: ICorDebugILFrame::GetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d7eca3c2825707c9190436377bba7e4bb0d5447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757977"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP, méthode
Obtient la valeur de pointeur d’instruction et une valeur de combinaison de bits qui décrit la façon dont la valeur de pointeur d’instruction a été obtenue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pnOffset`  
 [out] La valeur de pointeur d’instruction.  
  
 `pMappingResult`  
 [out] Pointeur vers une combinaison au niveau du bit des valeurs d’énumération CorDebugMappingResult qui décrivent comment la valeur du pointeur d’instruction a été obtenue.  
  
## <a name="remarks"></a>Notes  
 La valeur de pointeur d’instruction est l’offset du frame de pile dans le code de la fonction Microsoft intermediate language (MSIL). Si le frame de pile est actif, cette adresse est l’instruction suivante à exécuter. Si le frame de pile n’est pas actif, cette adresse est la prochaine instruction à exécuter lorsque le frame de pile est réactivé.  
  
 Si ce frame est un frame de compilé juste-à-temps (JIT), la valeur de pointeur d’instruction sera déterminée en mappant vers l’arrière à partir du pointeur d’instruction natif réel, donc la valeur peut être uniquement approximative.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
