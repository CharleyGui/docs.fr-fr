---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926598"
---
# <a name="allowaccounts"></a><span data-ttu-id="8536a-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="8536a-101">\<allowAccounts></span></span>
<span data-ttu-id="8536a-102">Contient une collection d’éléments de configuration qui spécifient des comptes d’utilisateur pour les processus qui hébergent des services Windows Communication Foundation (WCF) et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="8536a-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="8536a-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="8536a-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8536a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8536a-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8536a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8536a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8536a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8536a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8536a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8536a-107">Attributes</span></span>  
 <span data-ttu-id="8536a-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8536a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8536a-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8536a-109">Child Elements</span></span>  
  
|<span data-ttu-id="8536a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8536a-110">Attribute</span></span>|<span data-ttu-id="8536a-111">Description</span><span class="sxs-lookup"><span data-stu-id="8536a-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8536a-112">\<add></span><span class="sxs-lookup"><span data-stu-id="8536a-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="8536a-113">Ajoute un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="8536a-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8536a-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8536a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8536a-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8536a-115">Element</span></span>|<span data-ttu-id="8536a-116">Description</span><span class="sxs-lookup"><span data-stu-id="8536a-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8536a-117">NET. pipe > ou [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="8536a-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="8536a-118">Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.</span><span class="sxs-lookup"><span data-stu-id="8536a-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8536a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8536a-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
