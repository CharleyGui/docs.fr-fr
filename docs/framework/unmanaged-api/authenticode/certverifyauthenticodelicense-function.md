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
ms.openlocfilehash: 388814d1c63f048c0aa231a1d0058a390cba9493
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674058"
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
 [en sortie] Pour recevoir les informations du signataire. Si la licence n'était pas signée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodesignerinfo,](certfreeauthenticodesignerinfo-function.md) après utilisation.  
  
 Consultez [AXL_AUTHENTICODE_SIGNER_INFO structure](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [en sortie] Pour recevoir les informations de l'horodateur, si elles sont disponibles. Si la licence n'était pas horodatée, `dwError` est défini à TRUST_E_NOSIGNATURE. Il incombe à l’appelant de libérer des ressources à l’aide de la fonction [certfreeauthenticodetimestamperinfo,](certfreeauthenticodetimestamperinfo-function.md) après utilisation.  
  
 Consultez [AXL_AUTHENTICODE_TIMESTAMPER_INFO structure](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne `S_OK` en cas de réussite. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
- [GetHashFromHandle, méthode](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
