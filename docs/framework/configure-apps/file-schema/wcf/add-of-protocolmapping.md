---
title: <add> de <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 46ba21b65f524f88bfce81739f0cd73040a2ad45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205007"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="ef47d-102">\<add> de \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="ef47d-102">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="ef47d-103">Représente un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et une liaison Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ef47d-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="ef47d-104">Lors de la création de points de terminaison par défaut au moment de l’exécution, WCF examine les mappages configurés et décide de la liaison à utiliser pour une adresse de base particulière.</span><span class="sxs-lookup"><span data-stu-id="ef47d-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ef47d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef47d-105">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef47d-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ef47d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ef47d-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ef47d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef47d-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ef47d-108">Attributes</span></span>  
  
|<span data-ttu-id="ef47d-109">Élément</span><span class="sxs-lookup"><span data-stu-id="ef47d-109">Element</span></span>|<span data-ttu-id="ef47d-110">Description</span><span class="sxs-lookup"><span data-stu-id="ef47d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef47d-111">binding</span><span class="sxs-lookup"><span data-stu-id="ef47d-111">binding</span></span>|<span data-ttu-id="ef47d-112">Chaîne qui spécifie le type de liaison à utiliser pour un point de terminaison pendant la création de points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="ef47d-112">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="ef47d-113">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef47d-113">bindingConfiguration</span></span>|<span data-ttu-id="ef47d-114">Chaîne qui spécifie le nom de la section de configuration de liaison à référencer.</span><span class="sxs-lookup"><span data-stu-id="ef47d-114">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="ef47d-115">scheme</span><span class="sxs-lookup"><span data-stu-id="ef47d-115">scheme</span></span>|<span data-ttu-id="ef47d-116">Schéma de protocole de transport à utiliser pour le point de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="ef47d-116">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef47d-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ef47d-117">Child Elements</span></span>  

 <span data-ttu-id="ef47d-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ef47d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef47d-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ef47d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef47d-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ef47d-120">Element</span></span>|<span data-ttu-id="ef47d-121">Description</span><span class="sxs-lookup"><span data-stu-id="ef47d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="ef47d-122">Représente une section de configuration pour la définition de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et des liaisons Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ef47d-122">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef47d-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef47d-123">Example</span></span>  

 <span data-ttu-id="ef47d-124">L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ef47d-124">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="ef47d-125">Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ef47d-125">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="ef47d-126">Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.</span><span class="sxs-lookup"><span data-stu-id="ef47d-126">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="ef47d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef47d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
