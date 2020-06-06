---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397729"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="58e12-102">\<routing> de \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="58e12-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="58e12-103">Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="58e12-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="58e12-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e12-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58e12-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58e12-105">Attributes and Elements</span></span>  
 <span data-ttu-id="58e12-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58e12-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58e12-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="58e12-107">Attributes</span></span>  
  
|<span data-ttu-id="58e12-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="58e12-108">Attribute</span></span>|<span data-ttu-id="58e12-109">Description</span><span class="sxs-lookup"><span data-stu-id="58e12-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58e12-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="58e12-110">filterTable</span></span>|<span data-ttu-id="58e12-111">Chaîne qui spécifie le nom de la table de routage contenant les filtres destinés à être évalués par le service de routage.</span><span class="sxs-lookup"><span data-stu-id="58e12-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="58e12-112">Cette valeur doit correspondre à l' `name` attribut d’un [\<filterTable>](filtertable.md) élément dans la [\<filterTables>](filtertables.md) section.</span><span class="sxs-lookup"><span data-stu-id="58e12-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="58e12-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="58e12-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="58e12-114">Valeur booléenne qui spécifie si le filtre doit examiner à la fois le corps du message et l'en-tête, ou l'en-tête uniquement.</span><span class="sxs-lookup"><span data-stu-id="58e12-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="58e12-115">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="58e12-115">The default is `true`.</span></span>|  
|<span data-ttu-id="58e12-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="58e12-116">soapProcessingEnabled</span></span>|<span data-ttu-id="58e12-117">Valeur booléenne qui spécifie si le traitement SOAP doit avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="58e12-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58e12-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58e12-118">Child Elements</span></span>  
 <span data-ttu-id="58e12-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="58e12-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58e12-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58e12-120">Parent Elements</span></span>  
  
|<span data-ttu-id="58e12-121">Élément</span><span class="sxs-lookup"><span data-stu-id="58e12-121">Element</span></span>|<span data-ttu-id="58e12-122">Description</span><span class="sxs-lookup"><span data-stu-id="58e12-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="58e12-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="58e12-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e12-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="58e12-124">Remarks</span></span>  
 <span data-ttu-id="58e12-125">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration active le routage pour le service.</span><span class="sxs-lookup"><span data-stu-id="58e12-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="58e12-126">Vous pouvez spécifier la table de routage réelle que le service doit utiliser dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="58e12-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="58e12-127">Cette section de configuration vous permet de modifier immédiatement vos paramètres de routage lorsque votre modèle de déploiement change.</span><span class="sxs-lookup"><span data-stu-id="58e12-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="58e12-128">Au moment de l'exécution, vous pouvez inscrire votre propre extension de routage avec de nouveaux paramètres de routage. Le service de routage commence alors à utiliser les informations de configuration mises à jour pour les nouveaux messages et sessions, en laissant les messages/sessions en cours utiliser les règles qui étaient en place lorsqu'ils ont démarré.</span><span class="sxs-lookup"><span data-stu-id="58e12-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="58e12-129">Vous avez ainsi la possibilité de reconfigurer le service de routage au moment de l'exécution, sans interruption de session ni recyclage.</span><span class="sxs-lookup"><span data-stu-id="58e12-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
