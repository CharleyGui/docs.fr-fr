---
title: Vue d'ensemble de l'intégration à des applications COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c283e7cbc4cb4b8bc37dd1313480410df93a93bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596823"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="f2fed-102">Vue d'ensemble de l'intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="f2fed-102">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="f2fed-103">Windows Communication Foundation (WCF) fournit au développeur de code managé un environnement riche pour la création d’applications connectées.</span><span class="sxs-lookup"><span data-stu-id="f2fed-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="f2fed-104">Toutefois, si vous avez un investissement important dans du code COM non géré et que vous ne souhaitez pas effectuer la migration, vous pouvez toujours intégrer les services Web WCF directement dans votre code existant à l’aide du moniker de service WCF.</span><span class="sxs-lookup"><span data-stu-id="f2fed-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="f2fed-105">Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="f2fed-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="f2fed-106">Le moniker de service utilise un canal de communication WCF pour toutes les communications.</span><span class="sxs-lookup"><span data-stu-id="f2fed-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="f2fed-107">Les mécanismes de sécurité et d'identification de ce canal diffèrent de ceux utilisés sur les proxys standard COM et DCOM.</span><span class="sxs-lookup"><span data-stu-id="f2fed-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="f2fed-108">En outre, étant donné que le moniker de service utilise un canal de communication WCF, le délai d’attente par défaut est d’une minute pour tous les appels.</span><span class="sxs-lookup"><span data-stu-id="f2fed-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="f2fed-109">Le moniker de service est utilisé avec la `GetObject` fonction pour fournir au développeur non managé une approche fortement typée et spécifique à com pour l’appel de services Web WCF.</span><span class="sxs-lookup"><span data-stu-id="f2fed-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="f2fed-110">Cela nécessite une définition locale, visible par COM, du contrat de service Web WCF et de la liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f2fed-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="f2fed-111">À l’instar des autres clients WCF, le moniker de service doit construire un canal typé pour le service, bien que cette construction de canal se produise de manière transparente pour le programmeur COM sur le premier appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="f2fed-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="f2fed-112">En commun avec d’autres clients WCF, lors de l’utilisation du moniker, les applications spécifient l’adresse, la liaison et le contrat pour communiquer avec un service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="f2fed-113">Le contrat peut être spécifié (au choix) comme suit :</span><span class="sxs-lookup"><span data-stu-id="f2fed-113">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="f2fed-114">Contrat typé : le contrat est enregistré sur l'ordinateur client sous la forme d'un type visible par COM.</span><span class="sxs-lookup"><span data-stu-id="f2fed-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="f2fed-115">Contrat WSDL : le contrat est fourni sous forme de document WSDL.</span><span class="sxs-lookup"><span data-stu-id="f2fed-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="f2fed-116">Contrat MEX : le contrat est récupéré pendant l'exécution depuis un point de terminaison d'échange de métadonnées (Metadata Exchange, MEX).</span><span class="sxs-lookup"><span data-stu-id="f2fed-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="f2fed-117">Paramètres pris en charge par le moniker de service</span><span class="sxs-lookup"><span data-stu-id="f2fed-117">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="f2fed-118">Le tableau suivant contient les paramètres pris en charge par le moniker de service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-118">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="f2fed-119">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f2fed-119">Parameter</span></span>|<span data-ttu-id="f2fed-120">Description</span><span class="sxs-lookup"><span data-stu-id="f2fed-120">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="f2fed-121">Adresse URL du service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-121">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="f2fed-122">Nom de la section de liaison à partir de la configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="f2fed-122">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="f2fed-123">Instance de liaison nommée à partir de la section de liaison nommée.</span><span class="sxs-lookup"><span data-stu-id="f2fed-123">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="f2fed-124">Identificateur d'interface (IID) qui représente le contrat de service ou le nom de contrat (obtenu à partir de l'échange MEX).</span><span class="sxs-lookup"><span data-stu-id="f2fed-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="f2fed-125">Document WSDL qui offre une autre définition pour le contrat.</span><span class="sxs-lookup"><span data-stu-id="f2fed-125">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="f2fed-126">Identité de nom principal de serveur (Server Principal Name, SPN) à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="f2fed-127">Identité de nom principal d'utilisateur (User Principal Name, UPN) à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="f2fed-128">Identité DNS à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-128">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="f2fed-129">Adresse URL du point de terminaison MEX du service.</span><span class="sxs-lookup"><span data-stu-id="f2fed-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="f2fed-130">Nom de section de liaison depuis la configuration d'application avec laquelle se connecter au point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="f2fed-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="f2fed-131">Instance de liaison nommée à partir de la section de liaison nommée avec laquelle se connecter au point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="f2fed-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="f2fed-132">Espace de noms du nom de section de liaison obtenu à partir de l’échange MEX récupéré.</span><span class="sxs-lookup"><span data-stu-id="f2fed-132">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="f2fed-133">Espace de noms du contrat obtenu à partir de l'échange MEX récupéré.</span><span class="sxs-lookup"><span data-stu-id="f2fed-133">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="f2fed-134">Identité SPN à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="f2fed-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="f2fed-135">Identité UPN à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="f2fed-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="f2fed-136">Identité DNS à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="f2fed-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="f2fed-137">Indiquez le type de sérialiseur utilisé : « xml » ou « contrat de données ».</span><span class="sxs-lookup"><span data-stu-id="f2fed-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="f2fed-138">Même en cas d’utilisation avec des clients entièrement basés sur COM, le moniker de service requiert WCF et le support .NET Framework 2,0 pour être installé sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="f2fed-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="f2fed-139">Il est également essentiel que les applications clientes qui utilisent le moniker de service chargent la version appropriée de l'exécution .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2fed-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="f2fed-140">Lorsque le moniker de service est utilisé dans le cadre d'applications Office, un fichier de configuration peut s'avérer nécessaire afin d'assurer la chargement de la version d'infrastructure adéquate.</span><span class="sxs-lookup"><span data-stu-id="f2fed-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="f2fed-141">Par exemple, pour Excel, vous devez insérer le texte suivant dans un fichier Excel.exe.config, puis enregistrer ce fichier dans le même répertoire que le fichier Excel.exe :</span><span class="sxs-lookup"><span data-stu-id="f2fed-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="f2fed-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="f2fed-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="f2fed-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2fed-143">See also</span></span>

- [<span data-ttu-id="f2fed-144">Comment : inscrire et configurer un moniker de service</span><span class="sxs-lookup"><span data-stu-id="f2fed-144">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
