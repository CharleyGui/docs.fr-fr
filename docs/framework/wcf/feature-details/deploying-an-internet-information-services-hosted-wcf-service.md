---
title: Déploiement d'un service WCF hébergé dans Internet Information Services
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 826a8798ada8f04173b047dc27829c384f79e2b8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599241"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Déploiement d'un service WCF hébergé dans Internet Information Services

Le développement et le déploiement d’un service Windows Communication Foundation (WCF) hébergé dans Internet Information Services (IIS) se composent des tâches suivantes :

- Assurez-vous qu’IIS, ASP.NET, WCF et le composant d’activation WCF sont correctement installés et inscrits.

- Créer une application IIS ou réutiliser une application ASP.NET existante.

- Créez un fichier. svc pour le service WCF.

- Déployer l'implémentation de service vers l'application IIS.

- Configurez le service WCF.

Pour obtenir une procédure pas à pas détaillée de la création d’un service WCF hébergé par IIS, voir [Comment : héberger un service WCF dans IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Vérifier que les services IIS, ASP.NET et WCF sont installés et enregistrés correctement

WCF, IIS et ASP.NET doivent être installés pour que les services WCF hébergés dans IIS fonctionnent correctement. Les procédures d’installation de WCF (dans le cadre de l' .NET Framework), ASP.NET et IIS varient en fonction de votre système d’exploitation. Pour plus d’informations sur l’installation de WCF et du .NET Framework, consultez [installer le .NET Framework pour les développeurs](../../install/guide-for-developers.md). Pour installer IIS sur Windows 10, ouvrez **programmes et fonctionnalités** dans **le panneau de configuration** , puis sélectionnez **activer ou désactiver des fonctionnalités Windows**. Dans **fonctionnalités de Windows**, sélectionnez **Internet Information Services** , puis choisissez **OK**.

![Fonctionnalités Windows avec IIS en surbrillance](./media/windows-features-iis.png)

Pour obtenir des instructions sur l’installation d’IIS sur d’autres systèmes d’exploitation, consultez [installer IIS sur Windows Vista et Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) et [installer IIS 8,5 sur Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Le processus d’installation de .NET Framework inscrit automatiquement WCF auprès d’IIS si IIS est déjà présent sur l’ordinateur. Si IIS est installé après le .NET Framework, une étape supplémentaire est nécessaire pour inscrire WCF auprès d’IIS et de ASP.NET. Pour ce faire, procédez comme suit selon votre système d'exploitation :

- Windows 7 et Windows Server 2003 : utilisez l’outil [ServiceModel Registration Tool (ServiceModelReg. exe)](../servicemodelreg-exe.md) pour inscrire WCF auprès d’IIS. Pour utiliser cet outil, tapez **ServiceModelReg. exe/i/x** dans le [invite de commandes développeur pour Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7 : Enfin, vous devez vérifier que ASP.NET est configuré pour utiliser le .NET Framework version 4 ou ultérieure. Pour ce faire, exécutez l’outil ASPNET_Regiis avec l' `–i` option. Pour plus d’informations, consultez [ASP.NET IIS Registration Tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Créer une nouvelle application IIS ou réutiliser une application ASP.NET existante

Les services WCF hébergés dans IIS doivent résider dans une application IIS. Vous pouvez créer une application IIS pour héberger des services WCF exclusivement. Vous pouvez également déployer un service WCF dans une application existante qui héberge déjà le contenu ASP.NET 2,0 (comme les pages. aspx et les services Web ASP.NET [ASMX]). Pour plus d’informations sur ces options, consultez les sections « Hébergement de WCF côte à côte avec ASP.NET » et « Hébergement de services WCF en mode de compatibilité ASP.NET » dans [services WCF et ASP.net](wcf-services-and-aspnet.md).

Notez que IIS 6,0 et versions ultérieures redémarrent périodiquement une application de programmation orientée objet isolée. La valeur par défaut est 1740 minutes. La valeur maximale est de 71,582 minutes. Ce redémarrage peut être désactivé. Pour plus d’informations sur cette propriété, consultez [PeriodicRestartTime](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Créer un fichier .svc pour le service WCF

Les services WCF hébergés dans IIS sont représentés sous forme de fichiers de contenu spéciaux (fichiers. svc) à l’intérieur de l’application IIS. Ce modèle est semblable à la façon dont les pages ASMX sont représentées dans une application IIS sous la forme de fichiers .asmx. Un fichier. svc contient une directive de traitement spécifique à WCF[ \@ ](../../configure-apps/file-schema/wcf-directive/servicehost.md)qui permet à l’infrastructure d’hébergement WCF d’activer des services hébergés en réponse à des messages entrants. La syntaxe la plus courante d'un fichier .svc se trouve dans l'instruction suivante.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Il se compose de la directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) et d’un attribut unique, `Service` . La valeur de l'attribut `Service` est le nom de type du Common Language Runtime (CLR) de l'implémentation de service. L'utilisation de cette directive revient essentiellement à créer un hôte de service à l'aide du code suivant :

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

La configuration d'hébergement supplémentaire, telle que la création d'une liste d'adresses de base pour le service peut aussi être effectuée. Vous pouvez aussi utiliser un <xref:System.ServiceModel.Activation.ServiceHostFactory> personnalisé pour étendre la directive et l'utiliser avec des solutions d'hébergement personnalisées. Les applications IIS qui hébergent les services WCF ne sont pas responsables de la gestion de la création et de la durée de vie des <xref:System.ServiceModel.ServiceHost> instances. L’infrastructure d’hébergement WCF gérée crée l' <xref:System.ServiceModel.ServiceHost> instance nécessaire dynamiquement lorsque la première demande est reçue pour le fichier. svc. L'instance n'est pas libérée tant qu'elle n'est pas fermée explicitement par le code ou que l'application est recyclée.

Pour plus d’informations sur la syntaxe des fichiers. svc, consultez [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Déployer l'implémentation de service vers l'application IIS

Les services WCF hébergés dans IIS utilisent le même modèle de compilation dynamique que ASP.NET 2,0. Tout comme avec ASP.NET, vous pouvez déployer le code d’implémentation pour les services WCF hébergés par IIS de plusieurs façons à différents emplacements, comme suit :

- Sous forme d'un fichier .dll précompilé situé dans le cache d'assembly global (GAC, Global Assembly Cache) ou dans le répertoire \bin de l'application. Les binaires précompilés ne sont pas mis à jour tant qu'une nouvelle version de la bibliothèque de classes n'a pas été déployée.

- En tant que fichiers sources non compilés situés dans le répertoire \ App_Code de l’application. Les fichiers sources situés dans ce répertoire sont requis dynamiquement lors du traitement de la première demande de l'application. Les modifications apportées aux fichiers dans le répertoire \App_Code provoque le recyclage et la recompilation de l'application toute entière lorsque la demande suivante est reçue.

- En tant que code non compilé placé directement dans le fichier. svc. Le code d’implémentation peut également être localisé en ligne dans le fichier. svc du service, après la \@ directive ServiceHost. Les transformations apportées au code inline provoquent le recyclage et la recompilation de l'application lorsque la demande suivante est reçue.

Pour plus d’informations sur le modèle de compilation ASP.NET 2,0, consultez [vue d’ensemble de la compilation ASP.net](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>Configurer le service WCF

Les services WCF hébergés dans IIS stockent leur configuration dans le fichier Web. config des applications. Les services hébergés dans IIS utilisent les mêmes éléments de configuration et la même syntaxe que les services WCF hébergés en dehors d’IIS. Toutefois, les contraintes suivantes sont uniques à l'environnement d'hébergement IIS :

- Adresses de base pour les services hébergés dans IIS.

- Les applications hébergeant des services WCF en dehors d’IIS peuvent contrôler l’adresse de base des services qu’elles hébergent en passant un ensemble d’URI d’adresse de base au <xref:System.ServiceModel.ServiceHost> constructeur ou en fournissant un [\<host>](../../configure-apps/file-schema/wcf/host.md) élément dans la configuration du service. Les services hébergés dans IIS n'ont pas la capacité de contrôler leur adresse de base ; l'adresse de base d'un service hébergé dans IIS est l'adresse de son fichier .svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresses de point de terminaison pour les services hébergés dans IIS

Lorsqu'elles sont hébergées dans IIS, les adresses de point de terminaison sont toujours considérées relatives à l'adresse du fichier .svc qui représente le service. Par exemple, si l’adresse de base d’un service WCF est `http://localhost/Application1/MyService.svc` avec la configuration de point de terminaison suivante :

```xml
<endpoint address="anotherEndpoint" />
```

Cela fournit un point de terminaison qui peut être atteint à l’adresse `http://localhost/Application1/MyService.svc/anotherEndpoint` .

De même, l’élément de configuration de point de terminaison qui utilise une chaîne vide comme adresse relative fournit un point de terminaison accessible à `http://localhost/Application1/MyService.svc` , qui est l’adresse de base.

```xml
<endpoint address="" />
```

Vous devez toujours utiliser des adresses de point de terminaison relatives pour les points de terminaison de service hébergés dans IIS. La fourniture d’une adresse de point de terminaison qualifiée complète (par exemple, `http://localhost/MyService.svc` ) peut entraîner des erreurs dans le déploiement du service si l’adresse de point de terminaison ne pointe pas vers l’application IIS qui héberge le service exposant le point de terminaison. L'utilisation d'adresses de point de terminaison relatives pour les services hébergés évite ces risques de conflits.

### <a name="available-transports"></a>Transports disponibles

Les services WCF hébergés dans IIS 5,1 et IIS 6,0 sont limités à l’utilisation de la communication basée sur HTTP. Sur ces plateformes IIS, configurer un service hébergé pour utiliser une liaison non-HTTP entraîne une erreur pendant l'activation du service. Pour IIS 7,0, les transports pris en charge incluent HTTP, net. TCP, net. pipe, net. MSMQ et MSMQ. FormatName pour la compatibilité descendante avec les applications MSMQ existantes.

### <a name="http-transport-security"></a>Sécurité de transport HTTP

Les services WCF hébergés par IIS peuvent utiliser la sécurité de transport HTTP (par exemple, les schémas d’authentification HTTPS et http, tels que l’authentification de base, Digest et Windows intégrée) tant que le répertoire virtuel IIS qui contient le service prend en charge ces paramètres. Les paramètres de la sécurité de transport HTTP sur la liaison d'un point de terminaison hébergé doivent correspondre aux paramètres de sécurité de transport sur le répertoire virtuel IIS qui la contient.

Par exemple, un point de terminaison WCF configuré pour utiliser l’authentification Digest HTTP doit résider dans un répertoire virtuel IIS qui est également configuré pour autoriser l’authentification Digest HTTP. Des combinaisons non appariées de paramètres IIS et de paramètres de point de terminaison WCF provoquent une erreur pendant l’activation du service.

## <a name="see-also"></a>Voir aussi

- [Hébergement dans les services IIS (Internet Information Services)](hosting-in-internet-information-services.md)
- [Meilleures pratiques pour l'hébergement dans Internet Information Services](internet-information-services-hosting-best-practices.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
