---
title: <participants> de WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 4ee70d3a9b5d75adc639f1e3922cfde6737e9e01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170153"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="9080d-102">\<participants> de WCF</span><span class="sxs-lookup"><span data-stu-id="9080d-102">\<participants> of WCF</span></span>

<span data-ttu-id="9080d-103">Configurez une liste de participants au suivi qui écoutent les enregistrements de suivi émis directement du runtime et les traitent en fonction de leur configuration.</span><span class="sxs-lookup"><span data-stu-id="9080d-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="9080d-104">Cela inclut l'écriture dans une sortie spécifique (par exemple, un fichier, une console ou le suivi d'événements pour Windows [ETW]), le traitement/regroupement des enregistrements ou toute autre combinaison requise.</span><span class="sxs-lookup"><span data-stu-id="9080d-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="9080d-105">Pour plus d’informations sur le suivi des workflows et les participants au suivi, consultez [suivi des workflows et](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) suivi et [suivi des participants](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="9080d-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="9080d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9080d-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9080d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9080d-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9080d-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9080d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9080d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9080d-109">Attributes</span></span>  

 <span data-ttu-id="9080d-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9080d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9080d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9080d-111">Child Elements</span></span>  
  
|<span data-ttu-id="9080d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="9080d-112">Element</span></span>|<span data-ttu-id="9080d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9080d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="9080d-114">Contient les paramètres d'un participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="9080d-114">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9080d-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9080d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9080d-116">Élément</span><span class="sxs-lookup"><span data-stu-id="9080d-116">Element</span></span>|<span data-ttu-id="9080d-117">Description</span><span class="sxs-lookup"><span data-stu-id="9080d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="9080d-118">Représente une section de configuration permettant de définir les paramètres de suivi d'un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="9080d-118">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9080d-119">Notes</span><span class="sxs-lookup"><span data-stu-id="9080d-119">Remarks</span></span>  

 <span data-ttu-id="9080d-120">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="9080d-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="9080d-121">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="9080d-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="9080d-122">Plusieurs participants au suivi peuvent consommer les événements de suivi simultanément.</span><span class="sxs-lookup"><span data-stu-id="9080d-122">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="9080d-123">Chaque participant au suivi peut être associé à un modèle de suivi différent.</span><span class="sxs-lookup"><span data-stu-id="9080d-123">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="9080d-124">Un participant au suivi standard est fourni, il écrit les enregistrements de suivi dans une session ETW.</span><span class="sxs-lookup"><span data-stu-id="9080d-124">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9080d-125">Le participant est configuré sur un service de flux de travail en ajoutant un comportement spécifique au suivi dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9080d-125">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="9080d-126">L'activation d'un participant au suivi ETW permet d'afficher les enregistrements de suivi dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="9080d-126">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="9080d-127">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9080d-127">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9080d-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="9080d-128">Example</span></span>  

 <span data-ttu-id="9080d-129">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="9080d-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="9080d-130">L'ID de fournisseur dont se sert le participant au suivi ETW pour écrire les enregistrements de suivi dans une session ETW est défini dans la section `<diagnostics>`.</span><span class="sxs-lookup"><span data-stu-id="9080d-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="9080d-131">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="9080d-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="9080d-132">Ce profil est défini par l'attribut `profileName` de l'élément `<add>`.</span><span class="sxs-lookup"><span data-stu-id="9080d-132">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="9080d-133">Une fois ces paramètres définis, le participant au suivi est ajouté au comportement de service `<etwTracking>`.</span><span class="sxs-lookup"><span data-stu-id="9080d-133">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="9080d-134">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="9080d-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9080d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9080d-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="9080d-136">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="9080d-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9080d-137">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="9080d-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
