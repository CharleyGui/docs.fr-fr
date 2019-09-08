---
title: CertTimestampAuthenticodeLicense, fonction
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaf76d4c3d0f5fb59aeb35fae7a7020ee97b74d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776481"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense, fonction
Horodate une licence XrML Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pSignedLicenseBlob`  
 [en entrée] La licence XrML Authenticode signée à horodater. Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pwszTimestampURI`  
 [en entrée] L'URI du server d'horodatage.  
  
 `pTimestampSignatureBlob`  
 [en sortie] Un pointeur vers CRYPT_DATA_BLOB pour recevoir la signature de l'horodatage codé en base64. L’appelant est `pTimestampSignatureBlob` responsable de la libération -> `pbData` `HepFree()` après utilisation. Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
## <a name="remarks"></a>Notes  
 La signature de l'horodatage est en réalité un message PKCS #7 SignedData dont le contenu est la forme binaire de la valeur de SignatureValue de la signature de la licence. Ceci agit comme une contre-signature de la licence.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la fonction réussit. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
