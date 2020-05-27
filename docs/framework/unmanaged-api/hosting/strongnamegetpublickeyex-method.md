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
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006371"
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
 dans Nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP). Dans ce cas, la `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.  
  
 Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits. Aucun autre type de clé n’est pris en charge pour l’instant.  
  
 `pbKeyBlob`  
 dans Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par la fonction Win32 `CryptExportKey` . Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `szKeyContainer` est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob` .  
  
 `ppbPublicKeyBlob`  
 à Objet BLOB de clé publique retourné. Le `ppbPublicKeyBlob` paramètre est alloué par le Common Language Runtime et retourné à l’appelant. L’appelant doit libérer la mémoire à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbPublicKeyBlob`  
 à Taille de l’objet BLOB de clé publique retourné.  
  
 `uHashAlgId`  
 dans Algorithme de hachage de l’assembly. Consultez la section Notes pour obtenir la liste des valeurs acceptées.  
  
 `uReserved`  
 dans Réservé à une utilisation ultérieure ; la valeur par défaut est null.  
  
## <a name="return-value"></a>Valeur renvoyée  
 `S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Remarques  
 La clé publique est contenue dans une structure [publicKeyBlob](../strong-naming/publickeyblob-structure.md) .  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant présente l’ensemble des valeurs acceptées pour le `uHashAlgId` paramètre.  
  
|Nom|Valeur|  
|----------|-----------|  
|None|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob, structure](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
- [StrongNameGetPublicKey, méthode](iclrstrongname-strongnamegetpublickey-method.md)
