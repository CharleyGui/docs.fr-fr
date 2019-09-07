---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397691"
---
# <a name="nettcp"></a><span data-ttu-id="0c5dc-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="0c5dc-102">\<net.tcp></span></span>
<span data-ttu-id="0c5dc-103">Spécifie les paramètres de configuration du service de partage de port NET.TCP, qui permet à plusieurs processus de partager le même port TCP.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
<span data-ttu-id="0c5dc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c5dc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c5dc-105">&nbsp;&nbsp;[ **\<System. serviceModel. activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="0c5dc-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="0c5dc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NET. TCP >**</span><span class="sxs-lookup"><span data-stu-id="0c5dc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c5dc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c5dc-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="0c5dc-108">Type</span><span class="sxs-lookup"><span data-stu-id="0c5dc-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c5dc-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c5dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c5dc-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c5dc-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c5dc-111">Attributes</span></span>  
  
|<span data-ttu-id="0c5dc-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c5dc-112">Attribute</span></span>|<span data-ttu-id="0c5dc-113">Description</span><span class="sxs-lookup"><span data-stu-id="0c5dc-113">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="0c5dc-114">Entier qui spécifie le nombre maximal de connexions en attente qui sont acceptées à partir de la connexion partagée, mais qui ne sont pas encore distribuées aux services Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0c5dc-114">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="0c5dc-115">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-115">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="0c5dc-116">Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-116">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="0c5dc-117">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-117">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="0c5dc-118">Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-118">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="0c5dc-119">Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-119">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="0c5dc-120">Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-120">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="0c5dc-121">Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-121">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="0c5dc-122">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-122">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0c5dc-123"><xref:System.TimeSpan> qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-123">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="0c5dc-124">La valeur par défaut est « 00:00:10 ».</span><span class="sxs-lookup"><span data-stu-id="0c5dc-124">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="0c5dc-125">Valeur booléenne qui indique si le service de partage de port utilise le service Microsoft Teredo pour écouter les ports TCP pour le compte des services WCF.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-125">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="0c5dc-126">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c5dc-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c5dc-127">Child Elements</span></span>  
  
|<span data-ttu-id="0c5dc-128">Élément</span><span class="sxs-lookup"><span data-stu-id="0c5dc-128">Element</span></span>|<span data-ttu-id="0c5dc-129">Description</span><span class="sxs-lookup"><span data-stu-id="0c5dc-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c5dc-130">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="0c5dc-130">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="0c5dc-131">Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-131">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c5dc-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c5dc-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0c5dc-133">Élément</span><span class="sxs-lookup"><span data-stu-id="0c5dc-133">Element</span></span>|<span data-ttu-id="0c5dc-134">Description</span><span class="sxs-lookup"><span data-stu-id="0c5dc-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c5dc-135">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0c5dc-135">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="0c5dc-136">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="0c5dc-136">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c5dc-137">Notes</span><span class="sxs-lookup"><span data-stu-id="0c5dc-137">Remarks</span></span>  
 <span data-ttu-id="0c5dc-138">Pour plus d’informations sur le partage de ports, consultez [partage de port Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="0c5dc-138">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="0c5dc-139">Pour comprendre comment configurer le service de partage de port, consultez [configuration du service de partage de ports net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="0c5dc-139">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5dc-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c5dc-140">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="0c5dc-141">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="0c5dc-141">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="0c5dc-142">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="0c5dc-142">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
