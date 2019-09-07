---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 094fbf95042c00287fb8dfcca28753cfe501a8d8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398757"
---
# <a name="etwtracking"></a><span data-ttu-id="94430-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="94430-101">\<etwTracking></span></span>
<span data-ttu-id="94430-102">Comportement de service qui permet à un service d’utiliser le suivi ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>à l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="94430-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="94430-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94430-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94430-104">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="94430-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="94430-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="94430-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="94430-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="94430-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="94430-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="94430-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="94430-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<etwTracking >**</span><span class="sxs-lookup"><span data-stu-id="94430-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94430-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94430-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94430-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="94430-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94430-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="94430-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94430-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="94430-112">Attributes</span></span>  
  
|<span data-ttu-id="94430-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="94430-113">Attribute</span></span>|<span data-ttu-id="94430-114">Description</span><span class="sxs-lookup"><span data-stu-id="94430-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94430-115">profileName</span><span class="sxs-lookup"><span data-stu-id="94430-115">profileName</span></span>|<span data-ttu-id="94430-116">Chaîne qui spécifie le nom du modèle de suivi a associé à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="94430-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94430-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94430-117">Child Elements</span></span>  
 <span data-ttu-id="94430-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="94430-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94430-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94430-119">Parent Elements</span></span>  
  
|<span data-ttu-id="94430-120">Élément</span><span class="sxs-lookup"><span data-stu-id="94430-120">Element</span></span>|<span data-ttu-id="94430-121">Description</span><span class="sxs-lookup"><span data-stu-id="94430-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94430-122">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="94430-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="94430-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="94430-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94430-124">Notes</span><span class="sxs-lookup"><span data-stu-id="94430-124">Remarks</span></span>  
 <span data-ttu-id="94430-125">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration configure un participant au suivi sur un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="94430-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="94430-126">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="94430-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="94430-127">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="94430-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94430-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="94430-128">Example</span></span>  
 <span data-ttu-id="94430-129">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="94430-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="94430-130">L’ID de fournisseur que le participant de suivi ETW utilise pour écrire les enregistrements de suivi dans ETW est défini dans la  **\<section Diagnostics >** .</span><span class="sxs-lookup"><span data-stu-id="94430-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="94430-131">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="94430-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="94430-132">Cela est défini par l’attribut **ProfileName** de l'  **\<élément Add >** .</span><span class="sxs-lookup"><span data-stu-id="94430-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="94430-133">Une fois ces derniers définis, le participant de suivi est ajouté au comportement du  **\<service etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="94430-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="94430-134">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="94430-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94430-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94430-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="94430-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="94430-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94430-137">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="94430-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
