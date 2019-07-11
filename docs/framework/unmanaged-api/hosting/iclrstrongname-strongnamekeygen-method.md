---
title: Méthode ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c535d3d73b6d3d0165ea2d744ef625a16bd76cd4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747835"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>Méthode ICLRStrongName::StrongNameKeyGen
Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszKeyContainer`  
 [in] Le nom du conteneur de clé demandé. `wszKeyContainer` doit être une chaîne non vide ou une valeur null pour générer un nom temporaire.  
  
 `dwFlags`  
 [in] Une valeur qui spécifie s’il faut laisser la clé enregistrée. Les valeurs suivantes sont prises en charge :  
  
- 0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
- 0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit être inscrit à gauche.  
  
 `ppbKeyBlob`  
 [out] La paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 [out] La taille, en octets, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Notes  
 Le [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) méthode crée une clé 1024 bits. Une fois que la clé est récupérée, vous devez appeler la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode pour libérer la mémoire allouée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyGenEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
