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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36ff06b4bbe916e7038840d9bf3cbc455f161b70
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768309"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx, méthode
Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.  
  
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
 [in] Le nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP). Dans ce cas, le `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
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
  
 `uHashAlgId`  
 [in] L’algorithme de hachage d’assembly. Consultez la section Notes pour obtenir la liste des valeurs acceptées.  
  
 `uReserved`  
 [in] Réservé pour une utilisation ultérieure ; valeur par défaut est null.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Notes  
 La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant présente l’ensemble des valeurs acceptées pour la `uHashAlgId` paramètre.  
  
|Nom|Valeur|  
|----------|-----------|  
|Aucun|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
