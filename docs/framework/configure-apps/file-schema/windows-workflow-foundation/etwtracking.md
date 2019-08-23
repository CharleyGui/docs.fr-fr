---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 653693fef92072cb1e6e23234359b765f0f18fc9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940227"
---
# <a name="etwtracking"></a><span data-ttu-id="5fa4a-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="5fa4a-101">\<etwTracking></span></span>
<span data-ttu-id="5fa4a-102">Comportement de service qui permet à un service d’utiliser le suivi ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>à l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="5fa4a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5fa4a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5fa4a-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5fa4a-104">\<behaviors></span></span>  
<span data-ttu-id="5fa4a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5fa4a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5fa4a-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="5fa4a-106">\<behavior></span></span>  
<span data-ttu-id="5fa4a-107">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="5fa4a-107">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa4a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fa4a-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fa4a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5fa4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5fa4a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fa4a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5fa4a-111">Attributes</span></span>  
  
|<span data-ttu-id="5fa4a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="5fa4a-112">Attribute</span></span>|<span data-ttu-id="5fa4a-113">Description</span><span class="sxs-lookup"><span data-stu-id="5fa4a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fa4a-114">profileName</span><span class="sxs-lookup"><span data-stu-id="5fa4a-114">profileName</span></span>|<span data-ttu-id="5fa4a-115">Chaîne qui spécifie le nom du modèle de suivi a associé à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-115">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fa4a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fa4a-116">Child Elements</span></span>  
 <span data-ttu-id="5fa4a-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fa4a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fa4a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5fa4a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="5fa4a-119">Element</span></span>|<span data-ttu-id="5fa4a-120">Description</span><span class="sxs-lookup"><span data-stu-id="5fa4a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fa4a-121">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="5fa4a-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5fa4a-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fa4a-123">Notes</span><span class="sxs-lookup"><span data-stu-id="5fa4a-123">Remarks</span></span>  
 <span data-ttu-id="5fa4a-124">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration configure un participant au suivi sur un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-124">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="5fa4a-125">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="5fa4a-126">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa4a-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="5fa4a-127">Example</span></span>  
 <span data-ttu-id="5fa4a-128">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-128">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="5fa4a-129">L’ID de fournisseur que le participant de suivi ETW utilise pour écrire les enregistrements de suivi dans ETW est  **\<** défini dans la section Diagnostics >.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-129">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="5fa4a-130">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-130">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="5fa4a-131">Cela est défini par l' attribut ProfileName de l'  **\<élément Add >** .</span><span class="sxs-lookup"><span data-stu-id="5fa4a-131">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="5fa4a-132">Une fois ces derniers définis, le participant de suivi est ajouté au comportement du  **\<service etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="5fa4a-132">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="5fa4a-133">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="5fa4a-133">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5fa4a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fa4a-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="5fa4a-135">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="5fa4a-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5fa4a-136">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="5fa4a-136">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
