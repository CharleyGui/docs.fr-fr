---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399537"
---
# \<soapProcessing>

<span data-ttu-id="7bdad-101">Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.</span><span class="sxs-lookup"><span data-stu-id="7bdad-101">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="7bdad-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bdad-102">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bdad-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7bdad-103">Attributes and elements</span></span>  
  
<span data-ttu-id="7bdad-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7bdad-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bdad-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7bdad-105">Attributes</span></span>  
  
|                   | <span data-ttu-id="7bdad-106">Description</span><span class="sxs-lookup"><span data-stu-id="7bdad-106">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="7bdad-107">Valeur booléenne qui spécifie si les messages doivent être marshalés entre des versions de message SOAP.</span><span class="sxs-lookup"><span data-stu-id="7bdad-107">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="7bdad-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7bdad-108">Child elements</span></span>

<span data-ttu-id="7bdad-109">Aucune</span><span class="sxs-lookup"><span data-stu-id="7bdad-109">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7bdad-110">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7bdad-110">Parent elements</span></span>

|     | <span data-ttu-id="7bdad-111">Description</span><span class="sxs-lookup"><span data-stu-id="7bdad-111">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="7bdad-112">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7bdad-112">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7bdad-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="7bdad-113">Remarks</span></span>

<span data-ttu-id="7bdad-114">Le traitement SOAP est le processus par lequel les messages sont convertis entre des versions de message.</span><span class="sxs-lookup"><span data-stu-id="7bdad-114">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="7bdad-115">Le service de routage Windows Communication Foundation (WCF) peut convertir les messages d’un protocole à un autre.</span><span class="sxs-lookup"><span data-stu-id="7bdad-115">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="7bdad-116">Si les versions des messages entrant et sortant sont différentes, un nouveau message est créé dans la version correcte.</span><span class="sxs-lookup"><span data-stu-id="7bdad-116">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="7bdad-117">Le traitement des messages d'un <xref:System.ServiceModel.Channels.MessageVersion> à un autre est accompli en construisant un nouveau message WCF qui contient le corps et les en-têtes pertinents du message WCF entrant.</span><span class="sxs-lookup"><span data-stu-id="7bdad-117">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="7bdad-118">Les en-têtes spécifiques à l'adressage ou reconnus au niveau du routeur ne sont pas utilisés pendant la création du nouveau message WCF car ils sont de versions différentes (dans le cas d'en-têtes d'adressage) ou ont été traités dans le cadre de la communication entre le client et le routeur.</span><span class="sxs-lookup"><span data-stu-id="7bdad-118">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="7bdad-119">Le placement d'un en-tête dans le message sortant dépend de son balisage comme étant compris au moment où il traverse la couche du canal entrant.</span><span class="sxs-lookup"><span data-stu-id="7bdad-119">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="7bdad-120">Les en-têtes non reconnus (tels que les en-têtes personnalisés) ne sont pas supprimés et traversent donc le service de routage en étant copiés dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="7bdad-120">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="7bdad-121">Le corps du message est copié dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="7bdad-121">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="7bdad-122">Le message est ensuite envoyé via le canal de sortie ; les en-têtes et autres données d'enveloppe spécifiques à ce protocole de communication/transport sont alors créés et ajoutés.</span><span class="sxs-lookup"><span data-stu-id="7bdad-122">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="7bdad-123">Ces étapes de traitement s'exécutent lorsque le comportement de traitement SOAP est spécifié.</span><span class="sxs-lookup"><span data-stu-id="7bdad-123">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="7bdad-124">Ce [\<soapProcessingExtension>](soapprocessing.md) comportement est un comportement de point de terminaison qui est appliqué à tous les points de terminaison client (sortants) au démarrage du service de routage.</span><span class="sxs-lookup"><span data-stu-id="7bdad-124">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="7bdad-125">par défaut, le [\<routing>](routing-of-servicebehavior.md) comportement crée et attache un nouveau [\<soapProcessingExtension>](soapprocessing.md) comportement avec ayant la `processMessages` valeur `true` pour chaque point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="7bdad-125">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="7bdad-126">Si vous utilisez un protocole non reconnu par le service de routage ou souhaitez remplacer le comportement de traitement par défaut, vous pouvez désactiver le traitement SOAP pour l'intégralité du service de routage ou pour des points de terminaison particuliers.</span><span class="sxs-lookup"><span data-stu-id="7bdad-126">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="7bdad-127">Pour désactiver le traitement SOAP pour l’intégralité du service de routage sur tous les points de terminaison, affectez `soapProcessing` à l’attribut du comportement la valeur [\<routing>](routing-of-servicebehavior.md) `false` .</span><span class="sxs-lookup"><span data-stu-id="7bdad-127">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="7bdad-128">Pour désactiver le traitement SOAP pour un point de terminaison particulier, utilisez ce comportement et affectez à son attribut `processMessages` la valeur `false`, puis attachez ce comportement au point de terminaison au niveau duquel vous ne voulez pas exécuter le code de traitement par défaut.</span><span class="sxs-lookup"><span data-stu-id="7bdad-128">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="7bdad-129">Lorsque le [\<routing>](routing-of-servicebehavior.md) comportement configure le service de routage, il ne réapplique pas le comportement du point de terminaison puisqu’il en existe déjà un.</span><span class="sxs-lookup"><span data-stu-id="7bdad-129">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
