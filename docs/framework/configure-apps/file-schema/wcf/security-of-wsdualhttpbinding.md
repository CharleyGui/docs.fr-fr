---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: b6a1c952b1ae65c8fb6f17237b5c15f3a8d4844a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399747"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="3f8c7-102">\<> de sécurité \<de WSDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3f8c7-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="3f8c7-103">Définit les fonctionnalités de sécurité de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3f8c7-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="3f8c7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3f8c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3f8c7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3f8c7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3f8c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3f8c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3f8c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3f8c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="3f8c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="3f8c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3f8c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="3f8c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8c7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f8c7-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f8c7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f8c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3f8c7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f8c7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f8c7-113">Attributes</span></span>  
  
|<span data-ttu-id="3f8c7-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f8c7-114">Attribute</span></span>|<span data-ttu-id="3f8c7-115">Description</span><span class="sxs-lookup"><span data-stu-id="3f8c7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f8c7-116">mode</span><span class="sxs-lookup"><span data-stu-id="3f8c7-116">mode</span></span>|<span data-ttu-id="3f8c7-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-117">-   Optional.</span></span> <span data-ttu-id="3f8c7-118">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3f8c7-119">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-119">The default value is `Message`.</span></span> <span data-ttu-id="3f8c7-120">Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3f8c7-121">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="3f8c7-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="3f8c7-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="3f8c7-122">Value</span></span>|<span data-ttu-id="3f8c7-123">Description</span><span class="sxs-lookup"><span data-stu-id="3f8c7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f8c7-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="3f8c7-124">None</span></span>|<span data-ttu-id="3f8c7-125">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-125">Security is disabled.</span></span>|  
|<span data-ttu-id="3f8c7-126">Message</span><span class="sxs-lookup"><span data-stu-id="3f8c7-126">Message</span></span>|<span data-ttu-id="3f8c7-127">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f8c7-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f8c7-128">Child Elements</span></span>  
  
|<span data-ttu-id="3f8c7-129">Élément</span><span class="sxs-lookup"><span data-stu-id="3f8c7-129">Element</span></span>|<span data-ttu-id="3f8c7-130">Description</span><span class="sxs-lookup"><span data-stu-id="3f8c7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f8c7-131">\<message></span><span class="sxs-lookup"><span data-stu-id="3f8c7-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="3f8c7-132">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="3f8c7-133">Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f8c7-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f8c7-134">Parent Elements</span></span>  
  
|<span data-ttu-id="3f8c7-135">Élément</span><span class="sxs-lookup"><span data-stu-id="3f8c7-135">Element</span></span>|<span data-ttu-id="3f8c7-136">Description</span><span class="sxs-lookup"><span data-stu-id="3f8c7-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f8c7-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="3f8c7-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="3f8c7-138">Définit toutes les fonctions de liaison de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3f8c7-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f8c7-139">Notes</span><span class="sxs-lookup"><span data-stu-id="3f8c7-139">Remarks</span></span>  
 <span data-ttu-id="3f8c7-140">Une liaison double expose l'adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="3f8c7-141">Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.</span><span class="sxs-lookup"><span data-stu-id="3f8c7-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8c7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f8c7-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="3f8c7-143">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3f8c7-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3f8c7-144">Liaisons</span><span class="sxs-lookup"><span data-stu-id="3f8c7-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f8c7-145">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="3f8c7-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3f8c7-146">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3f8c7-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3f8c7-147">\<binding></span><span class="sxs-lookup"><span data-stu-id="3f8c7-147">\<binding></span></span>](../../../misc/binding.md)
