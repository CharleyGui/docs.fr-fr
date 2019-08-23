---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936671"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="febf3-102">\<> de sécurité \<de NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="febf3-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="febf3-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="febf3-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="febf3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="febf3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="febf3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="febf3-105">\<bindings></span></span>  
<span data-ttu-id="febf3-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="febf3-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="febf3-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="febf3-107">\<binding></span></span>  
<span data-ttu-id="febf3-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="febf3-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febf3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="febf3-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="febf3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="febf3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="febf3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="febf3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="febf3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="febf3-112">Attributes</span></span>  
  
|<span data-ttu-id="febf3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="febf3-113">Attribute</span></span>|<span data-ttu-id="febf3-114">Description</span><span class="sxs-lookup"><span data-stu-id="febf3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="febf3-115">mode</span><span class="sxs-lookup"><span data-stu-id="febf3-115">mode</span></span>|<span data-ttu-id="febf3-116">Spécifie le type de sécurité appliqué à cette liaison.</span><span class="sxs-lookup"><span data-stu-id="febf3-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="febf3-117">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="febf3-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="febf3-118">None Cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="febf3-118">-   None: This disables security.</span></span><br /><span data-ttu-id="febf3-119">Transport La sécurité est assurée à l’aide de la sécurité basée sur le transport sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="febf3-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="febf3-120">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="febf3-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="febf3-121">-La valeur par défaut est transport.</span><span class="sxs-lookup"><span data-stu-id="febf3-121">-   The default value is Transport.</span></span> <span data-ttu-id="febf3-122">Cet attribut est de type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="febf3-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="febf3-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="febf3-123">Child Elements</span></span>  
  
|<span data-ttu-id="febf3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="febf3-124">Element</span></span>|<span data-ttu-id="febf3-125">Description</span><span class="sxs-lookup"><span data-stu-id="febf3-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="febf3-126">transport</span><span class="sxs-lookup"><span data-stu-id="febf3-126">transport</span></span>|<span data-ttu-id="febf3-127">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="febf3-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="febf3-128">Cet élément est de type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="febf3-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="febf3-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="febf3-129">Parent Elements</span></span>  
  
|<span data-ttu-id="febf3-130">Élément</span><span class="sxs-lookup"><span data-stu-id="febf3-130">Element</span></span>|<span data-ttu-id="febf3-131">Description</span><span class="sxs-lookup"><span data-stu-id="febf3-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="febf3-132">liaison</span><span class="sxs-lookup"><span data-stu-id="febf3-132">binding</span></span>|<span data-ttu-id="febf3-133">Élément de liaison de l' [ \<> NetNamedPipeBinding](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="febf3-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="febf3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="febf3-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="febf3-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="febf3-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="febf3-136">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="febf3-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="febf3-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="febf3-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="febf3-138">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="febf3-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="febf3-139">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="febf3-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="febf3-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="febf3-140">\<binding></span></span>](../../../misc/binding.md)
