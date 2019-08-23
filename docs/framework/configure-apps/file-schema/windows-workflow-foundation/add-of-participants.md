---
title: <add> de <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: a6dc07b6f419fcb98e3f182269a99cb281139ba9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946198"
---
# <a name="add-of-participants"></a><span data-ttu-id="dcdb2-102">\<Ajouter > de \<participants ></span><span class="sxs-lookup"><span data-stu-id="dcdb2-102">\<add> of \<participants></span></span>
<span data-ttu-id="dcdb2-103">Configurez un participant au suivi qui écoute les enregistrements de suivi émis directement du runtime et les traite en fonction de sa configuration.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="dcdb2-104">Cela inclut l'écriture dans une sortie spécifique (par exemple, un fichier, une console ou le suivi d'événements pour Windows [ETW]), le traitement/regroupement des enregistrements ou toute autre combinaison requise.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="dcdb2-105">Pour plus d’informations sur le suivi des workflows et les participants au suivi, consultez [suivi des workflows et](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) suivi et [suivi des participants](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="dcdb2-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="dcdb2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dcdb2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="dcdb2-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="dcdb2-107">\<tracking></span></span>  
<span data-ttu-id="dcdb2-108">\<participants></span><span class="sxs-lookup"><span data-stu-id="dcdb2-108">\<participants></span></span>  
<span data-ttu-id="dcdb2-109">\<add></span><span class="sxs-lookup"><span data-stu-id="dcdb2-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdb2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdb2-110">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcdb2-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dcdb2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dcdb2-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcdb2-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="dcdb2-113">Attributes</span></span>  
  
|<span data-ttu-id="dcdb2-114">Élément</span><span class="sxs-lookup"><span data-stu-id="dcdb2-114">Element</span></span>|<span data-ttu-id="dcdb2-115">Description</span><span class="sxs-lookup"><span data-stu-id="dcdb2-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcdb2-116">name</span><span class="sxs-lookup"><span data-stu-id="dcdb2-116">name</span></span>|<span data-ttu-id="dcdb2-117">Chaîne qui spécifie le nom d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="dcdb2-118">profileName</span><span class="sxs-lookup"><span data-stu-id="dcdb2-118">profileName</span></span>|<span data-ttu-id="dcdb2-119">Chaîne qui spécifie le nom du modèle de suivi qui définit les enregistrements de suivi auxquels le participant au suivi s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="dcdb2-120">type</span><span class="sxs-lookup"><span data-stu-id="dcdb2-120">type</span></span>|<span data-ttu-id="dcdb2-121">Chaîne qui spécifie le type d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcdb2-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dcdb2-122">Child Elements</span></span>  
 <span data-ttu-id="dcdb2-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcdb2-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dcdb2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dcdb2-125">Élément</span><span class="sxs-lookup"><span data-stu-id="dcdb2-125">Element</span></span>|<span data-ttu-id="dcdb2-126">Description</span><span class="sxs-lookup"><span data-stu-id="dcdb2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcdb2-127">\<participants></span><span class="sxs-lookup"><span data-stu-id="dcdb2-127">\<participants></span></span>](participants.md)|<span data-ttu-id="dcdb2-128">Liste de participants au suivi</span><span class="sxs-lookup"><span data-stu-id="dcdb2-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcdb2-129">Notes</span><span class="sxs-lookup"><span data-stu-id="dcdb2-129">Remarks</span></span>  
 <span data-ttu-id="dcdb2-130">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="dcdb2-131">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="dcdb2-132">Plusieurs participants au suivi peuvent consommer les événements de suivi simultanément.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="dcdb2-133">Chaque participant au suivi peut être associé à un modèle de suivi différent.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="dcdb2-134">Un participant au suivi standard est fourni, il écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="dcdb2-135">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="dcdb2-136">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="dcdb2-137">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcdb2-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcdb2-138">Example</span></span>  
 <span data-ttu-id="dcdb2-139">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="dcdb2-140">L’ID de fournisseur que le participant de suivi ETW utilise pour écrire les enregistrements de suivi dans ETW est  **\<** défini dans la section Diagnostics >.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="dcdb2-141">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="dcdb2-142">Cela est défini par l' attribut ProfileName de l'  **\<élément Add >** .</span><span class="sxs-lookup"><span data-stu-id="dcdb2-142">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="dcdb2-143">Une fois ces derniers définis, le participant de suivi est ajouté au comportement du  **\<service etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="dcdb2-143">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="dcdb2-144">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="dcdb2-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcdb2-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcdb2-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="dcdb2-146">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="dcdb2-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dcdb2-147">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="dcdb2-147">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
