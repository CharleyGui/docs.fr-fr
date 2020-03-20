---
title: Méthode ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176316"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>Méthode ICLRStrongName::StrongNameTokenFromPublicKey
Obtient un jeton qui représente une clé publique. Un jeton de nom fort est la forme raccourcie d’une clé publique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKeyBlob`  
 [dans] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.  
  
 `cbPublicKeyBlob`  
 [dans] La taille, dans les `pbPublicKeyBlob`octets, de .  
  
 `ppbStrongNameToken`  
 [out] Le jeton de nom fort `pbPublicKeyBlob`correspondant à la clé passée dedans . Le runtime de langue commune alloue la mémoire dans laquelle retourner le jeton. L’appelant doit libérer cette mémoire en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.  
  
 `pcbStrongNameToken`  
 [out] La taille, dans les octets, du jeton de nom fort retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes   
 Un jeton de nom fort est la forme raccourcie d’une clé publique qui est utilisée pour économiser de l’espace lors du stockage des informations clés dans les métadonnées. Plus précisément, des jetons de nom forts sont utilisés dans les références d’assemblage pour désigner l’assemblage dépendant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MetaHost.h MetaHost.h  
  
 **Bibliothèque:** Inclus comme une ressource dans mscoree.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
