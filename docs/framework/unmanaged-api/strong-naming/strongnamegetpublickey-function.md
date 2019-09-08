---
title: StrongNameGetPublicKey, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799061"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey, fonction
Obtient la clé publique à partir d’une paire de clés publique/privée. La paire de clés peut être fournie en tant que nom de conteneur de clé dans un fournisseur de services de chiffrement (CSP) ou en tant que collection brute d’octets.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szKeyContainer`  
 dans Nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur `szKeyContainer` null, doit spécifier un conteneur valide dans le CSP. Dans ce cas, `StrongNameGetPublicKey` extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.  
  
 Les clés doivent être des clés de signature RSA (Rivest-Shamir-Adleman) 1024 bits. Aucun autre type de clé n’est pris en charge pour l’instant.  
  
 `pbKeyBlob`  
 dans Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par la fonction Win32 `CryptExportKey` . Si `pbKeyBlob` a la valeur null, le conteneur de `szKeyContainer` clé spécifié par est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 à Objet BLOB de clé publique retourné. Le `ppbPublicKeyBlob` paramètre est alloué par le Common Language Runtime et retourné à l’appelant. L’appelant doit libérer la mémoire à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .  
  
 `pcbPublicKeyBlob`  
 à Taille de l’objet BLOB de clé publique retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 La clé publique est contenue dans une structure [publicKeyBlob](publickeyblob-structure.md) .  
  
 Si la `StrongNameGetPublicKey` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetPublicKey, méthode](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey, méthode](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob, structure](publickeyblob-structure.md)
