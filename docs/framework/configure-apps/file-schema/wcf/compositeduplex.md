---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a5209efddd489f8cb04b3266e6ba0bb033eeae6c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176017"
---
# \<compositeDuplex>

<span data-ttu-id="a36b7-101">Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.</span><span class="sxs-lookup"><span data-stu-id="a36b7-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="a36b7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a36b7-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a36b7-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a36b7-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a36b7-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a36b7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a36b7-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="a36b7-105">Attributes</span></span>  
  
|<span data-ttu-id="a36b7-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="a36b7-106">Attribute</span></span>|<span data-ttu-id="a36b7-107">Description</span><span class="sxs-lookup"><span data-stu-id="a36b7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a36b7-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a36b7-108">clientBaseAddress</span></span>|<span data-ttu-id="a36b7-109">URI qui définit l'adresse du canal arrière en mode duplex.</span><span class="sxs-lookup"><span data-stu-id="a36b7-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="a36b7-110">Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.</span><span class="sxs-lookup"><span data-stu-id="a36b7-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="a36b7-111">Si cet attribut n’est pas défini, une adresse par défaut " `full qualified name+default port\TemporaryIndigoAddress\guid` " est générée.</span><span class="sxs-lookup"><span data-stu-id="a36b7-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="a36b7-112">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="a36b7-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a36b7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a36b7-113">Child Elements</span></span>  

 <span data-ttu-id="a36b7-114">None</span><span class="sxs-lookup"><span data-stu-id="a36b7-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a36b7-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a36b7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a36b7-116">Élément</span><span class="sxs-lookup"><span data-stu-id="a36b7-116">Element</span></span>|<span data-ttu-id="a36b7-117">Description</span><span class="sxs-lookup"><span data-stu-id="a36b7-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a36b7-118">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a36b7-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a36b7-119">Notes</span><span class="sxs-lookup"><span data-stu-id="a36b7-119">Remarks</span></span>  

 <span data-ttu-id="a36b7-120">Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP.</span><span class="sxs-lookup"><span data-stu-id="a36b7-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="a36b7-121">En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.</span><span class="sxs-lookup"><span data-stu-id="a36b7-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="a36b7-122">Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="a36b7-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="a36b7-123">Cette adresse cliente est fournie par l'attribut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="a36b7-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="a36b7-124">Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a36b7-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a36b7-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="a36b7-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a36b7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a36b7-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a36b7-127">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a36b7-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a36b7-128">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a36b7-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a36b7-129">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a36b7-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
