---
title: StrongNameGetPublicKeyEx, méthode
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176225"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx, méthode
Obtient la clé publique d’une paire de clés publique/privée, et spécifie un algorithme de hachage et un algorithme de signature.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzKeyContainer`  
 [dans] Le nom du conteneur clé qui contient la paire de clés public/privé. S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide au sein du fournisseur de services cryptographiques (CSP). Dans ce cas, la `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
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
  
 `uHashAlgId`  
 [dans] L’algorithme de hachage d’assemblage. Consultez la section Remarques pour une liste de valeurs acceptées.  
  
 `uReserved`  
 [dans] Réservé à une utilisation future; par défaut à null.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes   
 La clé publique est contenue dans une structure [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="remarks"></a>Notes   
 Le tableau suivant montre l’ensemble `uHashAlgId` des valeurs acceptées pour le paramètre.  
  
|Nom|Valeur|  
|----------|-----------|  
|None|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MetaHost.h MetaHost.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
