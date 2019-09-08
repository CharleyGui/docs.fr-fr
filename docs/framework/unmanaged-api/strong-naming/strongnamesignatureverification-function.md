---
title: StrongNameSignatureVerification, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798951"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification, fonction
Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameSignatureVerification (](../hosting/iclrstrongname-strongnamesignatureverification-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 dans Chemin d’accès au fichier exécutable portable (. dll ou. exe) de l’assembly à vérifier.  
  
 `dwInFlags`  
 dans Indicateurs permettant de modifier le comportement de vérification. Les valeurs suivantes sont prises en charge :  
  
- `SN_INFLAG_FORCE_VER`(0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.  
  
- `SN_INFLAG_INSTALL`(0x00000002) : spécifie qu’il s’agit de la première fois que le manifeste est vérifié.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004) : spécifie que le cache autorise uniquement l’accès aux utilisateurs disposant de privilèges d’administrateur.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-réservé au débogage interne.  
  
 `pdwOutFlags`  
 à Indicateurs indiquant si la signature de nom fort a été vérifiée. La valeur suivante est prise en charge :  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si la vérification a réussi ; Sinon, `false`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerification, méthode](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx, méthode](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
