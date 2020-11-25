---
title: ICorDebugILFrame2::RemapFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: 5eb6299526d69624056961cfb7f0387ff8f873cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725025"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction, méthode

Remappe une fonction modifiée en spécifiant le nouvel offset MSIL (Microsoft Intermediate Language)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `newILOffset`  
 dans Nouvel offset MSIL du frame de pile auquel le pointeur d’instruction doit être placé. Cette valeur doit être un point de séquence.  
  
 Il incombe à l’appelant de garantir la validité de cette valeur. Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.  
  
## <a name="remarks"></a>Remarques  

 Quand la fonction d’un frame a été modifiée, le débogueur peut appeler la `RemapFunction` méthode pour échanger la version la plus récente de la fonction du frame afin de pouvoir l’exécuter. L’exécution du code commence à l’offset MSIL donné.  
  
> [!NOTE]
> Appeler `RemapFunction` , comme appeler [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage liées à la génération d’une trace de la pile pour le thread. Ces interfaces incluent [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame et ICorDebugNativeFrame.  
  
 La `RemapFunction` méthode peut être appelée uniquement dans le contexte du frame actuel, et uniquement dans l’un des cas suivants :  
  
- Après réception d’un rappel [ICorDebugManagedCallback2 :: FunctionRemapOpportunity,](icordebugmanagedcallback2-functionremapopportunity-method.md) qui n’a pas encore été poursuivi.  
  
- Pendant l’arrêt de l’exécution du code en raison d’un événement [ICorDebugManagedCallback :: EditAndContinueRemap,](icordebugmanagedcallback-editandcontinueremap-method.md) pour ce frame.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
