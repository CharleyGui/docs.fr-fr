---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
description: Découvrez comment la méthode X509CertificateClaimSet. FindClaims a été modifiée pour les applications qui ciblent .NET Framework 4.6.1.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475318"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Atténuation : X509CertificateClaimSet.FindClaims, méthode

À compter des applications qui ciblent .NET Framework 4.6.1, la <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> méthode tente de faire correspondre l' `claimType` argument avec toutes les entrées DNS dans son champ San.  
  
## <a name="impact"></a>Impact  
 Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.  
  
 Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.  
  
## <a name="mitigation"></a>Limitation des risques  
 Si cette modification n’est pas souhaitable, les applications qui ciblent les versions de la .NET Framework à partir de la .NET Framework 4.6.1 peuvent les refuser en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 En outre, les applications qui ciblent des versions antérieures du .NET Framework mais s’exécutent sous le .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
