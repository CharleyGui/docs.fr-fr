---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 2c6b5de51e6508965daf6022a47d12d8d73f2a4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149125"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="8910b-102">\<add> de \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="8910b-102">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="8910b-103">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="8910b-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8910b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8910b-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8910b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8910b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8910b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8910b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8910b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8910b-107">Attributes</span></span>  
  
|<span data-ttu-id="8910b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8910b-108">Attribute</span></span>|<span data-ttu-id="8910b-109">Description</span><span class="sxs-lookup"><span data-stu-id="8910b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8910b-110">port</span><span class="sxs-lookup"><span data-stu-id="8910b-110">port</span></span>|<span data-ttu-id="8910b-111">Entier qui spécifie le numéro de port de communication par défaut.</span><span class="sxs-lookup"><span data-stu-id="8910b-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="8910b-112">scheme</span><span class="sxs-lookup"><span data-stu-id="8910b-112">scheme</span></span>|<span data-ttu-id="8910b-113">Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.</span><span class="sxs-lookup"><span data-stu-id="8910b-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8910b-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8910b-114">Child Elements</span></span>  

 <span data-ttu-id="8910b-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8910b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8910b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8910b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8910b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="8910b-117">Element</span></span>|<span data-ttu-id="8910b-118">Description</span><span class="sxs-lookup"><span data-stu-id="8910b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="8910b-119">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="8910b-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8910b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8910b-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
