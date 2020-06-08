---
title: Méthode ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 69ba58cc8c5235a15749281b3107481be9528f84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503976"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>Méthode ICLRStrongName::StrongNameKeyGen
Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszKeyContainer`  
 dans Nom du conteneur de clé demandé. `wszKeyContainer`doit être une chaîne non vide ou null pour générer un nom temporaire.  
  
 `dwFlags`  
 dans Valeur qui spécifie s’il faut conserver la clé inscrite. Les valeurs suivantes sont admises :  
  
- 0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
- 0x00000001 ( `SN_LEAVE_KEY` ) : spécifie que la clé doit rester inscrite.  
  
 `ppbKeyBlob`  
 à Paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 à Taille, en octets, de `ppbKeyBlob` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 `S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Remarques  
 La méthode [ICLRStrongName :: StrongNameKeyGen (](iclrstrongname-strongnamekeygen-method.md) crée une clé de 1024 bits. Une fois la clé Récupérée, vous devez appeler la méthode [ICLRStrongName :: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) pour libérer la mémoire allouée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyGenEx, méthode](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
