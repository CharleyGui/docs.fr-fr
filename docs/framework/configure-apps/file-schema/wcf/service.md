---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: dcc32f5aa055942408a3f01d37b5aa27ac0f51ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173768"
---
# \<service>

<span data-ttu-id="3ffc5-101">L'élément `service` contient les paramètres d'un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ffc5-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="3ffc5-102">Il contient également les points de terminaison qui exposent le service.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="3ffc5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ffc5-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ffc5-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3ffc5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3ffc5-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ffc5-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="3ffc5-106">Attributes</span></span>  
  
|<span data-ttu-id="3ffc5-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="3ffc5-107">Attribute</span></span>|<span data-ttu-id="3ffc5-108">Description</span><span class="sxs-lookup"><span data-stu-id="3ffc5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ffc5-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ffc5-109">behaviorConfiguration</span></span>|<span data-ttu-id="3ffc5-110">Chaîne qui contient le nom du comportement à utiliser pour instancier le service.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="3ffc5-111">Le nom du comportement doit être dans la portée, au niveau où le service est défini.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="3ffc5-112">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="3ffc5-113">name</span><span class="sxs-lookup"><span data-stu-id="3ffc5-113">name</span></span>|<span data-ttu-id="3ffc5-114">Attribut de chaîne requis indiquant le type de service à instancier.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="3ffc5-115">Ce paramètre doit correspondre à un type valide.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="3ffc5-116">Le format doit être `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="3ffc5-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ffc5-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3ffc5-117">Child Elements</span></span>  
  
|<span data-ttu-id="3ffc5-118">Élément</span><span class="sxs-lookup"><span data-stu-id="3ffc5-118">Element</span></span>|<span data-ttu-id="3ffc5-119">Description</span><span class="sxs-lookup"><span data-stu-id="3ffc5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="3ffc5-120">Collection d’éléments `endpoint` qui exposent ce service.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="3ffc5-121">Spécifie l'hôte de cette instance de service.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="3ffc5-122">Cet élément est de type <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ffc5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3ffc5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ffc5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3ffc5-124">Element</span></span>|<span data-ttu-id="3ffc5-125">Description</span><span class="sxs-lookup"><span data-stu-id="3ffc5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="3ffc5-126">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ffc5-127">Notes</span><span class="sxs-lookup"><span data-stu-id="3ffc5-127">Remarks</span></span>  

 <span data-ttu-id="3ffc5-128">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ffc5-129">Un assembly peut contenir n'importe quel nombre de services.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="3ffc5-130">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3ffc5-131">Cette section et son contenu définissent le contrat de service, le comportement et les points de terminaison de ce service en particulier.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3ffc5-132">L'élément `behaviorConfiguration` est également facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="3ffc5-133">Il identifie le comportement que le service adopte.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="3ffc5-134">Le comportement spécifié dans cet attribut doit créer une liaison avec un comportement dans la portée du même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="3ffc5-135">Chaque service expose un ou plusieurs points de terminaison, qui ont leurs propres adresse et liaison.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="3ffc5-136">Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="3ffc5-137">La liaison est liée aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3ffc5-138">L'attribut `name` décrit la section dans laquelle la liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="3ffc5-139">L'attribut `bindingConfiguration` définit quelle configuration de la section de liaison est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="3ffc5-140">Une section de liaison peut définir plusieurs configurations.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ffc5-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ffc5-141">Example</span></span>  

 <span data-ttu-id="3ffc5-142">Il s'agit d'un exemple de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="3ffc5-142">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="3ffc5-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ffc5-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="3ffc5-144">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="3ffc5-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
