---
title: Activation basée sur la configuration dans les services IIS et WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 5e1672f4dd67950178c95d3e043e16072fcd0ef4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593579"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="979b8-102">Activation basée sur la configuration dans les services IIS et WAS</span><span class="sxs-lookup"><span data-stu-id="979b8-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="979b8-103">Normalement, lors de l’hébergement d’un service Windows Communication Foundation (WCF) sous Internet Information Services (IIS) ou WAS (Windows Process Activation Service), vous devez fournir un fichier. svc.</span><span class="sxs-lookup"><span data-stu-id="979b8-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="979b8-104">Le fichier .svc contient le nom du service et une fabrique hôte de service personnalisée facultative.</span><span class="sxs-lookup"><span data-stu-id="979b8-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="979b8-105">Ce fichier supplémentaire facilite encore la gestion.</span><span class="sxs-lookup"><span data-stu-id="979b8-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="979b8-106">Grâce à la fonctionnalité d’activation basée sur la configuration, le fichier .svc et, par conséquent, les surcharges associées ne sont plus indispensables.</span><span class="sxs-lookup"><span data-stu-id="979b8-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="979b8-107">Activation basée sur la configuration</span><span class="sxs-lookup"><span data-stu-id="979b8-107">Configuration-Based Activation</span></span>

<span data-ttu-id="979b8-108">L'activation basée sur la configuration prend les métadonnées qui étaient placées dans le fichier .svc et les met dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="979b8-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="979b8-109">Dans l' `serviceHostingEnvironment` élément<> il existe un `serviceActivations` élément <>.</span><span class="sxs-lookup"><span data-stu-id="979b8-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="979b8-110">Dans le <`serviceActivations`> élément est un ou plusieurs `add` éléments <>, un pour chaque service hébergé.</span><span class="sxs-lookup"><span data-stu-id="979b8-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="979b8-111">L' `add` élément <> contient des attributs qui vous permettent de définir l’adresse relative du service et le type de service ou une fabrique d’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="979b8-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="979b8-112">L'exemple de code de configuration suivant montre comment cette section est utilisée.</span><span class="sxs-lookup"><span data-stu-id="979b8-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="979b8-113">Chaque <`add` élément> doit spécifier un service ou un attribut Factory.</span><span class="sxs-lookup"><span data-stu-id="979b8-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="979b8-114">Il est possible de spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="979b8-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="979b8-115">Grâce à ce code dans le fichier Web.config, vous pouvez placer le code source du service dans le répertoire App_Code de l'application ou un assembly compilé dans le répertoire Bin de l'application.</span><span class="sxs-lookup"><span data-stu-id="979b8-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="979b8-116">Lors d'une activation basée sur la configuration, le code inline dans les fichiers .svc n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="979b8-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="979b8-117">L' `relativeAddress` attribut doit être défini sur une adresse relative telle que « \<sub-directory> /service.svc » ou « ~/ \< Sub-Directory/Service. svc ».</span><span class="sxs-lookup"><span data-stu-id="979b8-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="979b8-118">Une exception de configuration est levée si vous inscrivez une adresse relative sans extension connue, associée à WCF.</span><span class="sxs-lookup"><span data-stu-id="979b8-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="979b8-119">L'adresse relative spécifiée est relative à la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="979b8-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="979b8-120">En raison du modèle hiérarchique de configuration, les adresses relatives enregistrées au niveau de l'ordinateur et du site sont héritées par les applications virtuelles.</span><span class="sxs-lookup"><span data-stu-id="979b8-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="979b8-121">Les inscriptions dans un fichier de configuration sont prioritaires sur les paramètres d'un fichier .svc, .xamlx, .xoml ou autre.</span><span class="sxs-lookup"><span data-stu-id="979b8-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="979b8-122">Toute '\' (barre oblique inverse) qui se trouve dans un URI envoyé aux services IIS/WAS est automatiquement convertie en '/' (barre oblique).</span><span class="sxs-lookup"><span data-stu-id="979b8-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="979b8-123">Si une adresse relative contenant un signe '\' est ajoutée et que vous envoyez à IIS un URI utilisant cette adresse relative, la barre oblique inverse est convertie en barre oblique et IIS ne peut pas le faire correspondre à l'adresse relative.</span><span class="sxs-lookup"><span data-stu-id="979b8-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="979b8-124">IIS envoie des informations de suivi qui indiquent qu'aucune correspondance n'a été trouvée.</span><span class="sxs-lookup"><span data-stu-id="979b8-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="979b8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="979b8-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="979b8-126">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="979b8-126">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="979b8-127">Vue d'ensemble de l'hébergement de services de workflow</span><span class="sxs-lookup"><span data-stu-id="979b8-127">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="979b8-128">[Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="979b8-128">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
