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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c15b8e416a5070f59a4df44b3e670e2eb9316b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630544"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>Méthode ICLRStrongName::StrongNameSignatureVerification
Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort, ce qui est vérifiée en fonction des indicateurs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [in] Le chemin d’accès pour le fichier exécutable portable (.dll ou .exe) pour l’assembly à vérifier.  
  
 `dwInFlags`  
 [in] Indicateurs pour modifier le comportement de vérification. Les valeurs suivantes sont prises en charge :  
  
- `SN_INFLAG_FORCE_VER` (0 x 00000001) - force la vérification même s’il est nécessaire de remplacer les paramètres de Registre.  
  
- `SN_INFLAG_INSTALL` (0 x 00000002) - Spécifie qu’il s’agit de la première fois que le manifeste est vérifié.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0 x 00000004) - Spécifie que le cache autorise l’accès uniquement aux utilisateurs qui disposent des privilèges d’administrateur.  
  
- `SN_INFLAG_USER_ACCESS` (0 x 00000008) - Spécifie que l’assembly sera accessible uniquement à l’utilisateur actuel.  
  
- `SN_INFLAG_ALL_ACCESS` (0 x 00000010) - Spécifie que le cache ne fournirez aucune garantie de restriction d’accès.  
  
- `SN_INFLAG_RUNTIME` (0 x 80000000) - réservé au débogage interne.  
  
 `pdwOutFlags`  
 [out] Indicateurs spécifiant si la signature de nom fort a été vérifiée. La valeur suivante est prise en charge :  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0 x 00000001) - cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureVerificationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
