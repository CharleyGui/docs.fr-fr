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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176927"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey, fonction
Obtient la clé publique à partir d’une paire de clés publique/privée. La paire de clés peut être fournie soit comme un nom de conteneur clé au sein d’un fournisseur de services cryptographiques (CSP) ou comme une collection brute d’octets.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode à la place.  
  
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
 [dans] Le nom du conteneur clé qui contient la paire de clés public/privé. S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide dans le CSP. Dans ce `StrongNameGetPublicKey` cas, extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).  
  
 Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature. Aucun autre type de clés n’est pris en charge pour le moment.  
  
 `pbKeyBlob`  
 [dans] Un pointeur à la paire de clés public/privé. Cette paire est dans le format `CryptExportKey` créé par la fonction Win32. S’il `pbKeyBlob` est nul, `szKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 [dans] La taille, dans les `pbKeyBlob`octets, de .  
  
 `ppbPublicKeyBlob`  
 [out] Le BLOB clé publique retourné. Le `ppbPublicKeyBlob` paramètre est attribué par l’heure de l’exécution de la langue commune et retourné à l’appelant. L’appelant doit libérer la mémoire en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbPublicKeyBlob`  
 [out] La taille de la clé publique retournée BLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`à la réussite; autrement, `false`.  
  
## <a name="remarks"></a>Notes   
 La clé publique est contenue dans une structure [PublicKeyBlob.](publickeyblob-structure.md)  
  
 Si `StrongNameGetPublicKey` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetPublicKey, méthode](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey, méthode](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob, structure](publickeyblob-structure.md)
