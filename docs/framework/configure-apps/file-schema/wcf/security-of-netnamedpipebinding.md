---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736441"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="f485e-102">\<security> de \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f485e-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="f485e-103">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="f485e-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f485e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f485e-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f485e-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f485e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f485e-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f485e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f485e-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f485e-107">Attributes</span></span>  
  
|<span data-ttu-id="f485e-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f485e-108">Attribute</span></span>|<span data-ttu-id="f485e-109">Description</span><span class="sxs-lookup"><span data-stu-id="f485e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f485e-110">mode</span><span class="sxs-lookup"><span data-stu-id="f485e-110">mode</span></span>|<span data-ttu-id="f485e-111">Spécifie le type de sécurité appliqué à cette liaison.</span><span class="sxs-lookup"><span data-stu-id="f485e-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="f485e-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f485e-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f485e-113">-None : cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="f485e-113">-   None: This disables security.</span></span><br /><span data-ttu-id="f485e-114">-Transport : la sécurité est assurée à l’aide de la sécurité basée sur le transport sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="f485e-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="f485e-115">Il est possible de contrôler le niveau de protection avec ce mode.</span><span class="sxs-lookup"><span data-stu-id="f485e-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="f485e-116">-La valeur par défaut est transport.</span><span class="sxs-lookup"><span data-stu-id="f485e-116">-   The default value is Transport.</span></span> <span data-ttu-id="f485e-117">Cet attribut est de type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f485e-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f485e-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f485e-118">Child Elements</span></span>  
  
|<span data-ttu-id="f485e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f485e-119">Element</span></span>|<span data-ttu-id="f485e-120">Description</span><span class="sxs-lookup"><span data-stu-id="f485e-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f485e-121">transport</span><span class="sxs-lookup"><span data-stu-id="f485e-121">transport</span></span>|<span data-ttu-id="f485e-122">Définit les paramètres de sécurité pour le transport.</span><span class="sxs-lookup"><span data-stu-id="f485e-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="f485e-123">Cet élément est de type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f485e-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f485e-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f485e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f485e-125">Élément</span><span class="sxs-lookup"><span data-stu-id="f485e-125">Element</span></span>|<span data-ttu-id="f485e-126">Description</span><span class="sxs-lookup"><span data-stu-id="f485e-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f485e-127">binding</span><span class="sxs-lookup"><span data-stu-id="f485e-127">binding</span></span>|<span data-ttu-id="f485e-128">Élément de liaison de [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f485e-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f485e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f485e-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="f485e-130">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="f485e-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f485e-131">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="f485e-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f485e-132">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f485e-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f485e-133">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f485e-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f485e-134">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f485e-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
