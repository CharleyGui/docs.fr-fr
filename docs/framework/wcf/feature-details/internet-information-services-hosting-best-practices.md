---
title: Meilleures pratiques pour l'hébergement dans Internet Information Services
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184716"
---
# <a name="internet-information-services-hosting-best-practices"></a>Meilleures pratiques pour l'hébergement dans Internet Information Services
Ce sujet décrit quelques meilleures pratiques pour accueillir les services de la Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implémentation des services WCF comme DLL  
 La mise en œuvre d’un service WCF en tant que DLL qui est déployée à l’annuaire d’une application Web vous permet de réutiliser le service en dehors du modèle d’application Web, par exemple, dans un environnement de test qui peut ne pas avoir des services d’information Internet (IIS) déployés.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hôtes de service dans les applications hébergées par IIS  
 N’utilisez pas les API auto-hôtes impératives pour créer de nouveaux hôtes de service qui écoutent sur les transports réseau non pris en charge par l’environnement d’hébergement DE l’IIS (par exemple, IIS 6.0 pour accueillir les services TCP, parce que la communication TCP n’est pas soutenue par les autochtones sur l’IIS 6.0). Cette approche n'est pas recommandée. Les hôtes de service créés de manière impérative ne sont pas connus dans l'environnement d'hébergement IIS. Le point critique est que le traitement effectué par les services créés de manière impérative n'est pas pris en charge par les services IIS lorsqu'il détermine si le pool d'applications d'hébergement est inactif. Le résultat est que les applications qui possèdent ce type d'hôtes de service ont un environnement d'hébergement IIS qui élimine systématiquement les processus d'hôte IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI et points de terminaison hébergés par IIS  
 Les points de terminaison pour un service hébergé par IIS doivent être configurés à l'aide d'URI relatifs, pas d'adresses absolues. De cette manière, vous êtes certain que l'adresse du point de terminaison se situe dans le jeu des adresses URI qui appartiennent à l'application d'hébergement et que l'activation basée sur message se produit comme prévu.  
  
## <a name="state-management-and-process-recycling"></a>Gestion des états et recyclage de processus  
 L'environnement d'hébergement IIS est optimisé pour les services qui ne maintiennent pas l'état local en mémoire. Les services IIS recyclent le processus hôte en réponse à divers événements externes et internes, ce qui peut entraîner la perte de tout état volatil stocké exclusivement dans la mémoire. Les services hébergés dans IIS doivent stocker leur état en dehors du processus (par exemple, dans une base de données) ou dans un cache en mémoire qui peut être recréé facilement si un événement de recyclage d'application se produit.  
  
