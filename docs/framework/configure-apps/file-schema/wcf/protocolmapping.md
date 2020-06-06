---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400022"
---
# \<protocolMapping>
<span data-ttu-id="d3e93-101">Représente une section de configuration permettant de définir un ensemble de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="d3e93-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="d3e93-102">Lors de la création de points de terminaison par défaut au moment de l’exécution, Windows Communication Foundation (WCF) examine les mappages configurés et décide de la liaison à utiliser pour une adresse de base particulière.</span><span class="sxs-lookup"><span data-stu-id="d3e93-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="d3e93-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e93-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e93-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d3e93-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e93-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d3e93-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e93-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3e93-106">Attributes</span></span>  
 <span data-ttu-id="d3e93-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d3e93-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3e93-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3e93-108">Child Elements</span></span>  
  
|<span data-ttu-id="d3e93-109">Élément</span><span class="sxs-lookup"><span data-stu-id="d3e93-109">Element</span></span>|<span data-ttu-id="d3e93-110">Description</span><span class="sxs-lookup"><span data-stu-id="d3e93-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="d3e93-111">Contient un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="d3e93-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e93-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3e93-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e93-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d3e93-113">Element</span></span>|<span data-ttu-id="d3e93-114">Description</span><span class="sxs-lookup"><span data-stu-id="d3e93-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="d3e93-115">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="d3e93-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d3e93-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3e93-116">Example</span></span>  
 <span data-ttu-id="d3e93-117">L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="d3e93-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="d3e93-118">Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="d3e93-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="d3e93-119">Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.</span><span class="sxs-lookup"><span data-stu-id="d3e93-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3e93-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e93-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
