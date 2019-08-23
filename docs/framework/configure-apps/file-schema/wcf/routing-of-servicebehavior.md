---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934195"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="af37d-102">\<> de routage \<des > ServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="af37d-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="af37d-103">Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="af37d-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="af37d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="af37d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="af37d-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="af37d-105">\<behaviors></span></span>  
<span data-ttu-id="af37d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="af37d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="af37d-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="af37d-107">\<behavior></span></span>  
<span data-ttu-id="af37d-108">\<routing></span><span class="sxs-lookup"><span data-stu-id="af37d-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af37d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af37d-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af37d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af37d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af37d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af37d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af37d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="af37d-112">Attributes</span></span>  
  
|<span data-ttu-id="af37d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="af37d-113">Attribute</span></span>|<span data-ttu-id="af37d-114">Description</span><span class="sxs-lookup"><span data-stu-id="af37d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af37d-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="af37d-115">filterTable</span></span>|<span data-ttu-id="af37d-116">Chaîne qui spécifie le nom de la table de routage contenant les filtres destinés à être évalués par le service de routage.</span><span class="sxs-lookup"><span data-stu-id="af37d-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="af37d-117">Cette valeur doit correspondre à `name` l’attribut d’un [ \<élément filterTable >](filtertable.md) dans la [ \<section > filterTables](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="af37d-117">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="af37d-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="af37d-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="af37d-119">Valeur booléenne qui spécifie si le filtre doit examiner à la fois le corps du message et l'en-tête, ou l'en-tête uniquement.</span><span class="sxs-lookup"><span data-stu-id="af37d-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="af37d-120">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="af37d-120">The default is `true`.</span></span>|  
|<span data-ttu-id="af37d-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="af37d-121">soapProcessingEnabled</span></span>|<span data-ttu-id="af37d-122">Valeur booléenne qui spécifie si le traitement SOAP doit avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="af37d-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af37d-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af37d-123">Child Elements</span></span>  
 <span data-ttu-id="af37d-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="af37d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af37d-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af37d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="af37d-126">Élément</span><span class="sxs-lookup"><span data-stu-id="af37d-126">Element</span></span>|<span data-ttu-id="af37d-127">Description</span><span class="sxs-lookup"><span data-stu-id="af37d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af37d-128">\<behavior></span><span class="sxs-lookup"><span data-stu-id="af37d-128">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="af37d-129">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="af37d-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af37d-130">Notes</span><span class="sxs-lookup"><span data-stu-id="af37d-130">Remarks</span></span>  
 <span data-ttu-id="af37d-131">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration active le routage pour le service.</span><span class="sxs-lookup"><span data-stu-id="af37d-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="af37d-132">Vous pouvez spécifier la table de routage réelle que le service doit utiliser dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="af37d-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="af37d-133">Cette section de configuration vous permet de modifier immédiatement vos paramètres de routage lorsque votre modèle de déploiement change.</span><span class="sxs-lookup"><span data-stu-id="af37d-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="af37d-134">Au moment de l'exécution, vous pouvez inscrire votre propre extension de routage avec de nouveaux paramètres de routage. Le service de routage commence alors à utiliser les informations de configuration mises à jour pour les nouveaux messages et sessions, en laissant les messages/sessions en cours utiliser les règles qui étaient en place lorsqu'ils ont démarré.</span><span class="sxs-lookup"><span data-stu-id="af37d-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="af37d-135">Vous avez ainsi la possibilité de reconfigurer le service de routage au moment de l'exécution, sans interruption de session ni recyclage.</span><span class="sxs-lookup"><span data-stu-id="af37d-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
