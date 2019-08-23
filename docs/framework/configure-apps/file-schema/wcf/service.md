---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936525"
---
# <a name="service"></a><span data-ttu-id="18b59-101">\<service></span><span class="sxs-lookup"><span data-stu-id="18b59-101">\<service></span></span>
<span data-ttu-id="18b59-102">L'élément `service` contient les paramètres d'un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="18b59-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="18b59-103">Il contient également les points de terminaison qui exposent le service.</span><span class="sxs-lookup"><span data-stu-id="18b59-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="18b59-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18b59-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18b59-105">\<services></span><span class="sxs-lookup"><span data-stu-id="18b59-105">\<services></span></span>  
<span data-ttu-id="18b59-106">\<service></span><span class="sxs-lookup"><span data-stu-id="18b59-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b59-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18b59-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18b59-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="18b59-108">Attributes and Elements</span></span>  
 <span data-ttu-id="18b59-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="18b59-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18b59-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="18b59-110">Attributes</span></span>  
  
|<span data-ttu-id="18b59-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="18b59-111">Attribute</span></span>|<span data-ttu-id="18b59-112">Description</span><span class="sxs-lookup"><span data-stu-id="18b59-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18b59-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="18b59-113">behaviorConfiguration</span></span>|<span data-ttu-id="18b59-114">Chaîne qui contient le nom du comportement à utiliser pour instancier le service.</span><span class="sxs-lookup"><span data-stu-id="18b59-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="18b59-115">Le nom du comportement doit être dans la portée, au niveau où le service est défini.</span><span class="sxs-lookup"><span data-stu-id="18b59-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="18b59-116">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="18b59-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="18b59-117">name</span><span class="sxs-lookup"><span data-stu-id="18b59-117">name</span></span>|<span data-ttu-id="18b59-118">Attribut de chaîne requis indiquant le type de service à instancier.</span><span class="sxs-lookup"><span data-stu-id="18b59-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="18b59-119">Ce paramètre doit correspondre à un type valide.</span><span class="sxs-lookup"><span data-stu-id="18b59-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="18b59-120">Le format doit être `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="18b59-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18b59-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="18b59-121">Child Elements</span></span>  
  
|<span data-ttu-id="18b59-122">Élément</span><span class="sxs-lookup"><span data-stu-id="18b59-122">Element</span></span>|<span data-ttu-id="18b59-123">Description</span><span class="sxs-lookup"><span data-stu-id="18b59-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18b59-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="18b59-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="18b59-125">Collection d’éléments `endpoint` qui exposent ce service.</span><span class="sxs-lookup"><span data-stu-id="18b59-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="18b59-126">\<host></span><span class="sxs-lookup"><span data-stu-id="18b59-126">\<host></span></span>](host.md)|<span data-ttu-id="18b59-127">Spécifie l'hôte de cette instance de service.</span><span class="sxs-lookup"><span data-stu-id="18b59-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="18b59-128">Cet élément est de type <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="18b59-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18b59-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="18b59-129">Parent Elements</span></span>  
  
|<span data-ttu-id="18b59-130">Élément</span><span class="sxs-lookup"><span data-stu-id="18b59-130">Element</span></span>|<span data-ttu-id="18b59-131">Description</span><span class="sxs-lookup"><span data-stu-id="18b59-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18b59-132">\<services></span><span class="sxs-lookup"><span data-stu-id="18b59-132">\<services></span></span>](services.md)|<span data-ttu-id="18b59-133">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="18b59-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18b59-134">Notes</span><span class="sxs-lookup"><span data-stu-id="18b59-134">Remarks</span></span>  
 <span data-ttu-id="18b59-135">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="18b59-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="18b59-136">Un assembly peut contenir n'importe quel nombre de services.</span><span class="sxs-lookup"><span data-stu-id="18b59-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="18b59-137">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="18b59-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="18b59-138">Cette section et son contenu définissent le contrat de service, le comportement et les points de terminaison de ce service en particulier.</span><span class="sxs-lookup"><span data-stu-id="18b59-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="18b59-139">L'élément `behaviorConfiguration` est également facultatif.</span><span class="sxs-lookup"><span data-stu-id="18b59-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="18b59-140">Il identifie le comportement que le service adopte.</span><span class="sxs-lookup"><span data-stu-id="18b59-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="18b59-141">Le comportement spécifié dans cet attribut doit créer une liaison avec un comportement dans la portée du même fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="18b59-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="18b59-142">Chaque service expose un ou plusieurs points de terminaison, qui ont leurs propres adresse et liaison.</span><span class="sxs-lookup"><span data-stu-id="18b59-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="18b59-143">Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.</span><span class="sxs-lookup"><span data-stu-id="18b59-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="18b59-144">La liaison est liée aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="18b59-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="18b59-145">L'attribut `name` décrit la section dans laquelle la liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="18b59-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="18b59-146">L'attribut `bindingConfiguration` définit quelle configuration de la section de liaison est utilisée.</span><span class="sxs-lookup"><span data-stu-id="18b59-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="18b59-147">Une section de liaison peut définir plusieurs configurations.</span><span class="sxs-lookup"><span data-stu-id="18b59-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18b59-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="18b59-148">Example</span></span>  
 <span data-ttu-id="18b59-149">Il s'agit d'un exemple de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="18b59-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18b59-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18b59-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="18b59-151">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="18b59-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
