---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397717"
---
# \<net.pipe>
<span data-ttu-id="82e72-102">Spécifie les paramètres de configuration du service d'activation du canal nommé, qui gère la durée de vie de la connexion du canal nommé et les demandes d'activation qui arrivent par des canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="82e72-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="82e72-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e72-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="82e72-104">Type</span><span class="sxs-lookup"><span data-stu-id="82e72-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82e72-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="82e72-105">Attributes and Elements</span></span>  
 <span data-ttu-id="82e72-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="82e72-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82e72-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="82e72-107">Attributes</span></span>  
  
|<span data-ttu-id="82e72-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="82e72-108">Attribute</span></span>|<span data-ttu-id="82e72-109">Description</span><span class="sxs-lookup"><span data-stu-id="82e72-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="82e72-110">Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage.</span><span class="sxs-lookup"><span data-stu-id="82e72-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="82e72-111">La valeur par défaut est 2.</span><span class="sxs-lookup"><span data-stu-id="82e72-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="82e72-112">Entier qui définit le nombre maximal de connexions qui peuvent attendre la distribution.</span><span class="sxs-lookup"><span data-stu-id="82e72-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="82e72-113">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="82e72-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="82e72-114"><xref:System.TimeSpan> qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="82e72-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="82e72-115">La valeur par défaut est « 00:00:10 ».</span><span class="sxs-lookup"><span data-stu-id="82e72-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82e72-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82e72-116">Child Elements</span></span>  
  
|<span data-ttu-id="82e72-117">Élément</span><span class="sxs-lookup"><span data-stu-id="82e72-117">Element</span></span>|<span data-ttu-id="82e72-118">Description</span><span class="sxs-lookup"><span data-stu-id="82e72-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="82e72-119">Collection d’éléments de configuration qui contiennent un `securityIdentifier` attribut permettant de spécifier des comptes d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="82e72-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82e72-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="82e72-120">Parent Elements</span></span>  
  
|<span data-ttu-id="82e72-121">Élément</span><span class="sxs-lookup"><span data-stu-id="82e72-121">Element</span></span>|<span data-ttu-id="82e72-122">Description</span><span class="sxs-lookup"><span data-stu-id="82e72-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="82e72-123">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="82e72-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82e72-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82e72-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
