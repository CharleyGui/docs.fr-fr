---
title: ICorDebugNativeFrame::CanSetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: 21890f8130ec677cb88f2f5d7ef648aa19e67e71
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213060"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP, méthode
Obtient un HRESULT qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction (IP) à l’emplacement d’offset spécifié en code natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `nOffset`  
 dans Paramètre souhaité pour le pointeur d’instruction.  
  
## <a name="remarks"></a>Remarks  
 Utilisez la `CanSetIP` méthode avant d’appeler la méthode [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md) . Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugNativeFrame::SetIP` , mais il n’y a aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
