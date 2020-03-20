---
title: ICeeGen::GetString, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177904"
---
# <a name="iceegengetstring-method"></a>ICeeGen::GetString, méthode
Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.  
  
 Cette méthode est obsolète et ne doit pas être utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `RVA`  
 [dans] L’adresse virtuelle relative de la chaîne à revenir.  
  
 `lpString`  
 [out] La ficelle retournée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
