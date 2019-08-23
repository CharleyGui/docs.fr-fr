---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: ef980c86efad4fda86cf62148e50688fd22afe49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926090"
---
# <a name="comcontract"></a><span data-ttu-id="bd386-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="bd386-101">\<comContract></span></span>
<span data-ttu-id="bd386-102">Spécifie un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="bd386-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="bd386-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd386-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd386-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="bd386-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd386-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd386-105">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd386-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bd386-106">Attributes and Elements</span></span>  
 <span data-ttu-id="bd386-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bd386-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd386-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="bd386-108">Attributes</span></span>  
  
|<span data-ttu-id="bd386-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="bd386-109">Attribute</span></span>|<span data-ttu-id="bd386-110">Description</span><span class="sxs-lookup"><span data-stu-id="bd386-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd386-111">contrat</span><span class="sxs-lookup"><span data-stu-id="bd386-111">contract</span></span>|<span data-ttu-id="bd386-112">Chaîne qui contient le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="bd386-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="bd386-113">name</span><span class="sxs-lookup"><span data-stu-id="bd386-113">name</span></span>|<span data-ttu-id="bd386-114">Chaîne qui contient le type de nom.</span><span class="sxs-lookup"><span data-stu-id="bd386-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="bd386-115">namespace</span><span class="sxs-lookup"><span data-stu-id="bd386-115">namespace</span></span>|<span data-ttu-id="bd386-116">Chaîne qui contient l'espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="bd386-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="bd386-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="bd386-117">requiresSession</span></span>|<span data-ttu-id="bd386-118">Valeur booléenne qui spécifie si le contrat ne peut être utilisé que sur des liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="bd386-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="bd386-119">Lorsque le service est initialisé, l’exécution d’intégration garantit que ce paramètre est cohérent avec le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bd386-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="bd386-120">Une exception est générée en cas de conflit avec une ou plusieurs liaisons du contrat.</span><span class="sxs-lookup"><span data-stu-id="bd386-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="bd386-121">Si cette propriété a la valeur `false`, qu'un canal unidirectionnel est utilisé et qu'un paramètre [out] est présent, une exception est également levée.</span><span class="sxs-lookup"><span data-stu-id="bd386-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd386-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bd386-122">Child Elements</span></span>  
  
|<span data-ttu-id="bd386-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bd386-123">Element</span></span>|<span data-ttu-id="bd386-124">Description</span><span class="sxs-lookup"><span data-stu-id="bd386-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd386-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="bd386-125">persistableTypes</span></span>|<span data-ttu-id="bd386-126">Tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="bd386-126">All the persistable types.</span></span>|  
|<span data-ttu-id="bd386-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="bd386-127">userDefinedTypes</span></span>|<span data-ttu-id="bd386-128">Collection de types définis par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bd386-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="bd386-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="bd386-129">exposedMethods</span></span>|<span data-ttu-id="bd386-130">Collection de méthodes COM+ exposées lorsque l’interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="bd386-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd386-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bd386-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bd386-132">Élément</span><span class="sxs-lookup"><span data-stu-id="bd386-132">Element</span></span>|<span data-ttu-id="bd386-133">Description</span><span class="sxs-lookup"><span data-stu-id="bd386-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd386-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="bd386-134">comContracts</span></span>|<span data-ttu-id="bd386-135">Contient une collection d’éléments `comContract`.</span><span class="sxs-lookup"><span data-stu-id="bd386-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd386-136">Notes</span><span class="sxs-lookup"><span data-stu-id="bd386-136">Remarks</span></span>  
 <span data-ttu-id="bd386-137">Les contrats de service d’intégration com+ sont actuellement `http://tempuri.org` restreints à l’espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bd386-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="bd386-138">Toutefois, vous pouvez spécifier des alternatives à l'aide de la section `comContracts`, ainsi que l'élément `comContract` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="bd386-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="bd386-139">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms, le nom de contrat et les types définis par l'utilisateur à inclure, ainsi que d'autres paramètres pour un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bd386-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="bd386-140">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="bd386-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd386-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd386-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="bd386-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="bd386-142">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="bd386-143">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="bd386-143">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="bd386-144">Guide pratique pour Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="bd386-144">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
