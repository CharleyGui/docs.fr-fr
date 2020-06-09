---
title: Meilleures pratiques pour l'hébergement dans Internet Information Services
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: e62fed4f6a711ecc317b8f758d4948a477d136e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595269"
---
# <a name="internet-information-services-hosting-best-practices"></a>Meilleures pratiques pour l'hébergement dans Internet Information Services
Cette rubrique décrit quelques-unes des meilleures pratiques pour l’hébergement de services Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implémentation des services WCF comme DLL  
 L’implémentation d’un service WCF en tant que DLL déployée dans le répertoire \bin d’une application Web vous permet de réutiliser le service en dehors du modèle d’application Web, par exemple dans un environnement de test qui n’a peut-être pas déployé de Internet Information Services (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hôtes de service dans les applications hébergées par IIS  
 N’utilisez pas les API d’auto-hébergement impératifs pour créer de nouveaux hôtes de service qui écoutent les transports réseau qui ne sont pas pris en charge en mode natif par l’environnement d’hébergement IIS (par exemple, IIS 6,0 pour héberger des services TCP, car la communication TCP n’est pas prise en charge en mode natif sur IIS 6,0). Cette approche n’est pas recommandée. Les hôtes de service créés de manière impérative ne sont pas connus dans l'environnement d'hébergement IIS. Le point critique est que le traitement effectué par les services créés de manière impérative n'est pas pris en charge par les services IIS lorsqu'il détermine si le pool d'applications d'hébergement est inactif. Le résultat est que les applications qui possèdent ce type d'hôtes de service ont un environnement d'hébergement IIS qui élimine systématiquement les processus d'hôte IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI et points de terminaison hébergés par IIS  
 Les points de terminaison pour un service hébergé par IIS doivent être configurés à l'aide d'URI relatifs, pas d'adresses absolues. De cette manière, vous êtes certain que l'adresse du point de terminaison se situe dans le jeu des adresses URI qui appartiennent à l'application d'hébergement et que l'activation basée sur message se produit comme prévu.  
  
## <a name="state-management-and-process-recycling"></a>Gestion des états et recyclage de processus  
 L'environnement d'hébergement IIS est optimisé pour les services qui ne maintiennent pas l'état local en mémoire. Les services IIS recyclent le processus hôte en réponse à divers événements externes et internes, ce qui peut entraîner la perte de tout état volatil stocké exclusivement dans la mémoire. Les services hébergés dans IIS doivent stocker leur état en dehors du processus (par exemple, dans une base de données) ou dans un cache en mémoire qui peut être recréé facilement si un événement de recyclage d'application se produit.  
  
> [!NOTE]
> Les protocoles que WCF utilise pour la fiabilité et la sécurité de la couche de message utilisent l’État en mémoire volatile. Les sessions fiables et les sessions de sécurité WCF peuvent se terminer de manière inattendue en raison de recyclages d’applications. Les applications hébergées par IIS qui utilisent ces protocoles doivent dépendre d’un autre type que la clé de session fournie par WCF pour la corrélation de l’état de la couche application (par exemple, une construction de couche application ou un en-tête de corrélation personnalisé) ou désactiver le recyclage de processus IIS pour l’application hébergée.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimisation des performances dans les scénarios de couche intermédiaire  
 Pour des performances optimales dans un *scénario de niveau intermédiaire*(un service qui appelle d’autres services en réponse aux messages entrants), instanciez le client de service WCF au service distant une seule fois et réutilisez-le sur plusieurs demandes entrantes. L’instanciation des clients de service WCF est une opération coûteuse par rapport à l’exécution d’un appel de service sur une instance cliente préexistante, et les scénarios de couche intermédiaire produisent des gains de performances distincts en mettant en cache les clients distants entre les requêtes. Les clients de service WCF étant thread-safe, il n’est pas nécessaire de synchroniser l’accès à un client sur plusieurs threads.  
  
 Les scénarios de couche intermédiaire produisent également des gains de performance en utilisant les API asynchrones générées par l'option `svcutil /a`. Avec l' `/a` option, l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) génère `BeginXXX/EndXXX` des méthodes pour chaque opération de service, ce qui permet d’effectuer des appels potentiellement longs à des services distants sur des threads d’arrière-plan.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF dans des scénarios multi-résidents ou multi-nommés  
 Vous pouvez déployer des services WCF dans une batterie de serveurs Web IIS, où un ensemble d’ordinateurs partagent un nom externe commun (tel que `http://www.contoso.com` ), mais qui sont adressés individuellement par différents noms d’hôte (par exemple, `http://www.contoso.com` peut diriger le trafic vers deux ordinateurs différents nommés `http://machine1.internal.contoso.com` et `http://machine2.internal.contoso.com` ). Ce scénario de déploiement est entièrement pris en charge par WCF, mais requiert une configuration spéciale du site Web IIS hébergeant les services WCF pour afficher le nom d’hôte correct (externe) dans les métadonnées du service (Web Services Description Language).  
  
 Pour vous assurer que le nom d’hôte correct apparaît dans les métadonnées du service générées par WCF, configurez l’identité par défaut pour le site Web IIS qui héberge les services WCF afin d’utiliser un nom d’hôte explicite. Par exemple, les ordinateurs qui résident à l’intérieur de la `www.contoso.com` batterie de serveurs doivent utiliser une liaison de site IIS de * : 80 : www. contoso. com pour http et \* : 443 : www. contoso. com pour HTTPS.  
  
 Vous pouvez configurer des liaisons de site web IIS en utilisant le composant logiciel enfichable IIS Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Les pools d'applications qui s'exécutent dans des contextes d'utilisateur différents remplacent des assemblys d'autres comptes dans le dossier temporaire  
 Pour vous assurer que les pools d’applications qui s’exécutent dans des contextes d’utilisateur différents ne peuvent pas remplacer les assemblys d’autres comptes dans le dossier Temporary ASP.NET Files, utilisez des identités et des dossiers temporaires différents pour différentes applications. Par exemple, si vous avez deux applications virtuelles /Application1 et / Application2, vous pouvez créer deux pools d'applications, A et B, avec deux identités différentes. Le pool d'applications A peut s'exécuter sous une identité d'utilisateur (user1), et le pool d'applications B peut s'exécuter sous une autre identité d'utilisateur (user2), et configurer /Application1 pour utiliser A et /Application2 pour utiliser B.  
  
 Dans le fichier Web. config, vous pouvez configurer le dossier temporaire à l’aide de \<system.web/compilation/@tempFolder> . Pour/Application1, il peut s’agir de « c:\tempForUser1 » et pour application2 il peut être « c:\tempForUser2 ». Accordez l’autorisation en écriture correspondante à ces dossiers pour les deux identités.  
  
 Dès lors, user2 ne peut pas modifier le dossier de génération du code pour /application2 (sous c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Activation du traitement asynchrone  
 Par défaut, les messages envoyés à un service WCF hébergé sous IIS 6,0 et versions antérieures sont traités de manière synchrone. ASP.NET appelle WCF sur son propre thread (le thread de travail ASP.NET) et WCF utilise un autre thread pour traiter la demande. WCF met en attente le thread de travail ASP.NET jusqu'à la fin du traitement. Cela conduit au traitement synchrone des demandes. Le traitement des demandes de manière asynchrone permet une plus grande évolutivité, car il réduit le nombre de threads requis pour traiter une demande : WCF ne tient pas sur le thread ASP.NET lors du traitement de la demande. L’utilisation d’un comportement asynchrone n’est pas recommandée pour les ordinateurs exécutant IIS 6,0, car il n’existe aucun moyen de limiter les demandes entrantes qui ouvrent le serveur à des attaques par *déni de service* (dos). Depuis IIS 7.0, une limitation des demandes simultanées a été mise en place : `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Grâce à cette nouvelle limitation, l'utilisation du traitement asynchrone peut s'effectuer en toute sécurité.  Par défaut dans IIS 7.0, le gestionnaire asynchrone et le module sont inscrits. Si cette option a été désactivée, vous pouvez activer manuellement le traitement asynchrone des demandes dans le fichier Web.config de votre application. Les paramètres que vous utilisez dépendent de votre paramètre `aspNetCompatibilityEnabled`. Si `aspNetCompatibilityEnabled` a la valeur `false`, configurez `System.ServiceModel.Activation.ServiceHttpModule` comme illustré dans l'extrait de configuration suivant.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"
           preCondition="integratedMode,runtimeVersionv2.0"
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 Si `aspNetCompatibilityEnabled` a la valeur `true`, configurez `System.ServiceModel.Activation.ServiceHttpHandlerFactory` comme illustré dans l'extrait de configuration suivant.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"
               path="*.svc"
               verb="*"
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
               />  
    </handlers>
  </system.webServer>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d’hébergement de service](../samples/hosting.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
