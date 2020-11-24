---
title: Méthode ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 824dcf89bacec27ced7cc431a9646d00fb879430
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674669"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a>Méthode ICLRStrongName::StrongNameGetBlob

Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszFilePath`  
 dans Chemin d’accès valide au fichier exécutable à charger.  
  
 `pbBlob`  
 dans Mémoire tampon dans laquelle charger le fichier exécutable.  
  
 `pcbBlob`  
 [in, out] Taille maximale demandée, en octets, de `pbBlob` . Lors du retour, taille réelle, en octets, de `pbBlob` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetBlobFromImage, méthode](iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
