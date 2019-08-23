---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926068"
---
# <a name="compositeduplex"></a><span data-ttu-id="ee2db-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="ee2db-101">\<compositeDuplex></span></span>
<span data-ttu-id="ee2db-102">Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.</span><span class="sxs-lookup"><span data-stu-id="ee2db-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="ee2db-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee2db-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ee2db-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ee2db-104">\<bindings></span></span>  
<span data-ttu-id="ee2db-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ee2db-105">\<customBinding></span></span>  
<span data-ttu-id="ee2db-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="ee2db-106">\<binding></span></span>  
<span data-ttu-id="ee2db-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="ee2db-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2db-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee2db-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee2db-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee2db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee2db-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee2db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee2db-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee2db-111">Attributes</span></span>  
  
|<span data-ttu-id="ee2db-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee2db-112">Attribute</span></span>|<span data-ttu-id="ee2db-113">Description</span><span class="sxs-lookup"><span data-stu-id="ee2db-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee2db-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="ee2db-114">clientBaseAddress</span></span>|<span data-ttu-id="ee2db-115">URI qui définit l'adresse du canal arrière en mode duplex.</span><span class="sxs-lookup"><span data-stu-id="ee2db-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="ee2db-116">Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.</span><span class="sxs-lookup"><span data-stu-id="ee2db-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="ee2db-117">Si cet attribut n’est pas défini, une adresse par`full qualified name+default port\TemporaryIndigoAddress\guid`défaut "" est générée.</span><span class="sxs-lookup"><span data-stu-id="ee2db-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="ee2db-118">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="ee2db-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee2db-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee2db-119">Child Elements</span></span>  
 <span data-ttu-id="ee2db-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="ee2db-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee2db-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee2db-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ee2db-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ee2db-122">Element</span></span>|<span data-ttu-id="ee2db-123">Description</span><span class="sxs-lookup"><span data-stu-id="ee2db-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee2db-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="ee2db-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ee2db-125">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ee2db-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2db-126">Notes</span><span class="sxs-lookup"><span data-stu-id="ee2db-126">Remarks</span></span>  
 <span data-ttu-id="ee2db-127">Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="ee2db-128">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="ee2db-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="ee2db-129">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="ee2db-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="ee2db-130">Cette adresse cliente est fournie par l'attribut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="ee2db-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="ee2db-131">Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ee2db-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee2db-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee2db-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ee2db-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee2db-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ee2db-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ee2db-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee2db-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="ee2db-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ee2db-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="ee2db-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ee2db-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ee2db-137">\<customBinding></span></span>](custombinding.md)
