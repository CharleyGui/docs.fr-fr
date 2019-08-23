---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919976"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="0c325-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="0c325-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="0c325-102">Représente une collection d’URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="0c325-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="0c325-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0c325-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0c325-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="0c325-104">\<behaviors></span></span>  
<span data-ttu-id="0c325-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0c325-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0c325-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="0c325-106">\<behavior></span></span>  
<span data-ttu-id="0c325-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="0c325-107">\<serviceCredentials></span></span>  
<span data-ttu-id="0c325-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="0c325-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="0c325-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="0c325-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c325-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c325-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c325-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c325-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0c325-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c325-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c325-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c325-113">Attributes</span></span>  
 <span data-ttu-id="0c325-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c325-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c325-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c325-115">Child Elements</span></span>  
  
|<span data-ttu-id="0c325-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0c325-116">Element</span></span>|<span data-ttu-id="0c325-117">Description</span><span class="sxs-lookup"><span data-stu-id="0c325-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c325-118">\<add></span><span class="sxs-lookup"><span data-stu-id="0c325-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="0c325-119">Ajoute un URI cible pour lequel le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="0c325-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c325-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c325-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0c325-121">Élément</span><span class="sxs-lookup"><span data-stu-id="0c325-121">Element</span></span>|<span data-ttu-id="0c325-122">Description</span><span class="sxs-lookup"><span data-stu-id="0c325-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c325-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="0c325-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="0c325-124">Spécifie un jeton émis en guise d'information d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="0c325-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c325-125">Notes</span><span class="sxs-lookup"><span data-stu-id="0c325-125">Remarks</span></span>  
 <span data-ttu-id="0c325-126">Vous devez utiliser cette collection dans une application fédérée qui utilise un service de jeton de sécurité (STS) qui émet des jetons de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="0c325-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="0c325-127">Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant un <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> au jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0c325-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="0c325-128">Cela permet au <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0c325-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="0c325-129">Affectez à l'attribut `audienceUriMode` de `<issuedTokenAuthentication>` la valeur <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="0c325-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="0c325-130">Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection.</span><span class="sxs-lookup"><span data-stu-id="0c325-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="0c325-131">Pour plus d'informations, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="0c325-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="0c325-132">Pour plus d’informations sur l’utilisation de cet élément [de configuration, consultez Procédure: Configurez les informations d'](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)identification sur un service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="0c325-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c325-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c325-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="0c325-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="0c325-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="0c325-135">\<add></span><span class="sxs-lookup"><span data-stu-id="0c325-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="0c325-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="0c325-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0c325-137">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0c325-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0c325-138">Guide pratique : Configurer les informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="0c325-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
