---
title: Méthode ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181939"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>Méthode ICLRStrongName::StrongNameGetPublicKey
Obtient la clé publique d’une paire de clés public/privé. La paire de clés peut être fournie soit comme un nom de conteneur clé au sein d’un fournisseur de services cryptographiques (CSP) ou comme une collection brute d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szKeyContainer`  
 [dans] Le nom du conteneur clé qui contient la paire de clés public/privé. S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide dans le CSP. Dans ce cas, la méthode [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode extrait la clé publique de la paire de clés stockées dans le conteneur.  
  
 Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).  
  
 Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature. Aucun autre type de clés n’est pris en charge pour le moment.  
  
 `pbKeyBlob`  
 [dans] Un pointeur à la paire de clés public/privé. Cette paire est dans le format `CryptExportKey` créé par la fonction Win32. S’il `pbKeyBlob` est nul, `szKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 [dans] La taille, dans les `pbKeyBlob`octets, de .  
  
 `ppbPublicKeyBlob`  
 [out] Le BLOB clé publique retourné. Le `ppbPublicKeyBlob` paramètre est attribué par l’heure de l’exécution de la langue commune et retourné à l’appelant. L’appelant doit libérer la mémoire en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.  
  
 `pcbPublicKeyBlob`  
 [out] La taille de la clé publique retournée BLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes   
 La clé publique est contenue dans une structure [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MetaHost.h MetaHost.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
