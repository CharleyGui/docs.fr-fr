---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920032"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="38f7c-102">\<Ajouter > de \<la > serviceActivations</span><span class="sxs-lookup"><span data-stu-id="38f7c-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="38f7c-103">Élément de configuration qui vous permet de définir des paramètres d’activation de service virtuel mappés à vos types de service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="38f7c-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="38f7c-104">Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="38f7c-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="38f7c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="38f7c-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="38f7c-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="38f7c-106">\<serviceHostingEnvironment></span></span>

## <a name="syntax"></a><span data-ttu-id="38f7c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38f7c-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38f7c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38f7c-108">Attributes and Elements</span></span>

<span data-ttu-id="38f7c-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38f7c-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="38f7c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38f7c-110">Attributes</span></span>

|<span data-ttu-id="38f7c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="38f7c-111">Attribute</span></span>|<span data-ttu-id="38f7c-112">Description</span><span class="sxs-lookup"><span data-stu-id="38f7c-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="38f7c-113">factory</span><span class="sxs-lookup"><span data-stu-id="38f7c-113">factory</span></span>|<span data-ttu-id="38f7c-114">Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.</span><span class="sxs-lookup"><span data-stu-id="38f7c-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="38f7c-115">service</span><span class="sxs-lookup"><span data-stu-id="38f7c-115">service</span></span>|<span data-ttu-id="38f7c-116">Le ServiceType qui implémente le service (Typename qualifié complet ou Typename court (s’il est placé dans le dossier App_Code).</span><span class="sxs-lookup"><span data-stu-id="38f7c-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="38f7c-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="38f7c-117">relativeAddress</span></span>|<span data-ttu-id="38f7c-118">L'adresse relative dans l'application IIS active (par exemple « Service.svc ».</span><span class="sxs-lookup"><span data-stu-id="38f7c-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="38f7c-119">Dans WCF 4.0 cette adresse relative doit contenir une des extensions de fichiers connues (.svc, .xamlx,…). Aucun fichier physique ne doit exister pour relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="38f7c-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="38f7c-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38f7c-120">Child Elements</span></span>

<span data-ttu-id="38f7c-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38f7c-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38f7c-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38f7c-122">Parent Elements</span></span>

|<span data-ttu-id="38f7c-123">Élément</span><span class="sxs-lookup"><span data-stu-id="38f7c-123">Element</span></span>|<span data-ttu-id="38f7c-124">Description</span><span class="sxs-lookup"><span data-stu-id="38f7c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38f7c-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="38f7c-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="38f7c-126">Section de configuration qui décrit les paramètres d'activation.</span><span class="sxs-lookup"><span data-stu-id="38f7c-126">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38f7c-127">Notes</span><span class="sxs-lookup"><span data-stu-id="38f7c-127">Remarks</span></span>

<span data-ttu-id="38f7c-128">L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="38f7c-128">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="38f7c-129">Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="38f7c-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="38f7c-130">Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="38f7c-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="38f7c-131">Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="38f7c-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="38f7c-132">En outre, `serviceHostingEnvironment` est une section pouvant être héritée machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="38f7c-132">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="38f7c-133">Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="38f7c-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="38f7c-134">L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="38f7c-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="38f7c-135">Elle requiert des extensions dans relativeAddress, par exemple. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="38f7c-135">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="38f7c-136">Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension.</span><span class="sxs-lookup"><span data-stu-id="38f7c-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="38f7c-137">En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.</span><span class="sxs-lookup"><span data-stu-id="38f7c-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f7c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38f7c-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
