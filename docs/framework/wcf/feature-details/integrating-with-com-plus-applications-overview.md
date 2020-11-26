---
title: Vue d'ensemble de l'intégration à des applications COM+
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 1b9b7e57760c2aba0a8e9eadd53ca8e72529b787
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248966"
---
# <a name="integrating-with-com-applications-overview"></a>Vue d'ensemble de l'intégration à des applications COM+

Windows Communication Foundation (WCF) fournit un environnement riche pour la création d’applications distribuées. Si vous utilisez déjà une logique d’application basée sur des composants hébergée dans COM+, vous pouvez utiliser WCF pour étendre votre logique existante au lieu de la réécrire. Un scénario courant consiste à exposer une logique métier COM+ ou Enterprise Services existante par le biais de services Web.  
  
 Lorsqu'une interface sur un composant COM+ est exposée comme service Web, la spécification et le contrat de ces services sont déterminés par un mappage automatique exécuté au moment de l'initialisation de l'application. La liste suivante présente le modèle conceptuel de ce mappage :  
  
- Un service est défini pour chaque classe COM exposée.  
  
- Le contrat du service est directement dérivé de la définition d'interface du composant sélectionné avec la possibilité d'exclusion de méthode définie dans la configuration.  
  
- Les opérations figurant dans ce contrat sont directement dérivées des méthodes sur la définition d'interface du composant.  
  
- Les paramètres de ces opérations sont directement dérivés du type d'interopérabilité COM qui correspond aux paramètres de méthode du composant.  
  
 Les adresses et liaisons de transport par défaut du service sont fournies dans un fichier de configuration de service, mais elles peuvent être reconfigurées si nécessaire.  
  
> [!NOTE]
> Les contrats des services Web exposés restent constants tant que les interfaces et la configuration COM+ restent inchangées. La modification de plusieurs interfaces ne met pas automatiquement à jour les services disponibles et requiert de réexécuter l'outil ComSvcConfig.exe (COM+ Service Model Configuration).  
  
 Les spécifications d'authentification et d'autorisation de l'application COM+ et de ses composants continuent d'être appliquées lorsqu'elle sert de service Web.  
  
 Si l'appelant initie une transaction de service Web, les composants marqués comme transactionnels s'inscrivent dans l'étendue de cette transaction.  
  
 Les étapes suivantes sont requises pour exposer l'interface d'un composant COM+ comme service Web sans modifier le composant :  
  
1. Déterminez si l'interface du composant COM+ peut être exposée comme service Web.  
  
2. Sélectionnez un mode d'hébergement approprié.  
  
