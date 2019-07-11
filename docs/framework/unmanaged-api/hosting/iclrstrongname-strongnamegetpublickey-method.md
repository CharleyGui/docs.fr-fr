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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1d98ada710771029e92ae2a942105e361a6ac7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747980"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>Méthode ICLRStrongName::StrongNameGetPublicKey
Obtient la clé publique à partir d’une paire de clés publique/privée. La paire de clés peut être fournie sous la forme d’un nom de conteneur de clé au sein d’un fournisseur de services de chiffrement (CSP) ou une collection brute d’octets.  
  
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
 [in] Le nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le CSP. Dans ce cas, le [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.  
  
 Les clés doivent être Rivest-Shamir-Adleman (RSA 1024 bits) clés de signature. Aucun autre type de clés n’est pris en charge pour l’instant.  
  
 `pbKeyBlob`  
 [in] Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par Win32 `CryptExportKey` (fonction). Si `pbKeyBlob` est null, le conteneur de clé spécifié par `szKeyContainer` est supposée pour contenir la paire de clés.  
  
 `cbKeyBlob`  
 [in] La taille, en octets, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] La clé publique BLOB retournée. Le `ppbPublicKeyBlob` paramètre est allouée par le common language runtime et retourné à l’appelant. L’appelant doit libérer la mémoire à l’aide de la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).  
  
 `pcbPublicKeyBlob`  
 [out] La taille de la clé publique retournée BLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Notes  
 La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
