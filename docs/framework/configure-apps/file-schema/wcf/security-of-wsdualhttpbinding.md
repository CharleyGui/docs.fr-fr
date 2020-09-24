---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 7398cd538bb240e78413575f7c28abe7f797d05c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162203"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="b50fd-102">\<security> de \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b50fd-102">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="b50fd-103">Définit les fonctionnalités de sécurité de [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b50fd-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="b50fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b50fd-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b50fd-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b50fd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b50fd-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b50fd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b50fd-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b50fd-107">Attributes</span></span>  
  
|<span data-ttu-id="b50fd-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b50fd-108">Attribute</span></span>|<span data-ttu-id="b50fd-109">Description</span><span class="sxs-lookup"><span data-stu-id="b50fd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b50fd-110">mode</span><span class="sxs-lookup"><span data-stu-id="b50fd-110">mode</span></span>|<span data-ttu-id="b50fd-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b50fd-111">-   Optional.</span></span> <span data-ttu-id="b50fd-112">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="b50fd-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b50fd-113">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="b50fd-113">The default value is `Message`.</span></span> <span data-ttu-id="b50fd-114">Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b50fd-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b50fd-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="b50fd-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="b50fd-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="b50fd-116">Value</span></span>|<span data-ttu-id="b50fd-117">Description</span><span class="sxs-lookup"><span data-stu-id="b50fd-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b50fd-118">None</span><span class="sxs-lookup"><span data-stu-id="b50fd-118">None</span></span>|<span data-ttu-id="b50fd-119">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b50fd-119">Security is disabled.</span></span>|  
|<span data-ttu-id="b50fd-120">Message</span><span class="sxs-lookup"><span data-stu-id="b50fd-120">Message</span></span>|<span data-ttu-id="b50fd-121">La sécurité est fournie à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="b50fd-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b50fd-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b50fd-122">Child Elements</span></span>  
  
|<span data-ttu-id="b50fd-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b50fd-123">Element</span></span>|<span data-ttu-id="b50fd-124">Description</span><span class="sxs-lookup"><span data-stu-id="b50fd-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="b50fd-125">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="b50fd-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b50fd-126">Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="b50fd-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b50fd-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b50fd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b50fd-128">Élément</span><span class="sxs-lookup"><span data-stu-id="b50fd-128">Element</span></span>|<span data-ttu-id="b50fd-129">Description</span><span class="sxs-lookup"><span data-stu-id="b50fd-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="b50fd-130">Définit toutes les fonctions de liaison de [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b50fd-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b50fd-131">Notes</span><span class="sxs-lookup"><span data-stu-id="b50fd-131">Remarks</span></span>  

 <span data-ttu-id="b50fd-132">Une liaison double expose l'adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="b50fd-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="b50fd-133">Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.</span><span class="sxs-lookup"><span data-stu-id="b50fd-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50fd-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b50fd-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b50fd-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b50fd-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b50fd-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b50fd-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b50fd-137">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="b50fd-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b50fd-138">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b50fd-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
