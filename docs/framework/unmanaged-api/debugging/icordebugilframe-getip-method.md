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
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178823"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP, méthode
Obtient la valeur du pointeur d’instruction et une valeur de combinaison bitwise qui décrit comment la valeur du pointeur d’instruction a été obtenue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pnOffset`  
 [out] La valeur du pointeur d’instruction.  
  
 `pMappingResult`  
 [out] Un pointeur à une combinaison un peu sage des valeurs d’énumération CorDebugMappingResult qui décrivent comment la valeur du pointeur d’instruction a été obtenue.  
  
## <a name="remarks"></a>Notes   
 La valeur du pointeur d’instruction est la compensation de l’image de pile dans le code de la langue intermédiaire Microsoft (MSIL) de la fonction. Si le cadre de pile est actif, cette adresse est la prochaine instruction à exécuter. Si le cadre de pile n’est pas actif, cette adresse est la prochaine instruction à exécuter lorsque le cadre de pile est réactivé.  
  
 Si ce cadre est un cadre juste-à-temps (JIT) compilé, la valeur du pointeur d’instruction sera déterminée en cartographiant à l’envers à partir du pointeur d’instruction natif réel, de sorte que la valeur peut être seulement approximative.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
