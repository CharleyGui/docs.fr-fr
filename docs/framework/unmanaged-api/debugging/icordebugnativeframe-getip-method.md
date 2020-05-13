---
title: ICorDebugNativeFrame::GetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213593"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP, méthode
Obtient l’emplacement de décalage de code natif auquel le pointeur d’instruction est actuellement défini.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pnOffset`  
 à Pointeur vers l’emplacement d’offset dans le code natif.  
  
## <a name="remarks"></a>Remarks  
 Si le frame de pile représenté par ce « ICorDebugNativeFrame » est actif, le décalage est l’adresse de l’instruction suivante à exécuter. Si ce frame de pile n’est pas actif, le décalage est l’adresse de l’instruction suivante à exécuter lorsque le frame de pile est réactivé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
