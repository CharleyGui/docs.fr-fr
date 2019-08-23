---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936542"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="4f96b-102">\<> de sécurité \<de WSDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4f96b-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="4f96b-103">Définit les fonctionnalités de sécurité de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4f96b-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="4f96b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4f96b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f96b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4f96b-105">\<bindings></span></span>  
<span data-ttu-id="4f96b-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4f96b-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="4f96b-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="4f96b-107">\<binding></span></span>  
<span data-ttu-id="4f96b-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="4f96b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f96b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f96b-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f96b-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4f96b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f96b-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4f96b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f96b-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4f96b-112">Attributes</span></span>  
  
|<span data-ttu-id="4f96b-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="4f96b-113">Attribute</span></span>|<span data-ttu-id="4f96b-114">Description</span><span class="sxs-lookup"><span data-stu-id="4f96b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f96b-115">mode</span><span class="sxs-lookup"><span data-stu-id="4f96b-115">mode</span></span>|<span data-ttu-id="4f96b-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4f96b-116">-   Optional.</span></span> <span data-ttu-id="4f96b-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="4f96b-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4f96b-118">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="4f96b-118">The default value is `Message`.</span></span> <span data-ttu-id="4f96b-119">Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4f96b-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4f96b-120">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="4f96b-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="4f96b-121">`Value`</span><span class="sxs-lookup"><span data-stu-id="4f96b-121">Value</span></span>|<span data-ttu-id="4f96b-122">Description</span><span class="sxs-lookup"><span data-stu-id="4f96b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f96b-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="4f96b-123">None</span></span>|<span data-ttu-id="4f96b-124">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4f96b-124">Security is disabled.</span></span>|  
|<span data-ttu-id="4f96b-125">Message</span><span class="sxs-lookup"><span data-stu-id="4f96b-125">Message</span></span>|<span data-ttu-id="4f96b-126">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="4f96b-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f96b-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4f96b-127">Child Elements</span></span>  
  
|<span data-ttu-id="4f96b-128">Élément</span><span class="sxs-lookup"><span data-stu-id="4f96b-128">Element</span></span>|<span data-ttu-id="4f96b-129">Description</span><span class="sxs-lookup"><span data-stu-id="4f96b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f96b-130">\<message></span><span class="sxs-lookup"><span data-stu-id="4f96b-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="4f96b-131">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="4f96b-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="4f96b-132">Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="4f96b-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f96b-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4f96b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4f96b-134">Élément</span><span class="sxs-lookup"><span data-stu-id="4f96b-134">Element</span></span>|<span data-ttu-id="4f96b-135">Description</span><span class="sxs-lookup"><span data-stu-id="4f96b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f96b-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="4f96b-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4f96b-137">Définit toutes les fonctions de liaison de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4f96b-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f96b-138">Notes</span><span class="sxs-lookup"><span data-stu-id="4f96b-138">Remarks</span></span>  
 <span data-ttu-id="4f96b-139">Une liaison double expose l'adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="4f96b-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="4f96b-140">Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.</span><span class="sxs-lookup"><span data-stu-id="4f96b-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f96b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f96b-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="4f96b-142">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="4f96b-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4f96b-143">Liaisons</span><span class="sxs-lookup"><span data-stu-id="4f96b-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f96b-144">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="4f96b-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4f96b-145">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="4f96b-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4f96b-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="4f96b-146">\<binding></span></span>](../../../misc/binding.md)