> [!NOTE]
> Les protocoles que WCF utilise pour la fiabilité et la sécurité des couches de messages utilisent l’état volatil de la mémoire. Les sessions fiables et de sécurité WCF peuvent se terminer de façon inattendue en raison de recyclements d’applications. Les applications hébergées par l’IIS qui utilisent ces protocoles devraient dépendre soit d’autre chose que la clé de session fournie par WCF pour corrélation de l’état de la couche d’application (par exemple, une construction de couche d’application ou un en-tête de corrélation personnalisé) ou désactiver Recyclage de processus IIS pour l’application hébergée.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimisation des performances dans les scénarios de couche intermédiaire  
 Pour obtenir des performances optimales dans un *scénario de niveau intermédiaire*— un service qui appelle à d’autres services en réponse aux messages entrants — instantanément le client du service WCF au service à distance une fois et le réutiliser à travers plusieurs demandes entrantes. L’instantanéise des clients du service WCF est une opération coûteuse par rapport à l’appel de service sur une instance client préexistante, et les scénarios de niveau intermédiaire produisent des gains de performance distincts en cachant des clients distants à travers les demandes. Les clients du service WCF sont sans fil, il n’est donc pas nécessaire de synchroniser l’accès à un client sur plusieurs threads.  
  
 Les scénarios de couche intermédiaire produisent également des gains de performance en utilisant les API asynchrones générées par l'option `svcutil /a`. L’option `/a` oblige [l’outil utilitaire de métadonnées de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à générer des `BeginXXX/EndXXX` méthodes pour chaque opération de service, ce qui permet d’appeler potentiellement de longue durée vers des services distants sur les fils de fond.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF dans des scénarios multi-résidents ou multi-nommés  
 Vous pouvez déployer des services WCF à l’intérieur d’une ferme Web `http://www.contoso.com`DE l’IIS, où un ensemble `http://www.contoso.com` d’ordinateurs partagent un nom `http://machine1.internal.contoso.com` `http://machine2.internal.contoso.com`externe commun (tel que ) mais sont adressés individuellement par différents noms d’hôte (par exemple, peut diriger le trafic vers deux machines différentes nommées et ). Ce scénario de déploiement est entièrement pris en charge par WCF, mais nécessite une configuration spéciale du site Web DE l’IIS hébergeant des services WCF pour afficher le nom d’hôte correct (externe) dans les métadonnées du service (Web Services Description Language).  
  
 Pour vous assurer que le nom d’hôte correct apparaît dans les métadonnées de service générées par WCF, configurez l’identité par défaut du site Web IIS qui héberge les services WCF pour utiliser un nom d’hôte explicite. Par exemple, les ordinateurs `www.contoso.com` qui résident à l’intérieur de la ferme devraient utiliser un site IIS de liaison de :80:www.contoso.com pour HTTP et \*:443:www.contoso.com pour HTTPS.  
  
 Vous pouvez configurer des liaisons de site web IIS en utilisant le composant logiciel enfichable IIS Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Les pools d'applications qui s'exécutent dans des contextes d'utilisateur différents remplacent des assemblys d'autres comptes dans le dossier temporaire  
 Pour s’assurer que les pools d’applications fonctionnant dans différents contextes d’utilisateurs ne peuvent pas remplacer les assemblages d’autres comptes dans le dossier de fichiers ASP.NET temporaires, utilisez différentes identités et dossiers temporaires pour différentes applications. Par exemple, si vous avez deux applications virtuelles /Application1 et / Application2, vous pouvez créer deux pools d'applications, A et B, avec deux identités différentes. Le pool d'applications A peut s'exécuter sous une identité d'utilisateur (user1), et le pool d'applications B peut s'exécuter sous une autre identité d'utilisateur (user2), et configurer /Application1 pour utiliser A et /Application2 pour utiliser B.  
  
 Dans Web.config, vous pouvez configurer \< system.web/compilation/@tempFolder le dossier temporaire à l’aide de>. Pour /Application1, il peut s’agir de "c:'tempForUser1" et pour l’application2, il peut être "c:'tempForUser2". Accordez l’autorisation en écriture correspondante à ces dossiers pour les deux identités.  
  
 Dès lors, user2 ne peut pas modifier le dossier de génération du code pour /application2 (sous c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Activation du traitement asynchrone  
 Par défaut, les messages envoyés à un service WCF hébergé sous IIS 6.0 et plus tôt sont traités de manière synchrone. ASP.NET appelle WCF sur son propre thread (le fil de travailleur ASP.NET) et WCF utilise un autre thread pour traiter la demande. WCF met en attente le thread de travail ASP.NET jusqu'à la fin du traitement. Cela conduit au traitement synchrone des demandes. Le traitement des demandes permet asynchronement une plus grande évolutivité, car il réduit le nombre de threads nécessaires pour traiter une demande -WCF ne s’accroche pas au fil ASP.NET pendant le traitement de la demande. L’utilisation d’un comportement asynchrone n’est pas recommandée pour les machines fonctionnant en état d’exécution IIS 6.0 parce qu’il n’y a aucun moyen d’étrangler les demandes entrantes qui ouvrent le serveur à des attaques *de déni de service* (DOS). Depuis IIS 7.0, une limitation des demandes simultanées a été mise en place : `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Grâce à cette nouvelle limitation, l'utilisation du traitement asynchrone peut s'effectuer en toute sécurité.  Par défaut dans IIS 7.0, le gestionnaire asynchrone et le module sont inscrits. Si cette option a été désactivée, vous pouvez activer manuellement le traitement asynchrone des demandes dans le fichier Web.config de votre application. Les paramètres que vous utilisez dépendent de votre paramètre `aspNetCompatibilityEnabled`. Si `aspNetCompatibilityEnabled` a la valeur `false`, configurez `System.ServiceModel.Activation.ServiceHttpModule` comme illustré dans l'extrait de configuration suivant.  
  
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

- [Échantillons d’hébergement de service](../samples/hosting.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
