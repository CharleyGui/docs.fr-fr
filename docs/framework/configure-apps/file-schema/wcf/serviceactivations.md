---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855136"
---
# \<serviceActivations>

<span data-ttu-id="9b87e-101">Élément de configuration qui vous permet d’ajouter des paramètres qui définissent des paramètres d’activation de service virtuel mappés à vos types de service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9b87e-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="9b87e-102">Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="9b87e-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="9b87e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b87e-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b87e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b87e-104">Attributes and Elements</span></span>

<span data-ttu-id="9b87e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9b87e-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b87e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b87e-106">Attributes</span></span>

<span data-ttu-id="9b87e-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b87e-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b87e-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b87e-108">Child Elements</span></span>

|<span data-ttu-id="9b87e-109">Élément</span><span class="sxs-lookup"><span data-stu-id="9b87e-109">Element</span></span>|<span data-ttu-id="9b87e-110">Description</span><span class="sxs-lookup"><span data-stu-id="9b87e-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="9b87e-111">Ajoute un élément de configuration qui spécifie l'activation d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="9b87e-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b87e-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b87e-112">Parent Elements</span></span>

|<span data-ttu-id="9b87e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9b87e-113">Element</span></span>|<span data-ttu-id="9b87e-114">Description</span><span class="sxs-lookup"><span data-stu-id="9b87e-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="9b87e-115">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="9b87e-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b87e-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="9b87e-116">Remarks</span></span>

<span data-ttu-id="9b87e-117">L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="9b87e-117">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="9b87e-118">Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="9b87e-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="9b87e-119">Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="9b87e-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="9b87e-120">Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9b87e-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="9b87e-121">En outre, `serviceHostingEnvironment` est une section pouvant être héritée machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="9b87e-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="9b87e-122">Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9b87e-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="9b87e-123">L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="9b87e-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="9b87e-124">Elle requiert des extensions dans relativeAddress, par exemple. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="9b87e-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="9b87e-125">Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension.</span><span class="sxs-lookup"><span data-stu-id="9b87e-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="9b87e-126">En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.</span><span class="sxs-lookup"><span data-stu-id="9b87e-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b87e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b87e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
