---
title: Création de revendications et valeurs de ressource
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: fabd0a2606560d99174e5ad28940c3b59ee689d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587051"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="7d5c1-102">Création de revendications et valeurs de ressource</span><span class="sxs-lookup"><span data-stu-id="7d5c1-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="7d5c1-103">La classe <xref:System.IdentityModel.Claims.Claim> fournit plusieurs méthodes de création d'instances de types de revendications intégrés.</span><span class="sxs-lookup"><span data-stu-id="7d5c1-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="7d5c1-104">Parmi ces méthodes, les suivantes n'effectuent pas de vérification de format ou de sémantique sur la ressource fournie :</span><span class="sxs-lookup"><span data-stu-id="7d5c1-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="7d5c1-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (ne vérifie pas la longueur ou contenu du tableau d'octets)</span><span class="sxs-lookup"><span data-stu-id="7d5c1-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="7d5c1-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (ne vérifie pas la longueur ou contenu du tableau d'octets)</span><span class="sxs-lookup"><span data-stu-id="7d5c1-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="7d5c1-107">Lorsque vous appelez les méthodes ci-dessus, vous devez vous assurer que les valeurs de ressource passées sont au format approprié ou qu'elles contiennent le type d'informations correct (ou les deux).</span><span class="sxs-lookup"><span data-stu-id="7d5c1-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="7d5c1-108">Les méthodes suivantes prennent des types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="7d5c1-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="7d5c1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d5c1-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="7d5c1-110">Gestion des revendications et autorisation avec le modèle d'identité</span><span class="sxs-lookup"><span data-stu-id="7d5c1-110">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
