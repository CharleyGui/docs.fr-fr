---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398402"
---
# <a name="allowaccounts"></a><span data-ttu-id="f3b8c-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="f3b8c-101">\<allowAccounts></span></span>
<span data-ttu-id="f3b8c-102">Contient une collection d’éléments de configuration qui spécifient des comptes d’utilisateur pour les processus qui hébergent des services Windows Communication Foundation (WCF) et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="f3b8c-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="f3b8c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3b8c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3b8c-104">&nbsp;&nbsp;[ **\<System. serviceModel. activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="f3b8c-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="f3b8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="f3b8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="f3b8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**</span><span class="sxs-lookup"><span data-stu-id="f3b8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b8c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3b8c-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3b8c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f3b8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3b8c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f3b8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3b8c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f3b8c-110">Attributes</span></span>  
 <span data-ttu-id="f3b8c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f3b8c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3b8c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f3b8c-112">Child Elements</span></span>  
  
|<span data-ttu-id="f3b8c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f3b8c-113">Attribute</span></span>|<span data-ttu-id="f3b8c-114">Description</span><span class="sxs-lookup"><span data-stu-id="f3b8c-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f3b8c-115">\<add></span><span class="sxs-lookup"><span data-stu-id="f3b8c-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="f3b8c-116">Ajoute un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="f3b8c-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3b8c-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f3b8c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f3b8c-118">Élément</span><span class="sxs-lookup"><span data-stu-id="f3b8c-118">Element</span></span>|<span data-ttu-id="f3b8c-119">Description</span><span class="sxs-lookup"><span data-stu-id="f3b8c-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3b8c-120">NET. pipe > ou [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="f3b8c-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="f3b8c-121">Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.</span><span class="sxs-lookup"><span data-stu-id="f3b8c-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3b8c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3b8c-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
