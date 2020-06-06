---
title: <claimTypeRequirements> (élément)
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926144"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="3dfd0-102">\<claimTypeRequirements>, élément</span><span class="sxs-lookup"><span data-stu-id="3dfd0-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="3dfd0-103">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="3dfd0-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="3dfd0-104">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="3dfd0-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3dfd0-105">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="3dfd0-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3dfd0-106">Chaque élément enfant de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="3dfd0-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="3dfd0-107">Une exigence de type de revendication se compose de l’URI du type de revendication requis dans le jeton émis avec un paramètre booléen qui indique si ce type de revendication est requis ou facultatif dans le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="3dfd0-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfd0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dfd0-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3dfd0-109">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="3dfd0-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3dfd0-110">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="3dfd0-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3dfd0-111">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="3dfd0-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3dfd0-112">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="3dfd0-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="3dfd0-113">Liaisons</span><span class="sxs-lookup"><span data-stu-id="3dfd0-113">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3dfd0-114">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="3dfd0-114">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3dfd0-115">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="3dfd0-115">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="3dfd0-116">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3dfd0-116">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="3dfd0-117">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="3dfd0-117">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
