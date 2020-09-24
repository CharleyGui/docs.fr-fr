---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b3234bfa60cd1e3c88778951fc27301c615c84ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148956"
---
# \<client>

<span data-ttu-id="4e8de-101">L'élément `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="4e8de-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="4e8de-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e8de-102">Syntax</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e8de-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e8de-103">Attributes and Elements</span></span>

 <span data-ttu-id="4e8de-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e8de-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e8de-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e8de-105">Attributes</span></span>

 <span data-ttu-id="4e8de-106">None</span><span class="sxs-lookup"><span data-stu-id="4e8de-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e8de-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e8de-107">Child Elements</span></span>

|<span data-ttu-id="4e8de-108">Élément</span><span class="sxs-lookup"><span data-stu-id="4e8de-108">Element</span></span>|<span data-ttu-id="4e8de-109">Description</span><span class="sxs-lookup"><span data-stu-id="4e8de-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="4e8de-110">Contient une collection d’éléments de point de terminaison qui spécifient les points de terminaison auxquels ce client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="4e8de-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="4e8de-111">Contient des paramètres pour le traitement de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4e8de-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e8de-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e8de-112">Parent Elements</span></span>

|<span data-ttu-id="4e8de-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4e8de-113">Element</span></span>|<span data-ttu-id="4e8de-114">Description</span><span class="sxs-lookup"><span data-stu-id="4e8de-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="4e8de-115">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4e8de-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e8de-116">Notes</span><span class="sxs-lookup"><span data-stu-id="4e8de-116">Remarks</span></span>

 <span data-ttu-id="4e8de-117">La section `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="4e8de-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="4e8de-118">Chaque point de terminaison répertorié dans la section client définit ses propres liaison, comportement et contrat.</span><span class="sxs-lookup"><span data-stu-id="4e8de-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="4e8de-119">Il est identifié uniquement par la combinaison des attributs `name` et `contract`.</span><span class="sxs-lookup"><span data-stu-id="4e8de-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="4e8de-120">Le code client spécifie le `name` permettant de se connecter à un point de terminaison pour le service que le client implémente.</span><span class="sxs-lookup"><span data-stu-id="4e8de-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="4e8de-121">Si l'attribut `name` est omis, le point de terminaison agit comme point de terminaison par défaut pour le contrat qu'il implémente.</span><span class="sxs-lookup"><span data-stu-id="4e8de-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="4e8de-122">De plus, cette section spécifie également des paramètres pour le traitement des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4e8de-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="4e8de-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e8de-123">Example</span></span>

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a><span data-ttu-id="4e8de-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e8de-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="4e8de-125">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="4e8de-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="4e8de-126">Clients</span><span class="sxs-lookup"><span data-stu-id="4e8de-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