3. Utilisez l'outil ComSvcConfig.exe (COM+ Service Model Configuration) pour ajouter un service Web pour l'interface. Pour plus d’informations sur l’utilisation de ComSvcConfig.exe, consultez [Comment : utiliser l’outil de configuration de modèle de service com+](how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Configurez les paramètres de service supplémentaires dans le fichier de configuration de l'application. Pour plus d’informations sur la configuration d’un composant, consultez [procédure : configurer les paramètres du service com+](how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Interfaces prises en charge  

 Certaines restrictions s'appliquent aux types d'interfaces qui peuvent être exposés comme service Web. Les types d'interfaces suivants ne sont pas pris en charge :  
  
- Les interfaces qui passent des références d'objet comme paramètres - voir la section concernant la prise en charge limitée des références d'objet.  
  
- Les interfaces qui passent des types qui ne sont pas compatibles avec les conversions de l’interopérabilité COM .NET Framework.  
  
- Les interfaces des applications dont la fonction de regroupement d'applications est activée lorsqu'elles sont hébergées par COM+.  
  
- Les interfaces des composants marqués comme privés pour l'application.  
  
- Les interfaces d'infrastructure COM+.  
  
- Les interfaces issues de l'application système.  
  
- Les interfaces issues des composants Enterprise Services qui n'ont pas été ajoutés au cache GAC (Global Assembly Cache).  
  
### <a name="limited-object-reference-support"></a>Prise en charge limitée des références d'objet  

 Comme un certain nombre de composants COM+ déployés n'utilisent pas de paramètres de référence d'objet, pour retourner un objet ADO Recordset par exemple, l'intégration COM+ inclut une prise en charge limitée des paramètres de référence d'objet. Cette prise en charge est limitée aux objets qui implémentent l'interface COM `IPersistStream`. Elle inclut les objets ADO Recordset et peut être implémentée pour des objets COM propres à l'application.  
  
 Pour activer cette prise en charge, l’outil ComSvcConfig.exe fournit le commutateur **allowreferences** qui désactive le paramètre de signature de méthode normal et vérifie que l’outil s’exécute pour s’assurer que les paramètres de référence d’objet ne sont pas utilisés. En outre, les types d’objets que vous transmettez comme paramètres doivent être nommés et identifiés dans le <`persistableTypes`> élément de configuration qui est un enfant de l' `comContract` élément <>.  
  
 Lorsque cette fonctionnalité est activée, le service d’intégration COM+ utilise l’interface `IPersistStream` pour sérialiser ou désérialiser l’instance d’objet. Si l'instance d'objet ne prend pas en charge `IPersistStream`, une exception est levée.  
  
 Dans une application cliente, les méthodes sur l'objet <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> peuvent être utilisées pour passer un objet dans un service, et pour récupérer un objet de la même façon.  
  
> [!NOTE]
> En raison de la nature personnalisée et propre à la plateforme de l’approche de sérialisation, il est préférable de l’utiliser entre les clients WCF et les services WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Sélection du mode d'hébergement  

 COM+ expose des services Web dans l'un des modes d'hébergement suivants :  
  
- Hébergé par COM+  
  
     Le service Web est hébergé dans le processus serveur COM+ dédié de l'application (Dllhost.exe). Ce mode requiert le démarrage explicite de l'application pour qu'elle puisse recevoir des demandes de service Web. Les options COM+ « Exécuter en tant que service NT » ou « Ne pas arrêter l'exécution lors de l'inactivité » peuvent être utilisées pour empêcher l'arrêt de l'application et de ses services suite à une période d'inactivité. Ce mode fournit à la fois un service Web et un accès DCOM à l'application serveur.  
  
- Hébergé sur le Web  
  
     Le service Web est hébergé dans un processus de travail de serveur web. Ce mode ne requiert pas l'activation de COM+ lorsque la demande initiale est reçue. Si l'application n'est pas active lorsque cette demande est reçue, elle est activée automatiquement avant le traitement de la demande. Ce mode fournit également un service Web et un accès DCOM à l'application serveur, mais provoque un saut de processus pour les demandes de service Web.  En général, il requiert l'activation de l'emprunt d'identité par le client. Dans WCF, cette opération peut être effectuée à l’aide <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> de la propriété de la <xref:System.ServiceModel.Security.WindowsClientCredential> classe, qui est accessible en tant que propriété de la <xref:System.ServiceModel.ChannelFactory%601> classe générique, ainsi que de la valeur d' <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> énumération.  
  
- Hébergé sur le Web dans un processus  
  
     Le service Web et la logique d’application COM+ sont hébergés dans le processus de travail de serveur web. Cela permet l'activation automatique du mode Hébergé sur le Web sans provoquer de saut de processus pour les demandes de service Web. L'inconvénient est que l'application serveur n'est pas accessible par le biais de DCOM.  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  

 À l’instar des autres services WCF, les paramètres de sécurité du service exposé sont administrés par le biais des paramètres de configuration du canal WCF. D'ordinaire, les paramètres de sécurité DCOM, tels que les paramètres des autorisations DCOM à l'échelle de l'ordinateur, ne sont pas appliqués. Pour appliquer des rôles d'application COM+, l'autorisation « Appliquer les vérifications d'accès au niveau du composant » doit être activée pour le composant.  
  
 L’utilisation d’une liaison non sécurisée peut exposer la communication à des risques de falsification et de divulgation d’informations. Pour éviter ce problème, il est recommandé de recourir à une liaison sécurisée.  
  
 Pour les modes Hébergé par COM+ et Hébergé sur le Web, les applications clientes doivent autoriser le processus serveur à emprunter l'identité de l'utilisateur client. Cela peut être fait dans les clients WCF en affectant au niveau d’emprunt d’identité la valeur <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .  
  
 Lorsque les services IIS (Internet Information Services) ou le service d'activation de processus de Windows (WAS, Windows Process Activation Service) utilisent le transport HTTP, l'outil Httpcfg.exe peut être exécuté pour réserver une adresse de point de terminaison de transport. Dans d'autres configurations, il est important de se protéger contre les services non autorisés qui se comportent comme le service prévu. Pour empêcher un service non autorisé de démarrer au point de terminaison souhaité, le service légitime peut être configuré pour s'exécuter comme un service NT. Cette méthode permet au service légitime de revendiquer l'adresse du point de terminaison avant un service non autorisé.  
  
 Quand vous exposez une application COM+ avec des rôles COM+ configurés en tant que service hébergé sur le Web, le « lancement du compte de processus IIS » doit être ajouté à l’un des rôles de l’application. Ce compte, généralement appelé IWAM_nom_ordinateur, doit être ajouté pour activer l'arrêt normal des objets après leur utilisation. Aucune autre autorisation ne doit être accordée au compte.  
  
 Les fonctionnalités de recyclage de processus COM+ ne peuvent pas être utilisées sur des applications intégrées. Si l'application est configurée pour utiliser le recyclage de processus et que les composants s'exécutent dans un processus hébergé par COM+, le service ne démarre pas. Cette exigence ne concerne pas les services utilisant le mode Hébergé sur le Web dans un processus car les paramètres de recyclage de processus ne sont pas appliqués.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de l'intégration à des applications COM](integrating-with-com-applications-overview.md)
