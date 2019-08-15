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
ms.openlocfilehash: 8736da6c8db876b3dadb3b906a586633be176cf6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038325"
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
  
 Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `dwFlags`  
 [in] Facultatif. Une combinaison des valeurs suivantes :  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [en sortie] Pour recevoir les informations du signataire. Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodesignerinfo,](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) après utilisation.  
  
 Consultez [structure AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles. Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodetimestamperinfo,](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) après utilisation.  
  
 Consultez [structure AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [GetHashFromHandle, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
