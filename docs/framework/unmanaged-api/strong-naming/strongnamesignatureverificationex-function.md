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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798915"
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
 dans pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres du Registre ; `false`sinon,. `true`  
  
 `pfWasVerified`  
 à Si la signature de nom fort a été vérifiée ; sinon, `false`. `true` `pfWasVerified`est également défini sur `false` si la vérification a réussi en raison des paramètres du Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si la vérification a réussi ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 `StrongNameSignatureVerificationEx`fournit une fonctionnalité similaire à la fonction [StrongNameSignatureVerification (](strongnamesignatureverification-function.md) . Toutefois, le deuxième paramètre d’entrée et le paramètre de `StrongNameSignatureVerificationEx` sortie de sont `BOOLEAN` de type `DWORD`au lieu de.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans Mscoree. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerificationEx, méthode](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification, méthode](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
