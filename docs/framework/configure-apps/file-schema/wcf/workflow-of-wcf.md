---
title: <workflow>de WCF
ms.date: 03/30/2017
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
ms.openlocfilehash: c6c9e14a4ad3d9713ae2d35d6ade20690e0c3575
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69932791"
---
# <a name="workflow-of-wcf"></a><span data-ttu-id="b0aff-102">\<workflow>de WCF</span><span class="sxs-lookup"><span data-stu-id="b0aff-102">\<workflow> of WCF</span></span>
<span data-ttu-id="b0aff-103">Configurez un participant au suivi qui écoute les enregistrements de suivi émis directement du runtime et les traite en fonction de sa configuration.</span><span class="sxs-lookup"><span data-stu-id="b0aff-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="b0aff-104">Cela inclut l'écriture dans une sortie spécifique (par exemple, un fichier, une console ou le suivi d'événements pour Windows [ETW]), le traitement/regroupement des enregistrements ou toute autre combinaison requise.</span><span class="sxs-lookup"><span data-stu-id="b0aff-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="b0aff-105">Pour plus d’informations sur le suivi des workflows et les participants au suivi, consultez [suivi des workflows et](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) suivi et [suivi des participants](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="b0aff-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 \<system.serviceModel>  
\<tracking>  
\<participants>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="b0aff-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0aff-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0aff-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b0aff-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b0aff-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b0aff-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0aff-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b0aff-109">Attributes</span></span>  
  
|<span data-ttu-id="b0aff-110">Élément</span><span class="sxs-lookup"><span data-stu-id="b0aff-110">Element</span></span>|<span data-ttu-id="b0aff-111">Description</span><span class="sxs-lookup"><span data-stu-id="b0aff-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0aff-112">name</span><span class="sxs-lookup"><span data-stu-id="b0aff-112">name</span></span>|<span data-ttu-id="b0aff-113">Chaîne qui spécifie le nom d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="b0aff-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="b0aff-114">profileName</span><span class="sxs-lookup"><span data-stu-id="b0aff-114">profileName</span></span>|<span data-ttu-id="b0aff-115">Chaîne qui spécifie le nom du modèle de suivi qui définit les enregistrements de suivi auxquels le participant au suivi s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="b0aff-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="b0aff-116">type</span><span class="sxs-lookup"><span data-stu-id="b0aff-116">type</span></span>|<span data-ttu-id="b0aff-117">Chaîne qui spécifie le type d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="b0aff-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0aff-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b0aff-118">Child Elements</span></span>  
 <span data-ttu-id="b0aff-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b0aff-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0aff-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b0aff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b0aff-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b0aff-121">Element</span></span>|<span data-ttu-id="b0aff-122">Description</span><span class="sxs-lookup"><span data-stu-id="b0aff-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="b0aff-123">Liste de participants au suivi</span><span class="sxs-lookup"><span data-stu-id="b0aff-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0aff-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="b0aff-124">Remarks</span></span>  
 <span data-ttu-id="b0aff-125">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="b0aff-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="b0aff-126">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="b0aff-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="b0aff-127">Plusieurs participants au suivi peuvent consommer les événements de suivi simultanément.</span><span class="sxs-lookup"><span data-stu-id="b0aff-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="b0aff-128">Chaque participant au suivi peut être associé à un modèle de suivi différent.</span><span class="sxs-lookup"><span data-stu-id="b0aff-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="b0aff-129">Un participant au suivi standard est fourni, il écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="b0aff-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b0aff-130">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b0aff-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b0aff-131">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="b0aff-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b0aff-132">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b0aff-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0aff-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0aff-133">Example</span></span>  
 <span data-ttu-id="b0aff-134">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="b0aff-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="b0aff-135">L'ID de fournisseur dont se sert le participant au suivi ETW pour écrire les enregistrements de suivi dans une session ETW est défini dans la section `<diagnostics>`.</span><span class="sxs-lookup"><span data-stu-id="b0aff-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="b0aff-136">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="b0aff-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="b0aff-137">Ce profil est défini par l'attribut `profileName` de l'élément `<add>`.</span><span class="sxs-lookup"><span data-stu-id="b0aff-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="b0aff-138">Une fois ces paramètres définis, le participant au suivi est ajouté au comportement de service `<etwTracking>`.</span><span class="sxs-lookup"><span data-stu-id="b0aff-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="b0aff-139">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="b0aff-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b0aff-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0aff-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="b0aff-141">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="b0aff-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b0aff-142">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="b0aff-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
