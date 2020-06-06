---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735897"
---
# \<windowsStreamSecurity>
<span data-ttu-id="e8edc-101">Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e8edc-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="e8edc-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8edc-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8edc-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e8edc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e8edc-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e8edc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8edc-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e8edc-105">Attributes</span></span>  
  
|<span data-ttu-id="e8edc-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e8edc-106">Attribute</span></span>|<span data-ttu-id="e8edc-107">Description</span><span class="sxs-lookup"><span data-stu-id="e8edc-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8edc-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="e8edc-108">protectionLevel</span></span>|<span data-ttu-id="e8edc-109">Définit la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="e8edc-109">Defines message-level security.</span></span> <span data-ttu-id="e8edc-110">La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert.</span><span class="sxs-lookup"><span data-stu-id="e8edc-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e8edc-111">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="e8edc-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="e8edc-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8edc-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8edc-113">-None : aucune protection.</span><span class="sxs-lookup"><span data-stu-id="e8edc-113">-   None: No protection.</span></span><br /><span data-ttu-id="e8edc-114">-Sign : les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="e8edc-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="e8edc-115">-EncryptAndSign : les messages sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="e8edc-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="e8edc-116">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="e8edc-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="e8edc-117">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="e8edc-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8edc-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8edc-118">Child Elements</span></span>  
 <span data-ttu-id="e8edc-119">Aucune</span><span class="sxs-lookup"><span data-stu-id="e8edc-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8edc-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8edc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e8edc-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e8edc-121">Element</span></span>|<span data-ttu-id="e8edc-122">Description</span><span class="sxs-lookup"><span data-stu-id="e8edc-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e8edc-123">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e8edc-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8edc-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8edc-124">Remarks</span></span>  
 <span data-ttu-id="e8edc-125">Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données.</span><span class="sxs-lookup"><span data-stu-id="e8edc-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="e8edc-126">Plus spécifiquement, WCF fournit les mises à niveau de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e8edc-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="e8edc-127">La configuration de cette sécurité de transport est encapsulée par cet élément de configuration ainsi que par [\<sslStreamSecurity>](sslstreamsecurity.md) , qui peut être configuré et ajouté à une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e8edc-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8edc-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8edc-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="e8edc-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e8edc-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e8edc-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="e8edc-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e8edc-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e8edc-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
