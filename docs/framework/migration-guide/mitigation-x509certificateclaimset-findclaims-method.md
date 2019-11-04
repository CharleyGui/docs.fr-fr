---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: e75b1cae599b153012b8525a0e1e36ed116e695f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457754"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Atténuation : X509CertificateClaimSet.FindClaims, méthode
En commençant par les applications qui ciblent .NET Framework 4.6.1, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de trouver une correspondance à l’argument `claimType` parmi toutes les entrées DNS de son champ SAN.  
  
## <a name="impact"></a>Impact  
 Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.  
  
 Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.  
  
## <a name="mitigation"></a>Atténuation  
 Si ce changement n’est pas souhaitable, les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous .NET Framework 4.6.1 et versions ultérieures peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
