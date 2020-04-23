---
title: 'Atténuation : X509CertificateClaimSet.FindClaims, méthode'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102643"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="71755-102">Atténuation : X509CertificateClaimSet.FindClaims, méthode</span><span class="sxs-lookup"><span data-stu-id="71755-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="71755-103">En commençant par les applications qui ciblent .NET <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Framework 4.6.1, la méthode tentera de faire correspondre l’argument `claimType` avec toutes les entrées DNS dans son champ SAN.</span><span class="sxs-lookup"><span data-stu-id="71755-103">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="71755-104">Impact</span><span class="sxs-lookup"><span data-stu-id="71755-104">Impact</span></span>  
 <span data-ttu-id="71755-105">Ce changement affecte uniquement les applications qui ciblent .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="71755-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="71755-106">Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.</span><span class="sxs-lookup"><span data-stu-id="71755-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="71755-107">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="71755-107">Mitigation</span></span>  
 <span data-ttu-id="71755-108">Si cette modification n’est pas souhaitable, les applications qui ciblent les versions du cadre .NET en commençant par le cadre [ \<](../configure-apps/file-schema/runtime/runtime-element.md) .NET 4.6.1 peuvent s’en retirer en ajoutant le paramètre de configuration suivant à la section>de l’application :</span><span class="sxs-lookup"><span data-stu-id="71755-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="71755-109">En outre, les applications qui ciblent les versions précédentes du cadre .NET mais sont en cours d’exécution sous le cadre .NET 4.6.1 et les versions ultérieures peuvent opter pour ce comportement en ajoutant le paramètre de configuration suivant à la [ \<section de temps d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application:</span><span class="sxs-lookup"><span data-stu-id="71755-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71755-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71755-110">See also</span></span>

- [<span data-ttu-id="71755-111">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="71755-111">Application compatibility</span></span>](application-compatibility.md)
