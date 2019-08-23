---
title: Service Auditing Behavior
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 6d5f254f4f94adfaeaf5632ddd696891af177e93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964545"
---
# <a name="service-auditing-behavior"></a>Service Auditing Behavior
Cet exemple montre comment utiliser <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> pour activer l'audit des événements de sécurité pendant des opérations de service. Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md). Le service et le client ont été configurés à l’aide de la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). L' `mode` attribut de la [ \<> de sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) a été défini `Message` sur `clientCredentialType` et a été défini `Windows`sur. Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fichier de configuration de service utilise l'élément `serviceSecurityAudit` pour configurer l'audit.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.  
  
 Les journaux d'audit résultants peuvent être consultés en exécutant l'Observateur d'événements. Par défaut, les événements d’audit peuvent être consultés sur Windows XP dans le journal d’application, tandis que sur Windows Server 2003 et Windows Vista, ils peuvent être consultés dans le journal de sécurité. Les événements d'audit peuvent être consultés sur Windows Server 2008 et Windows 7 dans les journaux d'application et de services. L’emplacement des événements d’audit peut être spécifié en affectant à l’attribut la `auditLogLocation` valeur «application» ou «Security». Pour plus d’informations, consultez [Guide pratique pour Auditer les](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)événements de sécurité. Si les événements sont écrits dans le journal de sécurité, LocalSecurityPolicy-> activer l’accès aux objets doit être défini pour «succès» et «échec».  
  
 Lors de la consultation du journal des événements, la source des événements d'audit est « ServiceModel Audit 3.0.0.0 ». Les enregistrements d’audit d’authentification de message ont une catégorie «MessageAuthentication» tandis que les enregistrements d’audit d’autorisation de service ont une catégorie «ServiceAuthorization».  
  
 Les événements de l'audit d'authentification du message permettent de savoir si le message a été falsifié, s'il a expiré et si le client peut s'authentifier auprès du service. Ils fournissent des informations sur la réussite ou l'échec de l'authentification, l'identité du client, le point de terminaison auquel le message a été envoyé et l'action associée au message.  
  
 Les événements de l'audit d'autorisation du service permettent de connaître la décision d'autorisation prise par un gestionnaire d'autorisation du service. Ils fournissent des informations sur la réussite ou l'échec de l'autorisation, ainsi que l'identité du client, le point de terminaison auquel le message a été envoyé, l'action associée au message, l'identificateur du contexte d'autorisation généré à partir du message entrant et le type du gestionnaire d'autorisations qui a pris la décision d'accès.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi

- [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Guide pratique pour Auditer les événements de sécurité](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
