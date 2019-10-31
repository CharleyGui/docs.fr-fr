---
title: CoInitializeEE, fonction
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131939"
---
# <a name="coinitializeee-function"></a>CoInitializeEE, fonction
Garantit que le moteur d’exécution de common language runtime est chargé dans un processus. Cette fonction est déconseillée dans le .NET Framework 4. Utilisez à la place la méthode [ICLRRuntimeHost :: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fFlags`  
 dans Une des constantes d’énumération [COINITIEE,](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans Winerror. h, ainsi que les valeurs du tableau suivant.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|Le moteur d’exécution a été chargé avec succès.|  
|S_FALSE|Le moteur d’exécution est déjà chargé.|  
|E_FAIL|Le moteur d’exécution n’a pas pu être chargé.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode charge le moteur d’exécution s’il n’a pas été chargé précédemment.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
