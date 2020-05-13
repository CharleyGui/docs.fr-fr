---
title: ICorDebugILFrame::SetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 325b2a009e77d87e95bdb02803dd3c4675c26ddc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213424"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP, méthode
Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `nOffset`  
 Emplacement de décalage dans le code MSIL.  
  
## <a name="remarks"></a>Remarks  
 Les appels à `SetIP` invalident immédiatement tous les frames et chaînes pour le thread actuel. Si le débogueur a besoin d’informations de frame après un appel à `SetIP` , il doit effectuer une nouvelle trace de la pile.  
  
 [ICorDebug](icordebug-interface.md) tente de conserver le frame de pile dans un état valide. Toutefois, même si le frame est dans un état valide, il peut y avoir des problèmes tels que les variables locales non initialisées. L’appelant est chargé de garantir la cohérence du programme en cours d’exécution.  
  
 Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un `catch` `finally` bloc ou. Si `SetIP` est appelé pour effectuer ce déplacement sur une plateforme 64 bits, il retourne un HRESULT indiquant un échec.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
