---
title: Audit des événements de sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 985004313c7d9843f2e9960805a6c0623d43a41f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234815"
---
# <a name="auditing-security-events"></a>Audit des événements de sécurité

Les applications créées avec Windows Communication Foundation (WCF) peuvent consigner les événements de sécurité (réussite, échec, ou les deux) avec la fonctionnalité d’audit. Les événements sont écrits dans le journal des événements système Windows et peuvent être examinés à l'aide de l'Observateur d'événements.  
  
 L'audit permet à un administrateur de détecter une attaque que s'est déjà produite ou qui est en cours. En outre, l'audit permet de déboguer des problèmes relatifs à la sécurité. Par exemple, si une erreur dans la configuration de la stratégie d'autorisation ou de vérification refuse accidentellement l'accès à un utilisateur autorisé, un développeur peut la détecter rapidement et en isoler la cause en examinant le journal des événements.  
  
 Pour plus d’informations sur la sécurité WCF, consultez [vue d’ensemble](security-overview.md)de la sécurité. Pour plus d’informations sur la programmation de WCF, consultez [programmation WCF de base](../basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Niveau et comportement d'audit  

 Il existe deux niveaux d'audit de sécurité :  
  
- Niveau d'autorisation de service, dans lequel un appelant est autorisé.  
  
- Niveau du message, dans lequel WCF vérifie la validité du message et authentifie l’appelant.  
  
 Vous pouvez vérifier les deux niveaux d’audit pour la réussite ou l’échec, ce qui est connu sous le nom de *comportement d’audit*.  
  
## <a name="audit-log-location"></a>Emplacement du journal d'audit  

 Après avoir déterminé un niveau et un comportement d'audit, vous (ou un administrateur) pouvez spécifier l'emplacement du journal d'audit. Vous disposez pour cela de trois options : Default, Application et Security. Lorsque vous spécifiez Default, le journal réel dépend du système que vous utilisez et du fait que celui-ci prend ou non en charge l'écriture dans le journal Security. Pour plus d’informations, consultez la section « système d’exploitation » plus loin dans cette rubrique.  
  
 L'écriture dans le journal Security requiert le privilège `SeAuditPrivilege`. Par défaut, seuls les comptes Système local et Service réseau possèdent ce privilège. La gestion des fonctions du journal Security `read` et `delete` requièrent le privilège `SeSecurityPrivilege`. Par défaut, seuls les administrateurs possèdent ce privilège.  
  
 En revanche, les utilisateurs authentifiés peuvent lire et écrire dans le journal des applications. Windows XP écrit les événements d’audit dans le journal des applications par défaut. Le journal peut également contenir des informations personnelles accessibles à tous les utilisateurs authentifiés.  
  
## <a name="suppressing-audit-failures"></a>Suppression des échecs d'audit  

 Une autre option pendant l'audit permet de déterminer s'il faut supprimer les échecs d'audit. Par défaut, un échec d'audit n'affecte pas une application. Toutefois, si cela s'avère nécessaire, vous pouvez affecter `false` à l'option, ce qui provoque la levée d'une exception.  
  
## <a name="programming-auditing"></a>Programmation de l'audit  

 Vous pouvez spécifier le comportement d'audit par programme ou via la configuration.  
  
### <a name="auditing-classes"></a>Classes d'audit  

 Le tableau suivant décrit les classes et propriétés utilisées pour programmer le comportement d'audit.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Permet de définir les options d'audit en tant que comportement de service.|  
|<xref:System.ServiceModel.AuditLogLocation>|Énumération permettant de spécifier le journal dans lequel écrire. Les valeurs possibles sont Default, Application et Security. Lorsque vous sélectionnez Default, le système d'exploitation détermine l'emplacement du journal réel. Consultez la section « Sélection du journal des événements Application ou Security » développée ultérieurement dans cette rubrique.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Spécifie les types d'événements d'authentification de message audités au niveau du message. Les options disponibles sont `None`, `Failure`, `Success` et `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Spécifie les types d'événements d'autorisation de service audités au niveau du service. Les options disponibles sont `None`, `Failure`, `Success` et `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Spécifie ce que devient demande du client en cas d'échec de l'audit. Par exemple, lorsque le service tente d'écrire dans le journal Security, mais n'a pas `SeAuditPrivilege`. La valeur par défaut `true` indique que les échecs sont ignorés et que la demande du client est traitée normalement.|  
  
 Pour obtenir un exemple de configuration d’une application pour enregistrer des événements d’audit, consultez [Comment : auditer des événements de sécurité](how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Configuration  

 Vous pouvez également utiliser la configuration pour spécifier le comportement de l’audit en ajoutant un [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) sous le [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) . Vous devez ajouter l’élément sous un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) comme indiqué dans le code suivant.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Si l'audit est activé et que `auditLogLocation` n'est pas spécifié, le nom de journal par défaut est "Security" pour la plateforme qui prend en charge l'écriture dans le journal Security, sinon il s'agit de "Application". Seuls les systèmes d’exploitation Windows Server 2003 et Windows Vista prennent en charge l’écriture dans le journal de sécurité. Pour plus d’informations, consultez la section « système d’exploitation » plus loin dans cette rubrique.  
  
## <a name="security-considerations"></a>Considérations relatives à la sécurité  

 Si un utilisateur malveillant sait que l'audit est activé, cet intrus peut envoyer des messages non valides pour provoquer l'écriture d'entrées d'audit. Si le journal d'audit se remplit de cette manière, le système d'audit échoue. Pour minimiser ce problème, affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> la valeur `true` et utilisez les propriétés de l'Observateur d'événements pour contrôler le comportement d'audit.  
  
 Les événements d’audit qui sont écrits dans le journal des applications sur Windows XP sont visibles par tous les utilisateurs authentifiés.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Sélection du journal des événements Application ou Security  

 Les tableaux suivants fournissent des informations vous permettant d'identifier si vous devez procéder à l'enregistrement dans le journal des événements Application ou dans le journal des événements Security.  
  
#### <a name="operating-system"></a>Système d’exploitation  
  
|Système|Journal des application|Journal de sécurité|  
|------------|---------------------|------------------|  
|Windows XP SP2 ou version ultérieure|Prise en charge|Non pris en charge|  
|Windows Server 2003 SP1 et Windows Vista|Prise en charge|Le contexte de thread doit posséder `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Autres facteurs  

 Outre le système d'exploitation, le tableau suivant décrit les autres paramètres qui contrôlent l'activation de l'enregistrement.  
  
|Factor|Journal des application|Journal de sécurité|  
|------------|---------------------|------------------|  
|Gestion de la stratégie d'audit|Non applicable.|Outre la configuration, le journal Security est également contrôlé par la stratégie de l'autorité de sécurité locale (LSA). La catégorie "Audit object access" doit également être activée.|  
|Expérience utilisateur par défaut|Tous les utilisateurs authentifiés pouvant écrire dans le journal Application, aucune étape d'autorisation supplémentaire n'est donc nécessaire pour les processus d'application.|Le processus d'application (contexte) doit avoir `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Présentation de la sécurité](security-overview.md)
- [Programmation WCF de base](../basic-wcf-programming.md)
- [Procédure : auditer des événements de sécurité](how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
