---
title: Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 1bfc41fdad35a7e0560d251179ea035c96aecab7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899531"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage
Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pbBase`  
 dans Adresse virtuelle relative du manifeste de l’assembly mappé.  
  
 `dwLength`  
 dans Taille, en octets, de l’image mappée.  
  
 `dwInFlags`  
 dans Indicateurs qui influencent le comportement de la vérification. Les valeurs suivantes sont admises :  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) : force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.  
  
- `SN_INFLAG_INSTALL` (0x00000002) : spécifie qu’il s’agit de la première vérification effectuée sur cette image.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) : spécifie que le cache autorise l’accès uniquement aux utilisateurs disposant de privilèges d’administrateur.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) : spécifie que l’assembly sera uniquement accessible à l’utilisateur actuel.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) : spécifie que le cache ne fournit aucune garantie de restriction d’accès.  
  
- `SN_INFLAG_RUNTIME` (0x80000000)-réservé au débogage interne.  
  
 `pdwOutFlags`  
 à Indicateur pour les informations de sortie supplémentaires. La valeur suivante est prise en charge :  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres du Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
