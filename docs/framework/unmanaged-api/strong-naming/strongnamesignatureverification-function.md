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
ms.openlocfilehash: c47d693f450b9cafcb4c8a388c8c38afcd2094e6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725714"
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
 dans Indicateurs permettant de modifier le comportement de vérification. Les valeurs suivantes sont admises :  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.  
  
- `SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première fois que le manifeste est vérifié.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise uniquement l’accès aux utilisateurs disposant de privilèges d’administrateur.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.  
  
- `SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.  
  
 `pdwOutFlags`  
 à Indicateurs indiquant si la signature de nom fort a été vérifiée. La valeur suivante est prise en charge :  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` Si la vérification a réussi ; Sinon, `false` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerification, méthode](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx, méthode](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
