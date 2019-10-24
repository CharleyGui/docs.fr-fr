---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773945"
---
# <a name="client"></a><span data-ttu-id="e096f-101">\<client ></span><span class="sxs-lookup"><span data-stu-id="e096f-101">\<client></span></span>
<span data-ttu-id="e096f-102">L'élément `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="e096f-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

<span data-ttu-id="e096f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e096f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e096f-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e096f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e096f-105">&nbsp; &nbsp; &nbsp; &nbsp; **\<client** ></span><span class="sxs-lookup"><span data-stu-id="e096f-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e096f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e096f-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e096f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e096f-107">Attributes and Elements</span></span>
 <span data-ttu-id="e096f-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e096f-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e096f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e096f-109">Attributes</span></span>
 <span data-ttu-id="e096f-110">aucune.</span><span class="sxs-lookup"><span data-stu-id="e096f-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e096f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e096f-111">Child Elements</span></span>

|<span data-ttu-id="e096f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e096f-112">Element</span></span>|<span data-ttu-id="e096f-113">Description</span><span class="sxs-lookup"><span data-stu-id="e096f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e096f-114">\<endpoint ></span><span class="sxs-lookup"><span data-stu-id="e096f-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="e096f-115">Contient une collection d’éléments de point de terminaison qui spécifient les points de terminaison auxquels ce client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="e096f-115">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[<span data-ttu-id="e096f-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="e096f-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="e096f-117">Contient des paramètres pour le traitement de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e096f-117">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e096f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e096f-118">Parent Elements</span></span>

|<span data-ttu-id="e096f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="e096f-119">Element</span></span>|<span data-ttu-id="e096f-120">Description</span><span class="sxs-lookup"><span data-stu-id="e096f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e096f-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e096f-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="e096f-122">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e096f-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e096f-123">Notes</span><span class="sxs-lookup"><span data-stu-id="e096f-123">Remarks</span></span>
 <span data-ttu-id="e096f-124">La section `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="e096f-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="e096f-125">Chaque point de terminaison répertorié dans la section client définit ses propres liaison, comportement et contrat.</span><span class="sxs-lookup"><span data-stu-id="e096f-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="e096f-126">Il est identifié uniquement par la combinaison des attributs `name` et `contract`.</span><span class="sxs-lookup"><span data-stu-id="e096f-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="e096f-127">Le code client spécifie le `name` permettant de se connecter à un point de terminaison pour le service que le client implémente.</span><span class="sxs-lookup"><span data-stu-id="e096f-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="e096f-128">Si l'attribut `name` est omis, le point de terminaison agit comme point de terminaison par défaut pour le contrat qu'il implémente.</span><span class="sxs-lookup"><span data-stu-id="e096f-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="e096f-129">De plus, cette section spécifie également des paramètres pour le traitement des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e096f-129">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="e096f-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="e096f-130">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e096f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e096f-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="e096f-132">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="e096f-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e096f-133">Clients</span><span class="sxs-lookup"><span data-stu-id="e096f-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
