---
title: Exemples - WCF Services
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: 9c4c6c0083a685f2f85b01ed3a5bed377708dd13
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425463"
---
# <a name="services"></a><span data-ttu-id="ed309-102">Services</span><span class="sxs-lookup"><span data-stu-id="ed309-102">Services</span></span>

<span data-ttu-id="ed309-103">Cette section contient des exemples qui illustrent des services Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ed309-103">This section contains samples that demonstrate Windows Communication Foundation (WCF) services.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ed309-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ed309-104">In this section</span></span>

- <span data-ttu-id="ed309-105">[Hébergement](../../../../docs/framework/wcf/feature-details/hosting.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-105">[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)</span></span>\
<span data-ttu-id="ed309-106">Montre les services d’hébergement WCF.</span><span class="sxs-lookup"><span data-stu-id="ed309-106">Demonstrates hosting WCF services.</span></span>

- <span data-ttu-id="ed309-107">[Interopérabilité des services](service-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-107">[Service Interoperability](service-interoperability.md)</span></span>\
<span data-ttu-id="ed309-108">Illustre l’interaction entre WCF et d’autres technologies de service.</span><span class="sxs-lookup"><span data-stu-id="ed309-108">Demonstrates interaction between WCF and other service technologies.</span></span>

- <span data-ttu-id="ed309-109">[Comportements](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-109">[Behaviors](behaviors.md)</span></span>\
<span data-ttu-id="ed309-110">Illustre des comportements de service WCF.</span><span class="sxs-lookup"><span data-stu-id="ed309-110">Demonstrates WCF service behaviors.</span></span>

- <span data-ttu-id="ed309-111">[Sécurité du service](service-security.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-111">[Service Security](service-security.md)</span></span>\
<span data-ttu-id="ed309-112">Illustre la sécurité de service WCF.</span><span class="sxs-lookup"><span data-stu-id="ed309-112">Demonstrates WCF service security.</span></span>

- <span data-ttu-id="ed309-113">[Configuration simplifiée pour les Services WCF](simplified-configuration-for-wcf-services.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-113">[Simplified Configuration for WCF Services](simplified-configuration-for-wcf-services.md)</span></span>\
<span data-ttu-id="ed309-114">Montre comment implémenter et configurer un service classique et le client à l’aide de WCF.</span><span class="sxs-lookup"><span data-stu-id="ed309-114">Demonstrates how to implement and configure a typical service and client using WCF.</span></span>

- <span data-ttu-id="ed309-115">[Utilisation de points de terminaison Standard](usage-of-standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-115">[Usage of Standard Endpoints](usage-of-standard-endpoints.md)</span></span>\
<span data-ttu-id="ed309-116">Montre comment utiliser des points de terminaison standard dans des fichiers de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="ed309-116">Demonstrates how to use standard endpoints in service configuration files.</span></span>

- <span data-ttu-id="ed309-117">[Stratégie de Protection étendue](extended-protection-policy.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-117">[Extended Protection Policy](extended-protection-policy.md)</span></span>\
<span data-ttu-id="ed309-118">Illustre la protection étendue, une initiative de sécurité visant à se protéger des attaques de l'intercepteur (MITM, Man In The Middle).</span><span class="sxs-lookup"><span data-stu-id="ed309-118">Demonstrates Extended Protection, a security initiative for protecting against man-in-the-middle (MITM) attacks.</span></span>

- <span data-ttu-id="ed309-119">[Fabrique de canaux de configuration](configuration-channel-factory.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-119">[Configuration Channel Factory](configuration-channel-factory.md)</span></span>\
<span data-ttu-id="ed309-120">Illustre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="ed309-120">Demonstrates the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span>

- <span data-ttu-id="ed309-121">[Adressage](addressing.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-121">[Addressing](addressing.md)</span></span>\
<span data-ttu-id="ed309-122">Illustre divers aspects et fonctionnalités des adresses de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ed309-122">Demonstrates various aspects and features of endpoint addresses.</span></span>

- <span data-ttu-id="ed309-123">[Impératif](imperative.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-123">[Imperative](imperative.md)</span></span>\
<span data-ttu-id="ed309-124">Montre comment définir un <xref:System.ServiceModel.WSHttpBinding> pour un service à l’aide de code, au lieu de définir la liaison `wsHttpBinding` dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ed309-124">Demonstrates how to define a <xref:System.ServiceModel.WSHttpBinding> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span>

- <span data-ttu-id="ed309-125">[Plusieurs contrats](multiple-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-125">[Multiple Contracts](multiple-contracts.md)</span></span>\
<span data-ttu-id="ed309-126">Indique comment implémenter plusieurs contrats sur un service et comment configurer des points de terminaison permettant de communiquer avec chaque contrat implémenté.</span><span class="sxs-lookup"><span data-stu-id="ed309-126">Demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span>

- <span data-ttu-id="ed309-127">[Plusieurs points de terminaison](multiple-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-127">[Multiple Endpoints](multiple-endpoints.md)</span></span>\
<span data-ttu-id="ed309-128">Montre comment configurer plusieurs points de terminaison sur un service et comment communiquer avec chacun d'entre eux à partir d'un client.</span><span class="sxs-lookup"><span data-stu-id="ed309-128">Demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span>

- <span data-ttu-id="ed309-129">[Plusieurs points de terminaison sur un ListenUri unique](multiple-endpoints-at-a-single-listenuri.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-129">[Multiple Endpoints at a Single ListenUri](multiple-endpoints-at-a-single-listenuri.md)</span></span>\
<span data-ttu-id="ed309-130">Présente un service qui héberge plusieurs points de terminaison au niveau d'un `ListenUri` unique.</span><span class="sxs-lookup"><span data-stu-id="ed309-130">Demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span>

- <span data-ttu-id="ed309-131">[OperationContextScope](operationcontextscope.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-131">[OperationContextScope](operationcontextscope.md)</span></span>\
<span data-ttu-id="ed309-132">Montre comment envoyer des informations supplémentaires sur un appel WCF à l’aide d’en-têtes.</span><span class="sxs-lookup"><span data-stu-id="ed309-132">Demonstrates how to send extra information on a WCF call using headers.</span></span>

- <span data-ttu-id="ed309-133">[Description du service](service-description.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-133">[Service Description](service-description.md)</span></span>\
<span data-ttu-id="ed309-134">Illustre comment un service peut récupérer les informations relatives à sa description pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ed309-134">Demonstrates how a service can retrieve its service description information at runtime.</span></span>

- <span data-ttu-id="ed309-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)</span><span class="sxs-lookup"><span data-stu-id="ed309-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)</span></span>\
<span data-ttu-id="ed309-136">Montre comment utiliser le mode d'accès concurrentiel Reentrant sur une implémentation de service.</span><span class="sxs-lookup"><span data-stu-id="ed309-136">Demonstrates how to use the Reentrant concurrency mode on a service implementation.</span></span>
