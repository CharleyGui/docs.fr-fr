---
title: StrongNameKeyGenEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: f28ee5767997240018d182b8303e4f65be81c702
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708541"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx, fonction

Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour une utilisation avec un nom fort.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameKeyGenEx (](../hosting/iclrstrongname-strongnamekeygenex-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszKeyContainer`  
 dans Nom du conteneur de clé demandé. `wszKeyContainer` doit être une chaîne non vide, ou null pour générer un nom temporaire.  
  
 `dwFlags`  
 dans Spécifie s’il faut conserver la clé inscrite. Les valeurs suivantes sont admises :  
  
- 0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
- 0x00000001 ( `SN_LEAVE_KEY` ) : spécifie que la clé doit rester inscrite.  
  
 `dwKeySize`  
 dans Taille demandée de la clé, en bits.  
  
 `ppbKeyBlob`  
 à Paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 à Taille, en octets, de `ppbKeyBlob` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` en cas de réussite de l’opération ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Les versions de .NET Framework 1,0 et 1,1 requièrent un `dwKeySize` de 1024 bits pour signer un assembly avec un nom fort ; la version 2,0 ajoute des prises en charge pour les clés 2048 bits.  
  
 Une fois la clé Récupérée, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.  
  
 Si la `StrongNameKeyGenEx` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyGenEx, méthode](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen, méthode](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
