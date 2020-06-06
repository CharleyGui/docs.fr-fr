---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397691"
---
# \<net.tcp>
<span data-ttu-id="1f200-102">Spécifie les paramètres de configuration du service de partage de port NET.TCP, qui permet à plusieurs processus de partager le même port TCP.</span><span class="sxs-lookup"><span data-stu-id="1f200-102">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="1f200-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f200-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="1f200-104">Type</span><span class="sxs-lookup"><span data-stu-id="1f200-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f200-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1f200-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1f200-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1f200-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f200-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f200-107">Attributes</span></span>  
  
|<span data-ttu-id="1f200-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1f200-108">Attribute</span></span>|<span data-ttu-id="1f200-109">Description</span><span class="sxs-lookup"><span data-stu-id="1f200-109">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="1f200-110">Entier qui spécifie le nombre maximal de connexions en attente qui sont acceptées à partir de la connexion partagée, mais qui ne sont pas encore distribuées aux services Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1f200-110">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="1f200-111">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="1f200-111">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="1f200-112">Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage.</span><span class="sxs-lookup"><span data-stu-id="1f200-112">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="1f200-113">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="1f200-113">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="1f200-114">Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application.</span><span class="sxs-lookup"><span data-stu-id="1f200-114">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="1f200-115">Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="1f200-115">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="1f200-116">Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions.</span><span class="sxs-lookup"><span data-stu-id="1f200-116">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="1f200-117">Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota.</span><span class="sxs-lookup"><span data-stu-id="1f200-117">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="1f200-118">La valeur par défaut est de 10.</span><span class="sxs-lookup"><span data-stu-id="1f200-118">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1f200-119"><xref:System.TimeSpan> qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="1f200-119">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="1f200-120">La valeur par défaut est « 00:00:10 ».</span><span class="sxs-lookup"><span data-stu-id="1f200-120">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="1f200-121">Valeur booléenne qui indique si le service de partage de port utilise le service Microsoft Teredo pour écouter les ports TCP pour le compte des services WCF.</span><span class="sxs-lookup"><span data-stu-id="1f200-121">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="1f200-122">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="1f200-122">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f200-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f200-123">Child Elements</span></span>  
  
|<span data-ttu-id="1f200-124">Élément</span><span class="sxs-lookup"><span data-stu-id="1f200-124">Element</span></span>|<span data-ttu-id="1f200-125">Description</span><span class="sxs-lookup"><span data-stu-id="1f200-125">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="1f200-126">Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="1f200-126">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f200-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f200-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1f200-128">Élément</span><span class="sxs-lookup"><span data-stu-id="1f200-128">Element</span></span>|<span data-ttu-id="1f200-129">Description</span><span class="sxs-lookup"><span data-stu-id="1f200-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="1f200-130">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1f200-130">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f200-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="1f200-131">Remarks</span></span>  
 <span data-ttu-id="1f200-132">Pour plus d’informations sur le partage de ports, consultez [partage de port Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="1f200-132">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="1f200-133">Pour comprendre comment configurer le service de partage de port, consultez [configuration du service de partage de ports net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="1f200-133">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f200-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f200-134">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="1f200-135">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1f200-135">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="1f200-136">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1f200-136">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
