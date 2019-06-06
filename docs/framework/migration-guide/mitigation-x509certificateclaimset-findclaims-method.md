---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7fb1eb0c502584caac11ca3dde6e7e646b29cfe
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251095"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="45ee4-102">Atténuation : X509CertificateClaimSet.FindClaims, méthode</span><span class="sxs-lookup"><span data-stu-id="45ee4-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="45ee4-103">En commençant par les applications qui ciblent .NET Framework 4.6.1, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de trouver une correspondance à l’argument `claimType` parmi toutes les entrées DNS de son champ SAN.</span><span class="sxs-lookup"><span data-stu-id="45ee4-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="45ee4-104">Impact</span><span class="sxs-lookup"><span data-stu-id="45ee4-104">Impact</span></span>  
 <span data-ttu-id="45ee4-105">Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="45ee4-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="45ee4-106">Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.</span><span class="sxs-lookup"><span data-stu-id="45ee4-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="45ee4-107">Atténuation</span><span class="sxs-lookup"><span data-stu-id="45ee4-107">Mitigation</span></span>  
 <span data-ttu-id="45ee4-108">Si ce changement n’est pas souhaitable, les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="45ee4-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="45ee4-109">De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous .NET Framework 4.6.1 et versions ultérieures peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="45ee4-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45ee4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45ee4-110">See also</span></span>

- [<span data-ttu-id="45ee4-111">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="45ee4-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
