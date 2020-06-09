---
title: 'Comment : auditer les événements de sécurité relatifs à Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 186dd4a7fc2beae848e5cbd167a204352ee6ed4e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601294"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="571c3-102">Comment : auditer les événements de sécurité relatifs à Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="571c3-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="571c3-103">Windows Communication Foundation (WCF) vous permet d’enregistrer des événements de sécurité dans le journal des événements Windows, que vous pouvez afficher à l’aide du observateur d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="571c3-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="571c3-104">Cette rubrique explique comment installer une application afin qu'elle enregistre des événements de sécurité.</span><span class="sxs-lookup"><span data-stu-id="571c3-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="571c3-105">Pour plus d’informations sur l’audit WCF, consultez [audit](auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="571c3-105">For more information about WCF auditing, see [Auditing](auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="571c3-106">Pour auditer des événements de sécurité dans le code</span><span class="sxs-lookup"><span data-stu-id="571c3-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="571c3-107">Spécifiez l'emplacement du journal d'audit.</span><span class="sxs-lookup"><span data-stu-id="571c3-107">Specify the audit log location.</span></span> <span data-ttu-id="571c3-108">Pour cela, affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> de la classe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> l'une des valeurs d'énumération <xref:System.ServiceModel.AuditLogLocation>, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="571c3-109">L' <xref:System.ServiceModel.AuditLogLocation> énumération a trois valeurs : `Application` , `Security` ou `Default` .</span><span class="sxs-lookup"><span data-stu-id="571c3-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="571c3-110">La valeur spécifie l'un des journaux visibles dans l'Observateur d'événements, le journal de sécurité ou le journal des applications.</span><span class="sxs-lookup"><span data-stu-id="571c3-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="571c3-111">Si vous utilisez la valeur `Default`, le journal réel dépend du système d'exploitation sur lequel l'application s'exécute.</span><span class="sxs-lookup"><span data-stu-id="571c3-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="571c3-112">Si l'audit est activé et que l'emplacement du journal n'est pas spécifié, la valeur par défaut est le journal `Security` pour les plateformes qui prennent en charge l'écriture dans le journal de sécurité ; sinon, les événements sont consignés dans le journal `Application`.</span><span class="sxs-lookup"><span data-stu-id="571c3-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="571c3-113">Seul Windows Server 2003 et Windows Vista prennent en charge l’écriture dans le journal de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="571c3-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="571c3-114">Installez les types d'événements à auditer.</span><span class="sxs-lookup"><span data-stu-id="571c3-114">Set up the types of events to audit.</span></span> <span data-ttu-id="571c3-115">Vous pouvez auditer simultanément des événements au niveau du service ou des événements d'autorisation au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="571c3-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="571c3-116">Pour cela, affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> ou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> l'une des valeurs d'énumération <xref:System.ServiceModel.AuditLevel>, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="571c3-117">Spécifiez s'il convient de supprimer ou d'exposer les défaillances de l'application concernant des événements d'audit de journal.</span><span class="sxs-lookup"><span data-stu-id="571c3-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="571c3-118">Affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> la valeur `true` ou `false`, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="571c3-119">La propriété `SuppressAuditFailure` par défaut a la valeur `true`, afin que l'échec de l'audit n'affecte pas l'application.</span><span class="sxs-lookup"><span data-stu-id="571c3-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="571c3-120">Sinon, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="571c3-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="571c3-121">Tout audit exécuté avec succès entraîne l'écriture d'un suivi de détails d'information.</span><span class="sxs-lookup"><span data-stu-id="571c3-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="571c3-122">Tout échec d'audit entraîne l'écriture d'un suivi au niveau d'erreur.</span><span class="sxs-lookup"><span data-stu-id="571c3-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="571c3-123">Supprimez le <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existant de la collection de comportements située dans la description d’un <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="571c3-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="571c3-124">La collection de comportements est accessible par le biais de la propriété <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, qui elle-même est accessible à partir de la propriété <xref:System.ServiceModel.ServiceHostBase.Description%2A>.</span><span class="sxs-lookup"><span data-stu-id="571c3-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="571c3-125">Puis, ajoutez le nouveau <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à la même collection, tel qu’indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="571c3-126">Pour installer l'audit dans la configuration</span><span class="sxs-lookup"><span data-stu-id="571c3-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="571c3-127">Pour configurer l’audit dans la configuration, ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément à la [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section du fichier Web. config.</span><span class="sxs-lookup"><span data-stu-id="571c3-127">To set up auditing in configuration, add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="571c3-128">Ajoutez ensuite un [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) élément et définissez les différents attributs, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-128">Then add a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"
                serviceAuthorizationAuditLevel="None"
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="571c3-129">Vous devez spécifier le comportement du service, tel qu'indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="571c3-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="571c3-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="571c3-130">Example</span></span>  
 <span data-ttu-id="571c3-131">Le code suivant crée une instance de la classe <xref:System.ServiceModel.ServiceHost> et ajoute un nouveau <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sa collection de comportements.</span><span class="sxs-lookup"><span data-stu-id="571c3-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="571c3-132">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="571c3-132">.NET Framework Security</span></span>  
 <span data-ttu-id="571c3-133">Affecter à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> la valeur `true` supprime toute impossibilité de générer des audits de sécurité (si la propriété a la valeur `false`, une exception est levée).</span><span class="sxs-lookup"><span data-stu-id="571c3-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="571c3-134">Toutefois, si vous activez la propriété de **paramètre de sécurité locale** Windows suivante, l’échec de la génération des événements d’audit entraînera l’arrêt immédiat de Windows :</span><span class="sxs-lookup"><span data-stu-id="571c3-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="571c3-135">**Audit : arrêter immédiatement le système s’il n’est pas possible de se connecter aux audits de sécurité**</span><span class="sxs-lookup"><span data-stu-id="571c3-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="571c3-136">Pour définir la propriété, ouvrez la boîte de dialogue **paramètres de sécurité locaux** .</span><span class="sxs-lookup"><span data-stu-id="571c3-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="571c3-137">Sous **paramètres de sécurité**, cliquez sur **stratégies locales**.</span><span class="sxs-lookup"><span data-stu-id="571c3-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="571c3-138">Cliquez ensuite sur **options de sécurité**.</span><span class="sxs-lookup"><span data-stu-id="571c3-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="571c3-139">Si la <xref:System.ServiceModel.AuditLogLocation> propriété a la valeur <xref:System.ServiceModel.AuditLogLocation.Security> et si **audit Object Access** n’est pas défini dans la **stratégie de sécurité locale**, les événements d’audit ne seront pas écrits dans le journal de sécurité.</span><span class="sxs-lookup"><span data-stu-id="571c3-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="571c3-140">Notez qu'aucun échec n'est retourné, mais que les entrées d'audit ne sont pas écrites dans le journal de sécurité.</span><span class="sxs-lookup"><span data-stu-id="571c3-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571c3-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="571c3-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="571c3-142">Audit</span><span class="sxs-lookup"><span data-stu-id="571c3-142">Auditing</span></span>](auditing-security-events.md)
