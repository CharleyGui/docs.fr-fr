---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201640"
---
# \<allowAccounts>

<span data-ttu-id="bf9e1-101">Contient une collection d’éléments de configuration qui spécifient des comptes d’utilisateur pour les processus qui hébergent des services Windows Communication Foundation (WCF) et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="bf9e1-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="bf9e1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf9e1-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf9e1-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bf9e1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="bf9e1-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bf9e1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf9e1-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf9e1-105">Attributes</span></span>  

 <span data-ttu-id="bf9e1-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bf9e1-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf9e1-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf9e1-107">Child Elements</span></span>  
  
|<span data-ttu-id="bf9e1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bf9e1-108">Attribute</span></span>|<span data-ttu-id="bf9e1-109">Description</span><span class="sxs-lookup"><span data-stu-id="bf9e1-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="bf9e1-110">Ajoute un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="bf9e1-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf9e1-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf9e1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="bf9e1-112">Élément</span><span class="sxs-lookup"><span data-stu-id="bf9e1-112">Element</span></span>|<span data-ttu-id="bf9e1-113">Description</span><span class="sxs-lookup"><span data-stu-id="bf9e1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf9e1-114">[\<net.pipe>](net-pipe.md) ni [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="bf9e1-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="bf9e1-115">Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.</span><span class="sxs-lookup"><span data-stu-id="bf9e1-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf9e1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf9e1-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
