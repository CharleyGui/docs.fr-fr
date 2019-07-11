---
title: CertVerifyAuthenticodeLicense, fonction
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf7e997282351cc10dd6da1fc405366ea67c7307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741099"
---
# <a name="certverifyauthenticodelicense-function"></a>CertVerifyAuthenticodeLicense, fonction
Vérifie la validité d'une licence XrML Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pLicenseBlob`  
 [en entrée] La licence XrML Authenticode à vérifier.  
  
 Consultez le [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.  
  
 `dwFlags`  
 [in] Facultatif. Une combinaison des valeurs suivantes :  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [en sortie] Pour recevoir les informations du signataire. Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe l’appelant de libérer des ressources à l’aide de la [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) fonction après utilisation.  
  
 Consultez [axl_authenticode_signer_info, Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles. Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe l’appelant de libérer des ressources à l’aide de la [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) fonction après utilisation.  
  
 Consultez [axl_authenticode_timestamper_info, Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [GetHashFromHandle, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
