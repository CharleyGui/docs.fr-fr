---
title: Migrer votre application ou service web .NET vers Azure App Service
description: En savoir plus sur la migration d’une application ou d’un service Web .NET d’un site local vers un Azure App Service.
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: a5e193b2dbaedb86ff0e24bc8b70043896bbeea3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539084"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Migrer votre application ou service web .NET vers Azure App Service

[App service](/azure/app-service/overview) est un service de plateforme de calcul entièrement géré qui est optimisé pour héberger des sites Web évolutifs et des applications Web. Cet article fournit des informations sur la façon de lever-déplacer une application existante vers Azure App Service, les modifications à prendre en compte et des ressources supplémentaires pour [migrer vers le Cloud](https://azure.microsoft.com/migration/web-applications/). La plupart des sites web ASP.NET (WebForms, MVC) et des services (API Web, WCF) peuvent passer directement à Azure App Service, sans aucune modification. Certains peuvent nécessiter des modifications mineures tandis que d’autres peuvent nécessiter une refactorisation.

Prêt à vous lancer ? [Publiez une application ASP.NET + SQL sur Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Considérations

### <a name="on-premises-resources-including-sql-server"></a>Ressources locales (y compris SQL Server)

Vérifiez l’accès aux ressources locales, car elles peuvent nécessiter une migration ou des modifications. Les options suivantes permettent de limiter l’accès aux ressources locales :

* Créez un VPN connectant App Service aux ressources locales à l’aide des [Réseaux virtuels Azure](/azure/app-service/web-sites-integrate-with-vnet).
* Exposez les services locaux au cloud de manière sécurisée sans modification du pare-feu à l’aide de [Azure Relay](/azure/service-bus-relay/relay-what-is-it).
* Migrez des dépendances comme une [base de données SQL](https://go.microsoft.com/fwlink/?linkid=863217) vers Azure.
* Utilisez des offres de plateforme en tant que service dans le Cloud pour réduire les dépendances. Par exemple, plutôt que de vous connecter à un serveur de messagerie sur site, envisagez d’utiliser [SendGrid](/azure/sendgrid-dotnet-how-to-send-email).

### <a name="port-bindings"></a>Liaisons de port

Azure App Service prend en charge le port 80 pour le trafic HTTP et le port 443 pour le trafic HTTPS.

Les liaisons suivantes sont prises en charge pour WCF :

| Liaison | Notes |
|--|--|
| `BasicHttp` |  |
| `WSHttp` |  |
| `WSDualHttpBinding` | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée. | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée. |
| `NetHttpBinding` | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée pour les contrats duplex. | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée pour les contrats duplex. |
| `NetHttpsBinding` | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée pour les contrats duplex. | La [prise en charge de Websocket](/azure/app-service/web-sites-configure) doit être activée pour les contrats duplex. |
| `BasicHttpContextBinding` |  |
| `WebHttpBinding` |  |
| `WSHttpContextBinding` |  |

### <a name="authentication"></a>Authentification

Azure App Service prend en charge l’authentification anonyme par défaut et l’authentification par formulaire lorsque cela est nécessaire. L’authentification Windows peut être utilisée uniquement en cas d’intégration à Azure Active Directory et ADFS. [Découvrez comment intégrer vos répertoires locaux à Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Assemblys dans le GAC (Global Assembly Cache)

Ceci n’est pas pris en charge. Envisagez de copier les assemblys requis dans le dossier *\Bin* de l’application. Les fichiers *. msi* personnalisés installés sur le serveur (par exemple, les générateurs de PDF) ne peuvent pas être utilisés.

### <a name="iis-settings"></a>Paramètres IIS

Tout ce qui est habituellement configuré via applicationHost.config dans votre application peut maintenant être configuré via le portail Azure. Cela s’applique au nombre de bits AppPool, à l’activation/désactivation de WebSockets, à la version de pipeline gérée, à la version .NET Framework (2.0/4.0), etc. Pour modifier vos [paramètres d’application](/azure/app-service/web-sites-configure), accédez au [portail Azure](https://portal.azure.com), ouvrez le panneau de votre application web, puis sélectionnez l’onglet **Paramètres de l’application**.

#### <a name="iis5-compatibility-mode"></a>Mode de compatibilité IIS5

Le mode de compatibilité IIS5 n’est pas pris en charge. Dans Azure App Service, chaque application Web et toutes les applications qu’elle contient s’exécutent dans le même processus de travail avec un ensemble spécifique de [pools d’applications](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)).

#### <a name="iis7-schema-compliance"></a>Conformité de schéma IIS7+

Certains éléments et attributs ne sont pas définis dans le schéma IIS Azure App Service. Si vous rencontrez des problèmes, envisagez d’utiliser des [transformations XDT](/azure/app-service/configure-common).

#### <a name="single-application-pool-per-site"></a>Pool d’applications unique par site

Dans Azure App Service, chaque application Web et toutes les applications qu’elle contient s’exécutent dans le même pool d’applications. Envisagez d’établir un pool d’applications unique avec des paramètres communs ou de créer une application Web distincte pour chaque application.

### <a name="com-and-com-components"></a>Composants COM et COM+

Azure App Service n’autorise pas l’inscription de composants COM sur la plateforme. Si votre application utilise des composants COM, ceux-ci doivent être réécrits en code managé et déployés avec le site ou l’application.

### <a name="physical-directories"></a>Répertoires physiques

Azure App Service n’autorise pas l’accès au lecteur physique. Vous devrez peut-être utiliser [Azure Files](/azure/storage/files/storage-files-introduction) pour accéder aux fichiers via SMB. Le [Stockage Blob Azure](/azure/storage/blobs/storage-blobs-introduction) peut stocker des fichiers pour l’accès via HTTPS.

### <a name="isapi-filters"></a>Filtres ISAPI

Azure App Service peut prendre en charge l’utilisation de filtres ISAPI, toutefois, la DLL ISAPI doit être déployée avec votre site et inscrite via le fichier web.config.

### <a name="https-bindings-and-ssl"></a>Liaisons HTTPS et SSL

Les liaisons HTTPs ne sont pas migrées, ni les certificats SSL associés à vos sites Web. [Les certificats SSL peuvent être téléchargés manuellement](/azure/app-service/app-service-web-tutorial-custom-ssl) après que la migration du site soit terminée.

### <a name="sharepoint-and-frontpage"></a>SharePoint et FrontPage

Les extensions de serveur SharePoint et FrontPage (FPSE) ne sont pas prises en charge.

### <a name="web-site-size"></a>Taille du site web

Les sites gratuits ont une limite de taille de 1 Go de contenu. Si la taille de votre site est supérieure à 1 Go, vous devez mettre à niveau vers une référence SKU payante. Consultez [app service tarification](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="database-size"></a>Taille de la base de données

Pour les bases de données SQL Server, consultez la [tarification SQL Database](https://azure.microsoft.com/pricing/details/sql-database) actuelle.

### <a name="azure-active-directory-aad-integration"></a>Intégration d’Azure Active Directory (AAD)

AAD ne fonctionne pas avec les applications gratuites. Pour utiliser l’authentification AAD, vous devez mettre à niveau la référence SKU de l’application. Consultez [app service tarification](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Surveillance et diagnostics

Il est peu probable que vos solutions locales actuelles d’analyse et de diagnostics fonctionnent dans le cloud. Toutefois, Azure fournit des outils pour la journalisation, l’analyse et les diagnostics afin que vous puissiez identifier et résoudre les problèmes liés aux applications web. Vous pouvez facilement activer les diagnostics pour votre application web dans sa configuration, et afficher les journaux d’activité enregistrés dans Azure Application Insights. [En savoir plus sur l’activation de la journalisation des diagnostics pour les applications web](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Chaînes de connexion et paramètres d’application

Envisagez d’utiliser [Azure KeyVault](/azure/key-vault/), un service qui stocke en toute sécurité les informations sensibles utilisées dans votre application. Vous pouvez également stocker ces données sous forme de paramètre App Service.

### <a name="dns"></a>DNS

Vous devrez peut-être mettre à jour les configurations DNS selon les besoins de votre application. Ces paramètres DNS peuvent être configurés dans les [paramètres de domaine personnalisés](/azure/app-service/app-service-web-tutorial-custom-domain) d’App Service.

## <a name="azure-app-service-with-windows-containers"></a>Azure App Service avec des conteneurs Windows

Si votre application ne peut pas être migrée directement vers App Service, envisagez d’utiliser App Service à l’aide de conteneurs Windows, ce qui permet l’utilisation du GAC, des composants COM, MSI, l’accès complet à .NET FX API, DirectX et bien plus encore.

## <a name="see-also"></a>Voir aussi

* [Comment déterminer si votre application est éligible à App Service](https://appmigration.microsoft.com/)
* [Transfert de votre base de données vers le cloud](sql.md)
* [Détails et restrictions du bac à sable (sandbox) de l’application Web Azure](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
