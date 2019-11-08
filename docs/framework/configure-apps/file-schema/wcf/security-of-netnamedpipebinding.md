---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736441"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="ee835-102">\<> de sécurité de \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="ee835-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="ee835-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="ee835-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="ee835-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee835-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ee835-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ee835-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ee835-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="ee835-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="ee835-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetNamedPipeBinding**](netnamedpipebinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ee835-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="ee835-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="ee835-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="ee835-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="ee835-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee835-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee835-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee835-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee835-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ee835-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee835-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee835-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee835-113">Attributes</span></span>  
  
|<span data-ttu-id="ee835-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee835-114">Attribute</span></span>|<span data-ttu-id="ee835-115">Description</span><span class="sxs-lookup"><span data-stu-id="ee835-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee835-116">mode</span><span class="sxs-lookup"><span data-stu-id="ee835-116">mode</span></span>|<span data-ttu-id="ee835-117">Spécifie le type de sécurité appliqué à cette liaison.</span><span class="sxs-lookup"><span data-stu-id="ee835-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="ee835-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee835-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee835-119">-None : cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="ee835-119">-   None: This disables security.</span></span><br /><span data-ttu-id="ee835-120">-Transport : la sécurité est assurée à l’aide de la sécurité basée sur le transport sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="ee835-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="ee835-121">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="ee835-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="ee835-122">-La valeur par défaut est transport.</span><span class="sxs-lookup"><span data-stu-id="ee835-122">-   The default value is Transport.</span></span> <span data-ttu-id="ee835-123">Cet attribut est de type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ee835-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee835-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee835-124">Child Elements</span></span>  
  
|<span data-ttu-id="ee835-125">Élément</span><span class="sxs-lookup"><span data-stu-id="ee835-125">Element</span></span>|<span data-ttu-id="ee835-126">Description</span><span class="sxs-lookup"><span data-stu-id="ee835-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee835-127">transport</span><span class="sxs-lookup"><span data-stu-id="ee835-127">transport</span></span>|<span data-ttu-id="ee835-128">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="ee835-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="ee835-129">Cet élément est de type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ee835-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee835-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee835-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ee835-131">Élément</span><span class="sxs-lookup"><span data-stu-id="ee835-131">Element</span></span>|<span data-ttu-id="ee835-132">Description</span><span class="sxs-lookup"><span data-stu-id="ee835-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee835-133">liaison</span><span class="sxs-lookup"><span data-stu-id="ee835-133">binding</span></span>|<span data-ttu-id="ee835-134">Élément de liaison de l' [\<netNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="ee835-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee835-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee835-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="ee835-136">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ee835-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ee835-137">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="ee835-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ee835-138">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ee835-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee835-139">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ee835-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ee835-140">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ee835-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ee835-141">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="ee835-141">\<binding></span></span>](bindings.md)
