---
title: 'Procédure : créer une stratégie d’autorisation personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: fef7aa531c946ecacef30bb79f2362bad4d375ed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256025"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="9833a-102">Procédure : créer une stratégie d’autorisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="9833a-102">How to: Create a Custom Authorization Policy</span></span>

<span data-ttu-id="9833a-103">L’infrastructure de modèle d’identité dans Windows Communication Foundation (WCF) prend en charge un modèle d’autorisation basé sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="9833a-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="9833a-104">Les revendications, une fois extraites des jetons, sont traitées par une stratégie d'autorisation personnalisée lorsqu'une telle stratégie a été définie, puis placées dans un <xref:System.IdentityModel.Policy.AuthorizationContext>, lequel peut ensuite être examiné afin de délivrer ou non les autorisations.</span><span class="sxs-lookup"><span data-stu-id="9833a-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="9833a-105">Il est possible d'utiliser une stratégie personnalisée afin de transformer les revendications émanant des jetons entrants en revendications escomptées par l'application.</span><span class="sxs-lookup"><span data-stu-id="9833a-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="9833a-106">De cette façon, la couche d’application peut être isolée des détails sur les revendications différentes servies par les différents types de jetons pris en charge par WCF.</span><span class="sxs-lookup"><span data-stu-id="9833a-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="9833a-107">Cette rubrique contient des instructions permettant d'implémenter une stratégie d'autorisation personnalisée et d'ajouter celle-ci à la collection de stratégies utilisées par un service donné.</span><span class="sxs-lookup"><span data-stu-id="9833a-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="9833a-108">Pour implémenter une stratégie d'autorisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="9833a-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="9833a-109">Définissez une nouvelle classe dérivée de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="9833a-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="9833a-110">Implémentez la propriété <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> en lecture seule en générant une chaîne unique dans le constructeur de la classe et en faisant en sorte que cette chaîne soit retournée à chaque accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9833a-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="9833a-111">Implémentez la propriété <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> en lecture seule en retournant un <xref:System.IdentityModel.Claims.ClaimSet> qui représente l'émetteur de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="9833a-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="9833a-112">Il peut s'agir d'un `ClaimSet` qui représente l'application ou d'un `ClaimSet` intégré (par exemple, le `ClaimSet` retourné par la propriété <xref:System.IdentityModel.Claims.ClaimSet.System%2A> statique).</span><span class="sxs-lookup"><span data-stu-id="9833a-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="9833a-113">Implémentez la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> comme décrit dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="9833a-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="9833a-114">Pour implémenter la méthode d'évaluation</span><span class="sxs-lookup"><span data-stu-id="9833a-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="9833a-115">Deux paramètres sont passés à cette méthode : une instance de la classe <xref:System.IdentityModel.Policy.EvaluationContext> ainsi qu'une référence d'objet.</span><span class="sxs-lookup"><span data-stu-id="9833a-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="9833a-116">Si la stratégie d’autorisation personnalisée ajoute <xref:System.IdentityModel.Claims.ClaimSet> des instances sans tenir compte du contenu actuel du <xref:System.IdentityModel.Policy.EvaluationContext> , ajoutez chacune d’elles `ClaimSet` en appelant la <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> méthode et en retournant la `true` <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="9833a-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="9833a-117">Le renvoi de la valeur `true` indique à l'infrastructure d'autorisation que la stratégie d'autorisation a terminé son travail et qu'il n'est plus nécessaire de l'appeler.</span><span class="sxs-lookup"><span data-stu-id="9833a-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="9833a-118">Si la stratégie d'autorisation personnalisée ajoute des ensembles de revendications uniquement lorsque des revendications sont déjà présentes dans le `EvaluationContext`, recherchez ces revendications en examinant les instances `ClaimSet` retournées par la propriété <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A>.</span><span class="sxs-lookup"><span data-stu-id="9833a-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="9833a-119">Si des revendications sont déjà présentes, ajoutez les nouveaux ensembles de revendications en appelant la méthode <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29>, puis, lorsqu'il n'y a plus d'ensembles de revendications à ajouter, retournez la valeur `true` afin d'indiquer à l'infrastructure d'autorisation que la stratégie d'autorisation a terminé son travail.</span><span class="sxs-lookup"><span data-stu-id="9833a-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="9833a-120">En l'absence de revendications, retournez la valeur `false` afin d'indiquer que la stratégie d'autorisation doit encore être appelée lorsque d'autres stratégies d'autorisation souhaitent ajouter de nouveaux ensembles de revendications au `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="9833a-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="9833a-121">Lorsque les autorisations nécessitent un traitement plus complexe, notamment une évaluation particulière, le second paramètre de la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> est utilisé pour stocker une variable d'état que l'infrastructure d'autorisation repasse à chaque nouvel appel de la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.</span><span class="sxs-lookup"><span data-stu-id="9833a-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="9833a-122">Pour spécifier une stratégie d'autorisation personnalisée dans le fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="9833a-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="9833a-123">Spécifiez le type de la stratégie d'autorisation personnalisée dans l'attribut `policyType` de l'élément `add` de l'élément `authorizationPolicies` de l'élément `serviceAuthorization`.</span><span class="sxs-lookup"><span data-stu-id="9833a-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="9833a-124">Pour spécifier une stratégie d'autorisation personnalisée dans le code</span><span class="sxs-lookup"><span data-stu-id="9833a-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="9833a-125">Créez une liste <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="9833a-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="9833a-126">Créez une instance de la stratégie d'autorisation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9833a-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="9833a-127">Ajoutez l'instance de la stratégie d'autorisation à la liste.</span><span class="sxs-lookup"><span data-stu-id="9833a-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="9833a-128">Répétez les étapes 2 et 3 pour chaque stratégie d'autorisation personnalisée à ajouter.</span><span class="sxs-lookup"><span data-stu-id="9833a-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="9833a-129">Assignez une version en lecture seule de la liste à la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>.</span><span class="sxs-lookup"><span data-stu-id="9833a-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="9833a-130"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9833a-130">Example</span></span>  

 <span data-ttu-id="9833a-131">Dans l'exemple suivant, la stratégie <xref:System.IdentityModel.Policy.IAuthorizationPolicy> est implémentée de manière exhaustive.</span><span class="sxs-lookup"><span data-stu-id="9833a-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9833a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9833a-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="9833a-133">Procédure : comparer des revendications</span><span class="sxs-lookup"><span data-stu-id="9833a-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="9833a-134">Procédure : créer un gestionnaire d’autorisations personnalisé pour un service</span><span class="sxs-lookup"><span data-stu-id="9833a-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="9833a-135">Authorization Policy</span><span class="sxs-lookup"><span data-stu-id="9833a-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
