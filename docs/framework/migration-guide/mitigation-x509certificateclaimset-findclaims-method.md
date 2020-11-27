---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
description: Découvrez comment la méthode X509CertificateClaimSet. FindClaims a été modifiée pour les applications qui ciblent .NET Framework 4.6.1.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253568"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="98d98-103">Atténuation : X509CertificateClaimSet.FindClaims, méthode</span><span class="sxs-lookup"><span data-stu-id="98d98-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="98d98-104">À compter des applications qui ciblent .NET Framework 4.6.1, la <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> méthode tente de faire correspondre l' `claimType` argument avec toutes les entrées DNS dans son champ San.</span><span class="sxs-lookup"><span data-stu-id="98d98-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="98d98-105">Impact</span><span class="sxs-lookup"><span data-stu-id="98d98-105">Impact</span></span>  

 <span data-ttu-id="98d98-106">Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="98d98-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="98d98-107">Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.</span><span class="sxs-lookup"><span data-stu-id="98d98-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="98d98-108">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="98d98-108">Mitigation</span></span>  

 <span data-ttu-id="98d98-109">Si cette modification n’est pas souhaitable, les applications qui ciblent les versions de la .NET Framework à partir de la .NET Framework 4.6.1 peuvent les refuser en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="98d98-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="98d98-110">En outre, les applications qui ciblent des versions antérieures du .NET Framework mais s’exécutent sous le .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="98d98-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98d98-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98d98-111">See also</span></span>

- [<span data-ttu-id="98d98-112">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="98d98-112">Application compatibility</span></span>](application-compatibility.md)
