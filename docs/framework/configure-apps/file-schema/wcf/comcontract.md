---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850029"
---
# <a name="comcontract"></a><span data-ttu-id="1e78b-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="1e78b-101">\<comContract></span></span>
<span data-ttu-id="1e78b-102">Spécifie un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="1e78b-102">Specifies a COM+ integration service contract.</span></span>  
  
<span data-ttu-id="1e78b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e78b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e78b-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1e78b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1e78b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comconventions**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="1e78b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="1e78b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<comContract >**</span><span class="sxs-lookup"><span data-stu-id="1e78b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e78b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e78b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e78b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1e78b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e78b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1e78b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e78b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1e78b-110">Attributes</span></span>  
  
|<span data-ttu-id="1e78b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1e78b-111">Attribute</span></span>|<span data-ttu-id="1e78b-112">Description</span><span class="sxs-lookup"><span data-stu-id="1e78b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e78b-113">contrat</span><span class="sxs-lookup"><span data-stu-id="1e78b-113">contract</span></span>|<span data-ttu-id="1e78b-114">Chaîne qui contient le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="1e78b-114">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="1e78b-115">name</span><span class="sxs-lookup"><span data-stu-id="1e78b-115">name</span></span>|<span data-ttu-id="1e78b-116">Chaîne qui contient le type de nom.</span><span class="sxs-lookup"><span data-stu-id="1e78b-116">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="1e78b-117">namespace</span><span class="sxs-lookup"><span data-stu-id="1e78b-117">namespace</span></span>|<span data-ttu-id="1e78b-118">Chaîne qui contient l'espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="1e78b-118">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="1e78b-119">requiresSession</span><span class="sxs-lookup"><span data-stu-id="1e78b-119">requiresSession</span></span>|<span data-ttu-id="1e78b-120">Valeur booléenne qui spécifie si le contrat ne peut être utilisé que sur des liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="1e78b-120">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="1e78b-121">Lorsque le service est initialisé, l’exécution d’intégration garantit que ce paramètre est cohérent avec le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1e78b-121">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="1e78b-122">Une exception est générée en cas de conflit avec une ou plusieurs liaisons du contrat.</span><span class="sxs-lookup"><span data-stu-id="1e78b-122">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="1e78b-123">Si cette propriété a la valeur `false`, qu'un canal unidirectionnel est utilisé et qu'un paramètre [out] est présent, une exception est également levée.</span><span class="sxs-lookup"><span data-stu-id="1e78b-123">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e78b-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1e78b-124">Child Elements</span></span>  
  
|<span data-ttu-id="1e78b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="1e78b-125">Element</span></span>|<span data-ttu-id="1e78b-126">Description</span><span class="sxs-lookup"><span data-stu-id="1e78b-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e78b-127">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="1e78b-127">persistableTypes</span></span>|<span data-ttu-id="1e78b-128">Tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="1e78b-128">All the persistable types.</span></span>|  
|<span data-ttu-id="1e78b-129">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="1e78b-129">userDefinedTypes</span></span>|<span data-ttu-id="1e78b-130">Collection de types définis par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="1e78b-130">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="1e78b-131">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="1e78b-131">exposedMethods</span></span>|<span data-ttu-id="1e78b-132">Collection de méthodes COM+ exposées lorsque l’interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="1e78b-132">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e78b-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1e78b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1e78b-134">Élément</span><span class="sxs-lookup"><span data-stu-id="1e78b-134">Element</span></span>|<span data-ttu-id="1e78b-135">Description</span><span class="sxs-lookup"><span data-stu-id="1e78b-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e78b-136">comContracts</span><span class="sxs-lookup"><span data-stu-id="1e78b-136">comContracts</span></span>|<span data-ttu-id="1e78b-137">Contient une collection d’éléments `comContract`.</span><span class="sxs-lookup"><span data-stu-id="1e78b-137">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e78b-138">Notes</span><span class="sxs-lookup"><span data-stu-id="1e78b-138">Remarks</span></span>  
 <span data-ttu-id="1e78b-139">Les contrats de service d’intégration com+ sont actuellement `http://tempuri.org` restreints à l’espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1e78b-139">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="1e78b-140">Toutefois, vous pouvez spécifier des alternatives à l'aide de la section `comContracts`, ainsi que l'élément `comContract` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1e78b-140">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="1e78b-141">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms, le nom de contrat et les types définis par l'utilisateur à inclure, ainsi que d'autres paramètres pour un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="1e78b-141">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="1e78b-142">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="1e78b-142">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e78b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e78b-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="1e78b-144">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="1e78b-144">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="1e78b-145">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="1e78b-145">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="1e78b-146">Guide pratique pour Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="1e78b-146">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
