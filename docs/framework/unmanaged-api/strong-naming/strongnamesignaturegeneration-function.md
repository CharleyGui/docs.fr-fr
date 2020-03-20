---
title: StrongNameSignatureGeneration, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176901"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration, fonction
Génère une signature de nom fort pour l’assembly spécifié.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
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
  
 Si `ppbSignatureBlob` elle n’est pas nulle, le runtime de langue commune alloue l’espace pour retourner la signature. L’appelant doit libérer cet espace en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbSignatureBlob`  
 [out] La taille, dans les octets, de la signature retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`à la réussite; autrement, `false`.  
  
## <a name="remarks"></a>Notes   
 Spécifier null pour `wszFilePath` calculer la taille de la signature sans créer la signature.  
  
 La signature peut être stockée directement dans le fichier, soit retournée à l’appelant.  
  
 Si `StrongNameSignatureGeneration` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureGeneration, méthode](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx, méthode](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
