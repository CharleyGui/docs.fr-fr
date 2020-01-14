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
ms.openlocfilehash: 834292192aa447a113372bc8807041954b39a115
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937770"
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
  
## <a name="parameters"></a>Parameters  
 `pwzKeyContainer`  
 dans Nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur null, `szKeyContainer` devez spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP). Dans ce cas, la méthode `StrongNameGetPublicKeyEx` extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.  
  
 Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits. Aucun autre type de clé n’est pris en charge pour l’instant.  
  
 `pbKeyBlob`  
 dans Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par la fonction de `CryptExportKey` Win32. Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `szKeyContainer` est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 à Objet BLOB de clé publique retourné. Le paramètre `ppbPublicKeyBlob` est alloué par le common language runtime et retourné à l’appelant. L’appelant doit libérer la mémoire à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbPublicKeyBlob`  
 à Taille de l’objet BLOB de clé publique retourné.  
  
 `uHashAlgId`  
 dans Algorithme de hachage de l’assembly. Consultez la section Notes pour obtenir la liste des valeurs acceptées.  
  
 `uReserved`  
 dans Réservé à une utilisation ultérieure ; la valeur par défaut est null.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes  
 La clé publique est contenue dans une structure [publicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant présente l’ensemble des valeurs acceptées pour le paramètre `uHashAlgId`.  
  
|Name|Value|  
|----------|-----------|  
|Aucun|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
