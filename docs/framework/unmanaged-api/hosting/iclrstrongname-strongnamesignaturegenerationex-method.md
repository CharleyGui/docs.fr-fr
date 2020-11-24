---
title: Méthode ICLRStrongName::StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 78cc043953e6288df136b43590831569d112afef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674513"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>Méthode ICLRStrongName::StrongNameSignatureGenerationEx

Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszFilePath`  
 dans Chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort sera générée.  
  
 `wszKeyContainer`  
 dans Nom du conteneur de clé qui contient la paire de clés publique/privée.  
  
 Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP). Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.  
  
 Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.  
  
 `pbKeyBlob`  
 dans Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par la fonction Win32 `CryptExportKey` . Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `wszKeyContainer` est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob` .  
  
 `ppbSignatureBlob`  
 à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature. Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath` .  
  
 Si `ppbSignatureBlob` n’a pas la valeur null, le Common Language Runtime alloue de l’espace dans lequel retourner la signature. L’appelant doit libérer cet espace à l’aide de la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbSignatureBlob`  
 à Taille, en octets, de la signature retournée.  
  
 `dwFlags`  
 dans Une ou plusieurs des valeurs suivantes :  
  
- `SN_SIGN_ALL_FILES` (0x00000001)-recalcule tous les hachages pour les modules liés.  
  
- `SN_TEST_SIGN` (0x00000002) : testez la signature de l’assembly.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Remarques  

 Spécifiez NULL pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.  
  
 La signature peut être stockée directement dans le fichier ou être retournée à l’appelant.  
  
 Si `SN_SIGN_ALL_FILES` est spécifié mais qu’une clé publique n’est pas incluse ( `pbKeyBlob` et que `wszFilePath` la valeur est null), les hachages des modules liés sont recalculés, mais l’assembly n’est pas à nouveau signé.  
  
 Si `SN_TEST_SIGN` est spécifié, l’en-tête Common Language Runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureGeneration, méthode](iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
