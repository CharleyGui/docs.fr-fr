---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 0f1dfd523e593c82727354db7ce39ffc992bdfb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932804"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="a2f66-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a2f66-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="a2f66-102">Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a2f66-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="a2f66-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a2f66-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a2f66-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a2f66-104">\<bindings></span></span>  
<span data-ttu-id="a2f66-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a2f66-105">\<customBinding></span></span>  
<span data-ttu-id="a2f66-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a2f66-106">\<binding></span></span>  
<span data-ttu-id="a2f66-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a2f66-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f66-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f66-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f66-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2f66-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a2f66-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a2f66-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f66-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2f66-111">Attributes</span></span>  
  
|<span data-ttu-id="a2f66-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a2f66-112">Attribute</span></span>|<span data-ttu-id="a2f66-113">Description</span><span class="sxs-lookup"><span data-stu-id="a2f66-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2f66-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a2f66-114">protectionLevel</span></span>|<span data-ttu-id="a2f66-115">Définit la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="a2f66-115">Defines message-level security.</span></span> <span data-ttu-id="a2f66-116">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="a2f66-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a2f66-117">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="a2f66-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a2f66-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2f66-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a2f66-119">None Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="a2f66-119">-   None: No protection.</span></span><br /><span data-ttu-id="a2f66-120">Expéditeur Les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="a2f66-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a2f66-121">EncryptAndSign Les messages sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="a2f66-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="a2f66-122">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="a2f66-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="a2f66-123">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="a2f66-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f66-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2f66-124">Child Elements</span></span>  
 <span data-ttu-id="a2f66-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="a2f66-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f66-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2f66-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f66-127">Élément</span><span class="sxs-lookup"><span data-stu-id="a2f66-127">Element</span></span>|<span data-ttu-id="a2f66-128">Description</span><span class="sxs-lookup"><span data-stu-id="a2f66-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2f66-129">\<binding></span><span class="sxs-lookup"><span data-stu-id="a2f66-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a2f66-130">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a2f66-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2f66-131">Notes</span><span class="sxs-lookup"><span data-stu-id="a2f66-131">Remarks</span></span>  
 <span data-ttu-id="a2f66-132">Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données.</span><span class="sxs-lookup"><span data-stu-id="a2f66-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="a2f66-133">Plus spécifiquement, WCF fournit les mises à niveau de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a2f66-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="a2f66-134">La configuration de cette sécurité de transport est encapsulée par cet élément de configuration ainsi que par [ \<section sslStreamSecurity >](sslstreamsecurity.md), qui peut être configuré et ajouté à une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a2f66-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f66-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2f66-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="a2f66-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a2f66-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a2f66-137">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a2f66-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a2f66-138">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a2f66-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a2f66-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a2f66-139">\<customBinding></span></span>](custombinding.md)
