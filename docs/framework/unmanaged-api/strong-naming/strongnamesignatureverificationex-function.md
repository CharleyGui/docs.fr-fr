---
title: StrongNameSignatureVerificationEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: 27417c379411e242c48d6d9b0c99de833f7ede8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719266"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx, fonction

Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameSignatureVerificationEx (](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszFilePath`  
 dans Chemin d’accès au fichier exécutable portable (. exe ou. dll) de l’assembly à vérifier.  
  
 `fForceVerification`  
 [in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; Sinon, `false` .  
  
 `pfWasVerified`  
 [out] `true` Si la signature de nom fort a été vérifiée ; Sinon, `false` . `pfWasVerified` est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` Si la vérification a réussi ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 `StrongNameSignatureVerificationEx` fournit une fonctionnalité similaire à la fonction [StrongNameSignatureVerification (](strongnamesignatureverification-function.md) . Toutefois, le deuxième paramètre d’entrée et le paramètre de sortie de `StrongNameSignatureVerificationEx` sont de type `BOOLEAN` au lieu de `DWORD` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans mscoree.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerificationEx, méthode](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification, méthode](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
