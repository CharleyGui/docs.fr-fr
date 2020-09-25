---
title: <claimTypeRequirements> pour <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: e70b036fddbc706c8c16de9a0834140f600aa5ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173794"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="55f6c-102">\<claimTypeRequirements> pour \<message></span><span class="sxs-lookup"><span data-stu-id="55f6c-102">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="55f6c-103">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="55f6c-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="55f6c-104">La collection est utilisée par le service pour spécifier toutes les revendications obligatoires et facultatives qui doivent se trouver dans le jeton émis que le client utilise pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="55f6c-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="55f6c-105">Le service expose les types de revendication obligatoires dans les métadonnées si la publication WSDL est activée mais WCF ne requiert pas que le jeton émis contienne les types de revendication spécifiés.</span><span class="sxs-lookup"><span data-stu-id="55f6c-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="55f6c-106">Les services qui souhaitent appliquer l'obligation de présence des types de revendication obligatoires doivent le faire à l'aide de la stratégie d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="55f6c-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="55f6c-107">Sur les clients fédérés, cette collection contient la liste des revendications obligatoires et facultatives envoyée au service d’émission de jeton de sécurité dans la demande de jeton émis du client.</span><span class="sxs-lookup"><span data-stu-id="55f6c-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f6c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55f6c-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
