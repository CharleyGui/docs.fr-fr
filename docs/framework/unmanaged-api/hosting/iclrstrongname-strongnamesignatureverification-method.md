---
title: Méthode ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 2d53eebcc272ab87a2af5b3c081ca37dde5c74b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674474"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>Méthode ICLRStrongName::StrongNameSignatureVerification

Obtient une valeur qui indique si le manifeste de l’assembly au chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
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

 `S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerificationEx, méthode](iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
