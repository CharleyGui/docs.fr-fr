---
title: <add> de <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152357"
---
# <a name="add-of-participants"></a><span data-ttu-id="ee8a3-102">\<ajouter> des \<participants></span><span class="sxs-lookup"><span data-stu-id="ee8a3-102">\<add> of \<participants></span></span>
<span data-ttu-id="ee8a3-103">Configurez un participant au suivi qui écoute les enregistrements de suivi émis directement du runtime et les traite en fonction de sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="ee8a3-104">Cela inclut l'écriture dans une sortie spécifique (par exemple, un fichier, une console ou le suivi d'événements pour Windows [ETW]), le traitement/regroupement des enregistrements ou toute autre combinaison requise.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="ee8a3-105">Pour plus d’informations sur le suivi et le suivi des flux de travail des participants, consultez [workflow Tracking and Tracking](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="ee8a3-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="ee8a3-106">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee8a3-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ee8a3-107">&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ee8a3-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="ee8a3-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<suivi des>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ee8a3-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="ee8a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span><span class="sxs-lookup"><span data-stu-id="ee8a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="ee8a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="ee8a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee8a3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee8a3-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee8a3-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee8a3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ee8a3-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee8a3-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee8a3-114">Attributes</span></span>  
  
|<span data-ttu-id="ee8a3-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ee8a3-115">Element</span></span>|<span data-ttu-id="ee8a3-116">Description</span><span class="sxs-lookup"><span data-stu-id="ee8a3-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee8a3-117">name</span><span class="sxs-lookup"><span data-stu-id="ee8a3-117">name</span></span>|<span data-ttu-id="ee8a3-118">Chaîne qui spécifie le nom d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="ee8a3-119">profileName</span><span class="sxs-lookup"><span data-stu-id="ee8a3-119">profileName</span></span>|<span data-ttu-id="ee8a3-120">Chaîne qui spécifie le nom du modèle de suivi qui définit les enregistrements de suivi auxquels le participant au suivi s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="ee8a3-121">type</span><span class="sxs-lookup"><span data-stu-id="ee8a3-121">type</span></span>|<span data-ttu-id="ee8a3-122">Chaîne qui spécifie le type d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee8a3-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee8a3-123">Child Elements</span></span>  
 <span data-ttu-id="ee8a3-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee8a3-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee8a3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ee8a3-126">Élément</span><span class="sxs-lookup"><span data-stu-id="ee8a3-126">Element</span></span>|<span data-ttu-id="ee8a3-127">Description</span><span class="sxs-lookup"><span data-stu-id="ee8a3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee8a3-128">\<participants></span><span class="sxs-lookup"><span data-stu-id="ee8a3-128">\<participants></span></span>](participants.md)|<span data-ttu-id="ee8a3-129">Liste de participants au suivi</span><span class="sxs-lookup"><span data-stu-id="ee8a3-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee8a3-130">Notes </span><span class="sxs-lookup"><span data-stu-id="ee8a3-130">Remarks</span></span>  
 <span data-ttu-id="ee8a3-131">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="ee8a3-132">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="ee8a3-133">Plusieurs participants au suivi peuvent consommer les événements de suivi simultanément.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="ee8a3-134">Chaque participant au suivi peut être associé à un modèle de suivi différent.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="ee8a3-135">Un participant au suivi standard est fourni, il écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ee8a3-136">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ee8a3-137">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ee8a3-138">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee8a3-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ee8a3-139">Example</span></span>  
 <span data-ttu-id="ee8a3-140">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="ee8a3-141">L’id fournisseur que le participant de suivi ETW utilise pour écrire les \*\* \<dossiers\*\* de suivi à ETW est défini dans la section>diagnostics.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="ee8a3-142">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="ee8a3-143">Ceci est défini par l’attribut **profileName** de \*\* \<l’élément ajouter>.\*\*</span><span class="sxs-lookup"><span data-stu-id="ee8a3-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="ee8a3-144">Une fois ces éléments définis, \*\* \<\*\* le participant de suivi est ajouté au comportement de service etwTracking>.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="ee8a3-145">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="ee8a3-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee8a3-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee8a3-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="ee8a3-147">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="ee8a3-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ee8a3-148">Suivi des participants</span><span class="sxs-lookup"><span data-stu-id="ee8a3-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
