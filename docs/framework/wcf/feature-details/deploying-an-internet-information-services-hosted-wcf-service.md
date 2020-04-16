---
title: Déploiement d'un service WCF hébergé dans Internet Information Services
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463857"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Déploiement d'un service WCF hébergé dans Internet Information Services

Le développement et le déploiement d’un service de la Windows Communication Foundation (WCF) hébergé dans les services d’information Sur Internet (IIS) se composent des tâches suivantes :

- Assurez-vous que l’IIS, le ASP.NET, le WCF et le composant d’activation WCF sont correctement installés et enregistrés.

- Créez une nouvelle application IIS ou réutilisez une application ASP.NET existante.

- Créez un fichier .svc pour le service WCF.

- Déployer l'implémentation de service vers l'application IIS.

- Configurer le service WCF.

Pour une procédure pas à pas détaillée de la création d’un service WCF hébergé par l’IIS, voir [Comment: Organiser un service WCF dans l’IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Vérifier que les services IIS, ASP.NET et WCF sont installés et enregistrés correctement

WCF, IIS et ASP.NET doivent être installés pour que les services WCF hébergés par l’IIS fonctionnent correctement. Les procédures d’installation de WCF (dans le cadre .NET), ASP.NET et IIS varient en fonction de votre système d’exploitation. Pour plus d’informations sur l’installation de WCF et le cadre .NET, voir [Installer le cadre .NET pour les développeurs](../../install/guide-for-developers.md). Pour installer IIS sur Windows 10, ouvrez **les programmes et les fonctionnalités** dans le panneau de **contrôle,** puis **sélectionnez Activez ou éteignez les fonctionnalités De Windows**. Dans **Windows Features**, sélectionnez des services **d’information Internet,** puis choisissez **OK**.

![Caractéristiques Windows avec IIS mis en évidence](./media/windows-features-iis.png)

Les instructions pour installer l’IIS sur d’autres systèmes d’exploitation peuvent être trouvées à [Install IIS sur Windows Vista et Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) et [installer IIS 8.5 sur Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Le processus d’installation de .NET Framework enregistre automatiquement WCF avec IIS si l’IIS est déjà présent sur la machine. Si l’IIS est installé après le cadre .NET, une étape supplémentaire est nécessaire pour enregistrer WCF auprès de l’IIS et ASP.NET. Pour ce faire, procédez comme suit selon votre système d'exploitation :

- Windows 7 et Windows Server 2003: Utilisez [l’outil d’enregistrement De l’outil d’enregistrement de modèle de service (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) pour enregistrer WCF auprès de l’IIS. Pour utiliser cet outil, tapez **ServiceModelReg.exe /i /x** dans le [Developer Command Prompt pour Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Enfin, vous devez vérifier que ASP.NET est configuré pour utiliser la version cadre .NET 4 ou plus tard. Pour ce faire, vous exécutez l’outil ASPNET_Regiis avec l’option. `–i` Pour plus d’informations, voir [ASP.NET outil d’enregistrement DE l’IIS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Créer une nouvelle application IIS ou réutiliser une application ASP.NET existante

Les services WCF hébergés par l’IIS doivent résider à l’intérieur d’une demande d’IIS. Vous pouvez créer une nouvelle application IIS pour héberger exclusivement les services WCF. Alternativement, vous pouvez déployer un service WCF dans une application existante qui héberge déjà ASP.NET contenu 2.0 (tels que les pages .aspx et ASP.NET services Web [ASMX]). Pour plus d’informations sur ces options, voir les sections « Hébergement WCF Side-by-Side with ASP.NET » et « Hosting WCF Services in ASP.NET Compatibility Mode » dans les sections [WCF Services et ASP.NET](wcf-services-and-aspnet.md).

Notez que les versions IIS 6.0 et ultérieures redémarrent périodiquement une application de programmation orientée objet isolé. La valeur par défaut est 1740 minutes. La valeur maximale est de 71,582 minutes. Ce redémarrage peut être désactivé. Pour plus d’informations sur cette propriété, voir le [PeriodicRestartTime](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Créer un fichier .svc pour le service WCF

Les services WCF hébergés dans l’IIS sont représentés sous forme de fichiers de contenu spéciaux (.fichiers svc) à l’intérieur de l’application IIS. Ce modèle est semblable à la façon dont les pages ASMX sont représentées dans une application IIS sous la forme de fichiers .asmx. Un fichier .svc contient une directive de traitement spécifique à la WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) qui permet à l’infrastructure d’hébergement WCF d’activer les services hébergés en réponse aux messages entrants. La syntaxe la plus courante d'un fichier .svc se trouve dans l'instruction suivante.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Il se compose de la `Service` [ \@directive ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) et d’un attribut unique, . La valeur de l'attribut `Service` est le nom de type du Common Language Runtime (CLR) de l'implémentation de service. L'utilisation de cette directive revient essentiellement à créer un hôte de service à l'aide du code suivant :

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

La configuration d'hébergement supplémentaire, telle que la création d'une liste d'adresses de base pour le service peut aussi être effectuée. Vous pouvez aussi utiliser un <xref:System.ServiceModel.Activation.ServiceHostFactory> personnalisé pour étendre la directive et l'utiliser avec des solutions d'hébergement personnalisées. Les applications IIS qui hébergent les services WCF <xref:System.ServiceModel.ServiceHost> ne sont pas responsables de la gestion de la création et de la durée de vie des instances. L’infrastructure d’hébergement WCF gérée crée l’instance nécessaire <xref:System.ServiceModel.ServiceHost> de façon dynamique lorsque la première demande est reçue pour le fichier .svc. L'instance n'est pas libérée tant qu'elle n'est pas fermée explicitement par le code ou que l'application est recyclée.

Pour plus d’informations sur la syntaxe pour les fichiers .svc, voir [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Déployer l'implémentation de service vers l'application IIS

Les services WCF hébergés dans l’IIS utilisent le même modèle de compilation dynamique que ASP.NET 2.0. Tout comme avec ASP.NET, vous pouvez déployer le code de implémentation des services WCF hébergés par l’IIS de plusieurs façons à différents endroits, comme suit :

- Sous forme d'un fichier .dll précompilé situé dans le cache d'assembly global (GAC, Global Assembly Cache) ou dans le répertoire \bin de l'application. Les binaires précompilés ne sont pas mis à jour tant qu'une nouvelle version de la bibliothèque de classes n'a pas été déployée.

- En tant que fichiers sources non compilés situés dans l’annuaire de l’application App_Code. Les fichiers sources situés dans ce répertoire sont requis dynamiquement lors du traitement de la première demande de l'application. Les modifications apportées aux fichiers dans le répertoire \App_Code provoque le recyclage et la recompilation de l'application toute entière lorsque la demande suivante est reçue.

- Comme code non comillé placé directement dans le fichier .svc. Le code de implémentation peut également être situé en \@ligne dans le fichier .svc du service, après la directive ServiceHost. Les transformations apportées au code inline provoquent le recyclage et la recompilation de l'application lorsque la demande suivante est reçue.

Pour plus d’informations sur le modèle de compilation ASP.NET 2.0, voir [ASP.NET Aperçu de la compilation](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>Configurer le service WCF

Les services WCF hébergés par l’IIS stockent leur configuration dans le fichier Web.config applications. Les services hébergés par l’IIS utilisent les mêmes éléments de configuration et la même syntaxe que les services WCF hébergés en dehors de l’IIS. Toutefois, les contraintes suivantes sont uniques à l'environnement d'hébergement IIS :

- Adresses de base pour les services hébergés dans IIS.

- Les applications hébergeant des services WCF en dehors de l’IIS peuvent contrôler l’adresse de base des services qu’ils hébergent en passant un ensemble d’URL d’adresse de base au <xref:System.ServiceModel.ServiceHost> constructeur ou en fournissant un [ \<élément>hôte](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) dans la configuration du service. Les services hébergés dans IIS n'ont pas la capacité de contrôler leur adresse de base ; l'adresse de base d'un service hébergé dans IIS est l'adresse de son fichier .svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresses de point de terminaison pour les services hébergés dans IIS

Lorsqu'elles sont hébergées dans IIS, les adresses de point de terminaison sont toujours considérées relatives à l'adresse du fichier .svc qui représente le service. Par exemple, si l’adresse de `http://localhost/Application1/MyService.svc` base d’un service WCF est avec la configuration de point de terminaison suivante :

```xml
<endpoint address="anotherEndpoint" />
```

Cela fournit un point de `http://localhost/Application1/MyService.svc/anotherEndpoint`terminaison qui peut être atteint à .

De même, l’élément de configuration de point de terminaison `http://localhost/Application1/MyService.svc`qui utilise une chaîne vide comme l’adresse relative fournit un point d’évaluation accessible à , qui est l’adresse de base.

```xml
<endpoint address="" />
```

Vous devez toujours utiliser des adresses de point de terminaison relatives pour les points de terminaison de service hébergés dans IIS. Fournir une adresse de point de terminaison entièrement qualifiée (par exemple) `http://localhost/MyService.svc`peut entraîner des erreurs dans le déploiement du service si l’adresse de point final ne pointe pas vers l’application IIS qui héberge le service exposant le point de terminaison. L'utilisation d'adresses de point de terminaison relatives pour les services hébergés évite ces risques de conflits.

### <a name="available-transports"></a>Transports disponibles

Les services WCF hébergés dans LES IIS 5.1 et IIS 6.0 sont limités à l’utilisation de la communication http://HTTP. Sur ces plateformes IIS, configurer un service hébergé pour utiliser une liaison non-HTTP entraîne une erreur pendant l'activation du service. Pour l’IIS 7.0, les transports pris en charge comprennent HTTP, Net.TCP, Net.Pipe, Net.MSMQ et msmq.formatname pour la compatibilité à l’envers avec les applications EXISTANTEs msMQ.

### <a name="http-transport-security"></a>Sécurité de transport HTTP

Les services WCF hébergés par l’IIS peuvent utiliser la sécurité des transports HTTP (par exemple, les systèmes d’authentification HTTPS et HTTP tels que Basic, Digest et Windows Integrated Authentication) à l’aide de l’annuaire virtuel DE l’IIS qui contient le service prend en charge ces paramètres. Les paramètres de la sécurité de transport HTTP sur la liaison d'un point de terminaison hébergé doivent correspondre aux paramètres de sécurité de transport sur le répertoire virtuel IIS qui la contient.

Par exemple, un point de terminaison WCF configuré pour utiliser l’authentification DE digestion HTTP doit résider dans un répertoire virtuel IIS qui est également configuré pour permettre l’authentification DE digestion HTTP. Des combinaisons inégalées de paramètres IIS et de paramètres de point de terminaison WCF entraînent une erreur lors de l’activation du service.

## <a name="see-also"></a>Voir aussi

- [Hébergement dans les services IIS (Internet Information Services)](hosting-in-internet-information-services.md)
- [Meilleures pratiques pour l'hébergement dans Internet Information Services](internet-information-services-hosting-best-practices.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
