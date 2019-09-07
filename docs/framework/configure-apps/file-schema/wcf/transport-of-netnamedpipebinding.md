---
title: <transport> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 6ea0b1e374659bbbbb2f47630c009f823ccd4de9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399326"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="d66c7-102">\<> de transport \<de NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="d66c7-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="d66c7-103">Définit les paramètres de sécurité de transport pour un canal nommé.</span><span class="sxs-lookup"><span data-stu-id="d66c7-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="d66c7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d66c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d66c7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d66c7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d66c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d66c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d66c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="d66c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="d66c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="d66c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d66c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="d66c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="d66c7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="d66c7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d66c7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d66c7-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d66c7-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d66c7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d66c7-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d66c7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d66c7-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d66c7-114">Attributes</span></span>  
  
|<span data-ttu-id="d66c7-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d66c7-115">Attribute</span></span>|<span data-ttu-id="d66c7-116">Description</span><span class="sxs-lookup"><span data-stu-id="d66c7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d66c7-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="d66c7-117">protectionLevel</span></span>|<span data-ttu-id="d66c7-118">Définit le niveau de protection du canal nommé.</span><span class="sxs-lookup"><span data-stu-id="d66c7-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="d66c7-119">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="d66c7-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="d66c7-120">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="d66c7-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="d66c7-121">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d66c7-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d66c7-122">None Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="d66c7-122">-   None: No protection.</span></span><br /><span data-ttu-id="d66c7-123">Expéditeur Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="d66c7-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d66c7-124">EncryptAndSign Les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="d66c7-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="d66c7-125">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="d66c7-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d66c7-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d66c7-126">Child Elements</span></span>  
 <span data-ttu-id="d66c7-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="d66c7-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d66c7-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d66c7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d66c7-129">Élément</span><span class="sxs-lookup"><span data-stu-id="d66c7-129">Element</span></span>|<span data-ttu-id="d66c7-130">Description</span><span class="sxs-lookup"><span data-stu-id="d66c7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d66c7-131">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="d66c7-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="d66c7-132">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="d66c7-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d66c7-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d66c7-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="d66c7-134">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d66c7-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d66c7-135">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d66c7-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d66c7-136">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d66c7-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d66c7-137">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d66c7-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d66c7-138">\<binding></span><span class="sxs-lookup"><span data-stu-id="d66c7-138">\<binding></span></span>](../../../misc/binding.md)
