---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736780"
---
# <a name="compositeduplex"></a><span data-ttu-id="a7c1a-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="a7c1a-101">\<compositeDuplex></span></span>
<span data-ttu-id="a7c1a-102">Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="a7c1a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7c1a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7c1a-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a7c1a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a7c1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="a7c1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="a7c1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a7c1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a7c1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="a7c1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="a7c1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="a7c1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c1a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7c1a-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7c1a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7c1a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7c1a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7c1a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7c1a-112">Attributes</span></span>  
  
|<span data-ttu-id="a7c1a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7c1a-113">Attribute</span></span>|<span data-ttu-id="a7c1a-114">Description</span><span class="sxs-lookup"><span data-stu-id="a7c1a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7c1a-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a7c1a-115">clientBaseAddress</span></span>|<span data-ttu-id="a7c1a-116">URI qui définit l'adresse du canal arrière en mode duplex.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="a7c1a-117">Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="a7c1a-118">Si cet attribut n’est pas défini, une adresse par défaut «`full qualified name+default port\TemporaryIndigoAddress\guid`» est générée.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="a7c1a-119">La valeur par défaut est `null`,</span><span class="sxs-lookup"><span data-stu-id="a7c1a-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7c1a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7c1a-120">Child Elements</span></span>  
 <span data-ttu-id="a7c1a-121">aucune.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7c1a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7c1a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a7c1a-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a7c1a-123">Element</span></span>|<span data-ttu-id="a7c1a-124">Description</span><span class="sxs-lookup"><span data-stu-id="a7c1a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7c1a-125">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="a7c1a-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="a7c1a-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7c1a-127">Notes</span><span class="sxs-lookup"><span data-stu-id="a7c1a-127">Remarks</span></span>  
 <span data-ttu-id="a7c1a-128">Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="a7c1a-129">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="a7c1a-130">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="a7c1a-131">Cette adresse cliente est fournie par l'attribut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="a7c1a-132">Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a7c1a-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7c1a-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7c1a-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a7c1a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7c1a-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a7c1a-135">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a7c1a-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7c1a-136">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a7c1a-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7c1a-137">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a7c1a-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a7c1a-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a7c1a-138">\<customBinding></span></span>](custombinding.md)
