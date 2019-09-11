---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850331"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="40444-102">\<Ajouter > de \<la > serviceActivations</span><span class="sxs-lookup"><span data-stu-id="40444-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="40444-103">Élément de configuration qui vous permet de définir des paramètres d’activation de service virtuel mappés à vos types de service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="40444-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="40444-104">Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="40444-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="40444-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40444-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40444-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="40444-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="40444-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="40444-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="40444-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceActivations >** ](serviceactivations.md)</span><span class="sxs-lookup"><span data-stu-id="40444-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)</span></span>\
<span data-ttu-id="40444-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="40444-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="40444-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40444-110">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40444-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40444-111">Attributes and Elements</span></span>

<span data-ttu-id="40444-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40444-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="40444-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="40444-113">Attributes</span></span>

|<span data-ttu-id="40444-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="40444-114">Attribute</span></span>|<span data-ttu-id="40444-115">Description</span><span class="sxs-lookup"><span data-stu-id="40444-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="40444-116">factory</span><span class="sxs-lookup"><span data-stu-id="40444-116">factory</span></span>|<span data-ttu-id="40444-117">Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.</span><span class="sxs-lookup"><span data-stu-id="40444-117">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="40444-118">service</span><span class="sxs-lookup"><span data-stu-id="40444-118">service</span></span>|<span data-ttu-id="40444-119">Le ServiceType qui implémente le service (Typename qualifié complet ou Typename court (s’il est placé dans le dossier App_Code).</span><span class="sxs-lookup"><span data-stu-id="40444-119">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="40444-120">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="40444-120">relativeAddress</span></span>|<span data-ttu-id="40444-121">L'adresse relative dans l'application IIS active (par exemple « Service.svc ».</span><span class="sxs-lookup"><span data-stu-id="40444-121">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="40444-122">Dans WCF 4.0 cette adresse relative doit contenir une des extensions de fichiers connues (.svc, .xamlx,…). Aucun fichier physique ne doit exister pour relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="40444-122">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40444-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40444-123">Child Elements</span></span>

<span data-ttu-id="40444-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="40444-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40444-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40444-125">Parent Elements</span></span>

|<span data-ttu-id="40444-126">Élément</span><span class="sxs-lookup"><span data-stu-id="40444-126">Element</span></span>|<span data-ttu-id="40444-127">Description</span><span class="sxs-lookup"><span data-stu-id="40444-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40444-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="40444-128">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="40444-129">Section de configuration qui décrit les paramètres d'activation.</span><span class="sxs-lookup"><span data-stu-id="40444-129">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40444-130">Notes</span><span class="sxs-lookup"><span data-stu-id="40444-130">Remarks</span></span>

<span data-ttu-id="40444-131">L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="40444-131">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="40444-132">Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="40444-132">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="40444-133">Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="40444-133">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="40444-134">Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="40444-134">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="40444-135">En outre, `serviceHostingEnvironment` est une section pouvant être héritée machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="40444-135">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="40444-136">Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="40444-136">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="40444-137">L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="40444-137">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="40444-138">Elle requiert des extensions dans relativeAddress, par exemple. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="40444-138">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="40444-139">Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension.</span><span class="sxs-lookup"><span data-stu-id="40444-139">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="40444-140">En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.</span><span class="sxs-lookup"><span data-stu-id="40444-140">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="40444-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40444-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
