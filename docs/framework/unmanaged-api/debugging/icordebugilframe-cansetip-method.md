---
title: ICorDebugILFrame::CanSetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788589"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP, méthode
Obtient un HRESULT qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `nOffset`  
 dans Paramètre souhaité pour le pointeur d’instruction.  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode `CanSetIP` avant d’appeler la méthode [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md) . Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugILFrame::SetIP`, mais il n’existe aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug, h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
