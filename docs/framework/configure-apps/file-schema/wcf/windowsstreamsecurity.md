---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735897"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="a8411-101">\<par windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="a8411-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="a8411-102">Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a8411-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="a8411-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8411-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8411-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a8411-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a8411-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="a8411-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="a8411-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a8411-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a8411-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="a8411-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="a8411-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**par windowsstreamsecurity >**</span><span class="sxs-lookup"><span data-stu-id="a8411-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8411-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8411-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8411-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a8411-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a8411-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a8411-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8411-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a8411-112">Attributes</span></span>  
  
|<span data-ttu-id="a8411-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a8411-113">Attribute</span></span>|<span data-ttu-id="a8411-114">Description</span><span class="sxs-lookup"><span data-stu-id="a8411-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8411-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a8411-115">protectionLevel</span></span>|<span data-ttu-id="a8411-116">Définit la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="a8411-116">Defines message-level security.</span></span> <span data-ttu-id="a8411-117">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="a8411-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a8411-118">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="a8411-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a8411-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8411-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a8411-120">-None : aucune protection.</span><span class="sxs-lookup"><span data-stu-id="a8411-120">-   None: No protection.</span></span><br /><span data-ttu-id="a8411-121">-Sign : les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="a8411-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a8411-122">-EncryptAndSign : les messages sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="a8411-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="a8411-123">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="a8411-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="a8411-124">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="a8411-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8411-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a8411-125">Child Elements</span></span>  
 <span data-ttu-id="a8411-126">aucune.</span><span class="sxs-lookup"><span data-stu-id="a8411-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8411-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a8411-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a8411-128">Élément</span><span class="sxs-lookup"><span data-stu-id="a8411-128">Element</span></span>|<span data-ttu-id="a8411-129">Description</span><span class="sxs-lookup"><span data-stu-id="a8411-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8411-130">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="a8411-130">\<binding></span></span>](bindings.md)|<span data-ttu-id="a8411-131">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a8411-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8411-132">Notes</span><span class="sxs-lookup"><span data-stu-id="a8411-132">Remarks</span></span>  
 <span data-ttu-id="a8411-133">Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données.</span><span class="sxs-lookup"><span data-stu-id="a8411-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="a8411-134">Plus spécifiquement, WCF fournit les mises à niveau de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a8411-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="a8411-135">La configuration de cette sécurité de transport est encapsulée par cet élément de configuration ainsi que par [\<> section sslStreamSecurity](sslstreamsecurity.md), qui peut être configurée et ajoutée à une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a8411-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8411-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8411-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="a8411-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a8411-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8411-138">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a8411-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a8411-139">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a8411-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a8411-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8411-140">\<customBinding></span></span>](custombinding.md)
