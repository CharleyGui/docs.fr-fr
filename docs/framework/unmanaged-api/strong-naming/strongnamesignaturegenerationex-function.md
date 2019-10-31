---
title: StrongNameSignatureGenerationEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141577"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx, fonction
Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameSignatureGenerationEx (](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
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
  
 Si `pbKeyBlob` a la valeur null, `wszKeyContainer` devez spécifier un conteneur valide dans le fournisseur de services de chiffrement (CSP). Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.  
  
 Si `pbKeyBlob` n’a pas la valeur null, la paire de clés est supposée être contenue dans l’objet BLOB (Binary Large Object) clé.  
  
 `pbKeyBlob`  
 dans Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par la fonction de `CryptExportKey` Win32. Si `pbKeyBlob` a la valeur null, le conteneur de clé spécifié par `wszKeyContainer` est supposé contenir la paire de clés.  
  
 `cbKeyBlob`  
 dans Taille, en octets, de `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 à Pointeur vers l’emplacement vers lequel le common language runtime retourne la signature. Si `ppbSignatureBlob` a la valeur null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath`.  
  
 Si `ppbSignatureBlob` n’a pas la valeur null, le common language runtime alloue de l’espace dans lequel retourner la signature. L’appelant doit libérer cet espace à l’aide de la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .  
  
 `pcbSignatureBlob`  
 à Taille, en octets, de la signature retournée.  
  
 `dwFlags`  
 dans Une ou plusieurs des valeurs suivantes :  
  
- `SN_SIGN_ALL_FILES` (0x00000001)-recalcule tous les hachages pour les modules liés.  
  
- `SN_TEST_SIGN` (0x00000002) : testez la signature de l’assembly.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Spécifiez NULL pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.  
  
 La signature peut être stockée directement dans le fichier ou être retournée à l’appelant.  
  
 Si `SN_SIGN_ALL_FILES` est spécifié mais qu’une clé publique n’est pas incluse (les `pbKeyBlob` et `wszFilePath` sont null), les hachages des modules liés sont recalculés, mais l’assembly n’est pas resigné.  
  
 Si `SN_TEST_SIGN` est spécifié, l’en-tête common language runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.  
  
 Si la fonction `StrongNameSignatureGenerationEx` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureGenerationEx, méthode](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration, méthode](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
