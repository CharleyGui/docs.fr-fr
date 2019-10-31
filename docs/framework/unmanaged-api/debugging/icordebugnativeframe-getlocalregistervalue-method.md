---
title: ICorDebugNativeFrame::GetLocalRegisterValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139398"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue, méthode
Obtient la valeur d’un argument ou d’une variable locale stockée dans le registre spécifié pour ce frame natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `reg`  
 dans Valeur de l’énumération « CorDebugRegister » qui spécifie le registre contenant la valeur.  
  
 `cbSigBlob`  
 dans Entier qui spécifie la taille de la signature de métadonnées binaires référencée par le paramètre `pvSigBlob`.  
  
 `pvSigBlob`  
 dans Valeur `PCCOR_SIGNATURE` qui pointe vers la signature de métadonnées binaires du type de la valeur.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le registre spécifié.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetLocalRegisterValue` peut être utilisée dans un frame natif ou dans un frame compilé juste-à-temps (JIT).  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
