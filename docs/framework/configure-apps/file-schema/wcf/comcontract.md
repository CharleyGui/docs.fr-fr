---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850029"
---
# \<comContract>
<span data-ttu-id="6dbae-101">Spécifie un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="6dbae-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="6dbae-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dbae-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dbae-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6dbae-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6dbae-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6dbae-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dbae-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6dbae-105">Attributes</span></span>  
  
|<span data-ttu-id="6dbae-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6dbae-106">Attribute</span></span>|<span data-ttu-id="6dbae-107">Description</span><span class="sxs-lookup"><span data-stu-id="6dbae-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6dbae-108">contract</span><span class="sxs-lookup"><span data-stu-id="6dbae-108">contract</span></span>|<span data-ttu-id="6dbae-109">Chaîne qui contient le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="6dbae-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="6dbae-110">name</span><span class="sxs-lookup"><span data-stu-id="6dbae-110">name</span></span>|<span data-ttu-id="6dbae-111">Chaîne qui contient le type de nom.</span><span class="sxs-lookup"><span data-stu-id="6dbae-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="6dbae-112">espace de noms</span><span class="sxs-lookup"><span data-stu-id="6dbae-112">namespace</span></span>|<span data-ttu-id="6dbae-113">Chaîne qui contient l'espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="6dbae-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="6dbae-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="6dbae-114">requiresSession</span></span>|<span data-ttu-id="6dbae-115">Valeur booléenne qui spécifie si le contrat ne peut être utilisé que sur des liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="6dbae-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="6dbae-116">Lorsque le service est initialisé, l’exécution d’intégration garantit que ce paramètre est cohérent avec le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6dbae-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="6dbae-117">Une exception est générée en cas de conflit avec une ou plusieurs liaisons du contrat.</span><span class="sxs-lookup"><span data-stu-id="6dbae-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="6dbae-118">Si cette propriété a la valeur `false`, qu'un canal unidirectionnel est utilisé et qu'un paramètre [out] est présent, une exception est également levée.</span><span class="sxs-lookup"><span data-stu-id="6dbae-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dbae-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6dbae-119">Child Elements</span></span>  
  
|<span data-ttu-id="6dbae-120">Élément</span><span class="sxs-lookup"><span data-stu-id="6dbae-120">Element</span></span>|<span data-ttu-id="6dbae-121">Description</span><span class="sxs-lookup"><span data-stu-id="6dbae-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6dbae-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="6dbae-122">persistableTypes</span></span>|<span data-ttu-id="6dbae-123">Tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="6dbae-123">All the persistable types.</span></span>|  
|<span data-ttu-id="6dbae-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="6dbae-124">userDefinedTypes</span></span>|<span data-ttu-id="6dbae-125">Collection de types définis par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="6dbae-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="6dbae-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="6dbae-126">exposedMethods</span></span>|<span data-ttu-id="6dbae-127">Collection de méthodes COM+ exposées lorsque l’interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="6dbae-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6dbae-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6dbae-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6dbae-129">Élément</span><span class="sxs-lookup"><span data-stu-id="6dbae-129">Element</span></span>|<span data-ttu-id="6dbae-130">Description</span><span class="sxs-lookup"><span data-stu-id="6dbae-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6dbae-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="6dbae-131">comContracts</span></span>|<span data-ttu-id="6dbae-132">Contient une collection d’éléments `comContract`.</span><span class="sxs-lookup"><span data-stu-id="6dbae-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dbae-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="6dbae-133">Remarks</span></span>  
 <span data-ttu-id="6dbae-134">Les contrats de service d’intégration COM+ sont actuellement restreints à l' `http://tempuri.org` espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6dbae-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="6dbae-135">Toutefois, vous pouvez spécifier des alternatives à l'aide de la section `comContracts`, ainsi que l'élément `comContract` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6dbae-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="6dbae-136">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms, le nom de contrat et les types définis par l'utilisateur à inclure, ainsi que d'autres paramètres pour un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="6dbae-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="6dbae-137">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="6dbae-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbae-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dbae-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="6dbae-139">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="6dbae-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="6dbae-140">Comment : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="6dbae-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
