---
title: <add> de <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850380"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="c80a9-102">\<Ajouter > de \<la > protocolMapping</span><span class="sxs-lookup"><span data-stu-id="c80a9-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="c80a9-103">Représente un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et une liaison Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c80a9-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="c80a9-104">Lors de la création de points de terminaison par défaut au moment de l’exécution, WCF examine les mappages configurés et décide de la liaison à utiliser pour une adresse de base particulière.</span><span class="sxs-lookup"><span data-stu-id="c80a9-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="c80a9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c80a9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c80a9-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c80a9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c80a9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protocolMapping >** ](protocolmapping.md)</span><span class="sxs-lookup"><span data-stu-id="c80a9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)</span></span>\
<span data-ttu-id="c80a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="c80a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80a9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c80a9-109">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c80a9-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c80a9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c80a9-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c80a9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c80a9-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c80a9-112">Attributes</span></span>  
  
|<span data-ttu-id="c80a9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c80a9-113">Element</span></span>|<span data-ttu-id="c80a9-114">Description</span><span class="sxs-lookup"><span data-stu-id="c80a9-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c80a9-115">liaison</span><span class="sxs-lookup"><span data-stu-id="c80a9-115">binding</span></span>|<span data-ttu-id="c80a9-116">Chaîne qui spécifie le type de liaison à utiliser pour un point de terminaison pendant la création de points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="c80a9-116">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="c80a9-117">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c80a9-117">bindingConfiguration</span></span>|<span data-ttu-id="c80a9-118">Chaîne qui spécifie le nom de la section de configuration de liaison à référencer.</span><span class="sxs-lookup"><span data-stu-id="c80a9-118">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="c80a9-119">scheme</span><span class="sxs-lookup"><span data-stu-id="c80a9-119">scheme</span></span>|<span data-ttu-id="c80a9-120">Schéma de protocole de transport à utiliser pour le point de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="c80a9-120">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c80a9-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c80a9-121">Child Elements</span></span>  
 <span data-ttu-id="c80a9-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c80a9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c80a9-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c80a9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c80a9-124">Élément</span><span class="sxs-lookup"><span data-stu-id="c80a9-124">Element</span></span>|<span data-ttu-id="c80a9-125">Description</span><span class="sxs-lookup"><span data-stu-id="c80a9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c80a9-126">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="c80a9-126">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="c80a9-127">Représente une section de configuration pour la définition de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et des liaisons Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c80a9-127">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c80a9-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="c80a9-128">Example</span></span>  
 <span data-ttu-id="c80a9-129">L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="c80a9-129">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="c80a9-130">Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="c80a9-130">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="c80a9-131">Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.</span><span class="sxs-lookup"><span data-stu-id="c80a9-131">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c80a9-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c80a9-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
