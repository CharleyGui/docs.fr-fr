---
title: Authenticode (Informations de référence sur les API non managées)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 9b3e1585278bda82dedf7542e866a551867b9c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674045"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (Informations de référence sur les API non managées)

Prend en charge le module de création et de vérification des licences XrML Authenticode.  
  
## <a name="in-this-section"></a>Dans cette section  

 [_AxlGetIssuerPublicKeyHash, fonction](axlgetissuerpublickeyhash-function.md)  
 Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.  
  
 [_AxlPublicKeyBlobToPublicKeyToken, fonction](axlpublickeyblobtopublickeytoken-function.md)  
 Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.  
  
 [_AxlRSAKeyValueToPublicKeyToken, fonction](axlrsakeyvaluetopublickeytoken-function.md)  
 Convertit un modulo et un exposant en un jeton de clé publique de nom fort.  
  
 [CertFreeAuthenticodeSignerInfo, fonction](certfreeauthenticodesignerinfo-function.md)  
 Libère les ressources allouées pour la structure AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [CertFreeAuthenticodeTimestamperInfo, fonction](certfreeauthenticodetimestamperinfo-function.md)  
 Libère les ressources allouées pour la structure AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [CertTimestampAuthenticodeLicense, fonction](certtimestampauthenticodelicense-function.md)  
 Effectue un horodatage d'une licence XrML Authenticode créée par CertCreateAuthenticodeLicense.  
  
 [CertVerifyAuthenticodeLicense, fonction](certverifyauthenticodelicense-function.md)  
 Vérifie la validité d'une licence XrML Authenticode.  
  
 [AXL_AUTHENTICODE_SIGNER_INFO, structure](axl-authenticode-signer-info-structure.md)  
 Définit les informations du signataire Authenticode.  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure](axl-authenticode-timestamper-info-structure.md)  
 Définit les informations de l'horodateur Authenticode.  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées](../index.md)
