---
title: <transport> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735961"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="5f826-102">\<transport> de \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="5f826-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="5f826-103">Définit les paramètres de sécurité de transport pour un canal nommé.</span><span class="sxs-lookup"><span data-stu-id="5f826-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="5f826-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f826-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f826-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5f826-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5f826-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5f826-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f826-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5f826-107">Attributes</span></span>  
  
|<span data-ttu-id="5f826-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f826-108">Attribute</span></span>|<span data-ttu-id="5f826-109">Description</span><span class="sxs-lookup"><span data-stu-id="5f826-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f826-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5f826-110">protectionLevel</span></span>|<span data-ttu-id="5f826-111">Définit le niveau de protection du canal nommé.</span><span class="sxs-lookup"><span data-stu-id="5f826-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="5f826-112">La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert.</span><span class="sxs-lookup"><span data-stu-id="5f826-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5f826-113">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="5f826-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="5f826-114">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f826-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5f826-115">-None : aucune protection.</span><span class="sxs-lookup"><span data-stu-id="5f826-115">-   None: No protection.</span></span><br /><span data-ttu-id="5f826-116">-Sign : les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="5f826-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5f826-117">-EncryptAndSign : les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="5f826-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="5f826-118">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="5f826-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f826-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5f826-119">Child Elements</span></span>  
 <span data-ttu-id="5f826-120">Aucune</span><span class="sxs-lookup"><span data-stu-id="5f826-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f826-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5f826-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5f826-122">Élément</span><span class="sxs-lookup"><span data-stu-id="5f826-122">Element</span></span>|<span data-ttu-id="5f826-123">Description</span><span class="sxs-lookup"><span data-stu-id="5f826-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="5f826-124">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="5f826-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f826-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f826-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="5f826-126">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="5f826-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5f826-127">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5f826-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5f826-128">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="5f826-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5f826-129">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="5f826-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
