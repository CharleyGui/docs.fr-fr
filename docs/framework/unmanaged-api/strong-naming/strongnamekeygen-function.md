---
title: StrongNameKeyGen, fonction
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799140"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen, fonction
Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameKeyGen (](../hosting/iclrstrongname-strongnamekeygen-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszKeyContainer`  
 dans Nom du conteneur de clé demandé. `wszKeyContainer`doit être une chaîne non vide, ou null pour générer un nom temporaire.  
  
 `dwFlags`  
 dans Spécifie s’il faut conserver la clé inscrite. Les valeurs suivantes sont prises en charge :  
  
- 0x00000000-utilisé lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
- 0x00000001 (`SN_LEAVE_KEY`) : spécifie que la clé doit rester inscrite.  
  
 `ppbKeyBlob`  
 à Paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 à Taille, en octets, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 La `StrongNameKeyGen` fonction crée une clé de 1024 bits. Une fois la clé Récupérée, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.  
  
 Si la `StrongNameKeyGen` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyGen, méthode](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx, méthode](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
