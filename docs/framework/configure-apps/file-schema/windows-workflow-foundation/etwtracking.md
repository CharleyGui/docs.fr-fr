---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152169"
---
# \<etwTracking>
<span data-ttu-id="46436-101">Comportement de service qui permet à un service d'utiliser le suivi ETW à l'aide d'un objet  <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="46436-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="46436-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46436-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46436-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46436-103">Attributes and Elements</span></span>  
 <span data-ttu-id="46436-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46436-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46436-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="46436-105">Attributes</span></span>  
  
|<span data-ttu-id="46436-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="46436-106">Attribute</span></span>|<span data-ttu-id="46436-107">Description</span><span class="sxs-lookup"><span data-stu-id="46436-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46436-108">profileName</span><span class="sxs-lookup"><span data-stu-id="46436-108">profileName</span></span>|<span data-ttu-id="46436-109">Chaîne qui spécifie le nom du modèle de suivi a associé à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="46436-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46436-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46436-110">Child Elements</span></span>  
 <span data-ttu-id="46436-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46436-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46436-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46436-112">Parent Elements</span></span>  
  
|<span data-ttu-id="46436-113">Élément</span><span class="sxs-lookup"><span data-stu-id="46436-113">Element</span></span>|<span data-ttu-id="46436-114">Description</span><span class="sxs-lookup"><span data-stu-id="46436-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46436-115">\<behavior>of\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="46436-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="46436-116">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="46436-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46436-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="46436-117">Remarks</span></span>  
 <span data-ttu-id="46436-118">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration configure un participant au suivi sur un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="46436-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="46436-119">Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.</span><span class="sxs-lookup"><span data-stu-id="46436-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="46436-120">De la même manière, tout post-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.</span><span class="sxs-lookup"><span data-stu-id="46436-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46436-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="46436-121">Example</span></span>  
 <span data-ttu-id="46436-122">L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="46436-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="46436-123">L’ID de fournisseur que le participant de suivi ETW utilise pour écrire les enregistrements de suivi dans ETW est défini dans la **\<diagnostics>** section.</span><span class="sxs-lookup"><span data-stu-id="46436-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="46436-124">Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.</span><span class="sxs-lookup"><span data-stu-id="46436-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="46436-125">Cela est défini par l’attribut **ProfileName** de l' **\<add>** élément.</span><span class="sxs-lookup"><span data-stu-id="46436-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="46436-126">Une fois ces derniers définis, le participant de suivi est ajouté au **\<etwTracking>** comportement du service.</span><span class="sxs-lookup"><span data-stu-id="46436-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="46436-127">Les participants au suivi sélectionnés sont ajoutés aux extensions de l’instance de flux de travail, afin qu’ils commencent à recevoir les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="46436-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46436-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46436-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="46436-129">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="46436-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="46436-130">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="46436-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
