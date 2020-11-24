---
title: Méthode ICLRStrongName::StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 7e0c689dad0c288e3af3a3d64ee1bba1c44053c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674526"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>Méthode ICLRStrongName::StrongNameKeyInstall

Importe une paire de clés publique/privée dans un conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszKeyContainer`  
 dans Nom du conteneur de clé. `wszKeyContainer` doit être une chaîne non vide.  
  
 `pbKeyBlob`  
 dans Paire de clés binaires.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Remarques  

 Utilisez la méthode [ICLRStrongName :: StrongNameKeyDelete (](iclrstrongname-strongnamekeydelete-method.md) pour supprimer le conteneur de clé.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyDelete, méthode](iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
