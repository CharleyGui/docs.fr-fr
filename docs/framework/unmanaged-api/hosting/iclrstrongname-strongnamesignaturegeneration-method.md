---
title: Méthode ICLRStrongName::StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178049"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>Méthode ICLRStrongName::StrongNameSignatureGeneration
Génère une signature de nom fort pour l’assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [dans] Le chemin vers le fichier qui contient le manifeste de l’assemblage pour lequel la signature du nom fort sera générée.  
  
 `wszKeyContainer`  
 [dans] Le nom du conteneur clé qui contient la paire de clés public/privé.  
  
 S’il `pbKeyBlob` `wszKeyContainer` est nul, doit spécifier un conteneur valide au sein du fournisseur de services cryptographiques (CSP). Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.  
  
 Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).  
  
 Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature. Aucun autre type de clés n’est pris en charge pour le moment.  
  
 `pbKeyBlob`  
 [dans] Un pointeur à la paire de clés public/privé. Cette paire est dans le format `CryptExportKey` créé par la fonction Win32. S’il `pbKeyBlob` est nul, `wszKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 [dans] La taille, dans les `pbKeyBlob`octets, de .  
  
 `ppbSignatureBlob`  
 [out] Un pointeur à l’endroit où le temps d’exécution de langue commune renvoie la signature. Si `ppbSignatureBlob` elle est nulle, le temps d’exécution stocke la signature dans le fichier spécifié par `wszFilePath`.  
  
 Si `ppbSignatureBlob` elle n’est pas nulle, le runtime de langue commune alloue l’espace pour retourner la signature. L’appelant doit libérer cet espace en utilisant la méthode [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode.  
  
 `pcbSignatureBlob`  
 [out] La taille, dans les octets, de la signature retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes   
 Spécifier null pour `wszFilePath` calculer la taille de la signature sans créer la signature.  
  
 La signature peut être stockée directement dans le fichier, soit retournée à l’appelant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MetaHost.h MetaHost.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureGenerationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
