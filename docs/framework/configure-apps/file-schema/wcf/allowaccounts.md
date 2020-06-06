---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398402"
---
# \<allowAccounts>
<span data-ttu-id="b8e75-101">Contient une collection d’éléments de configuration qui spécifient des comptes d’utilisateur pour les processus qui hébergent des services Windows Communication Foundation (WCF) et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="b8e75-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="b8e75-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8e75-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e75-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8e75-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e75-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8e75-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e75-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8e75-105">Attributes</span></span>  
 <span data-ttu-id="b8e75-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b8e75-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8e75-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8e75-107">Child Elements</span></span>  
  
|<span data-ttu-id="b8e75-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b8e75-108">Attribute</span></span>|<span data-ttu-id="b8e75-109">Description</span><span class="sxs-lookup"><span data-stu-id="b8e75-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="b8e75-110">Ajoute un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="b8e75-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e75-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8e75-111">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e75-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b8e75-112">Element</span></span>|<span data-ttu-id="b8e75-113">Description</span><span class="sxs-lookup"><span data-stu-id="b8e75-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8e75-114">[\<net.pipe>](net-pipe.md)ni[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="b8e75-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="b8e75-115">Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.</span><span class="sxs-lookup"><span data-stu-id="b8e75-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8e75-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8e75-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
