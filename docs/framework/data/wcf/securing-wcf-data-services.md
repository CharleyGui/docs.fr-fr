---
title: Sécurisation de WCF Data Services
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 4db6d7e13bfc4a0e2705c210820db511a60e09de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877352"
---
# <a name="securing-wcf-data-services"></a>Sécurisation de WCF Data Services
Cette rubrique décrit les considérations de sécurité qui sont spécifiques au développement, déploiement et en cours d’exécution WCF Data Services et applications que services d’accès qui prennent en charge le protocole Open Data Protocol (OData). Vous devez également suivre les recommandations pour la création d’applications .NET Framework sécurisées.  
  
Lorsque vous planifiez comment sécuriser un service OData basé sur WCF Data Services, vous devez prendre à la fois l’authentification, le processus de détection et de vérification de l’identité d’un principal et l’autorisation, le processus permettant de déterminer si un principal authentifié est autorisé à accéder aux ressources demandées. Vous devez également déterminer si chiffrer le message à l'aide de SSL.  
  
## <a name="authenticating-client-requests"></a>Authentification des demandes du client  
WCF Data Services n’implémente pas de n’importe quel type d’authentification de son propre, mais repose plutôt sur les dispositions d’authentification de l’hôte de service de données. Cela signifie que le service suppose que toute demande qu’il reçoit a déjà été authentifié par l’hôte de réseau et que l’hôte a correctement identifié le principal pour la demande via les interfaces fournies par WCF Data Services. Ces approches et les options d’authentification sont détaillées dans le multipart [OData et séries d’authentification](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Options d'authentification pour un service de données WCF  
 Le tableau suivant répertorie une partie des mécanismes d'authentification qui s'offrent à vous pour authentifier les demandes à un service de données WCF.  
  
|Options d’authentification|Description|  
|----------------------------|-----------------|  
|Authentification anonyme|Lorsque l'authentification anonyme HTTP est activée, n'importe quel principal est en mesure de se connecter au service de données. Les informations d'identification ne sont pas requises pour un accès anonyme. Utilisez cette option uniquement lorsque vous souhaitez autoriser tout le monde à accéder au service de données.|  
|Authentification de base et Digest|Les informations d'identification comprenant un nom d'utilisateur et un mot de passe sont requises pour l'authentification. Prend en charge l'authentification des clients non Windows. **Note de sécurité :**  Les informations d'authentification de base (nom d'utilisateur et mot de passe) sont envoyées en clair et peuvent être interceptées. L’authentification Digest envoie un hachage en fonction des informations d’identification fournies, les sécurisant davantage par rapport à une authentification basique. Ces deux authentifications sont vulnérables aux attaques de l'intercepteur (« Man-in-the-Middle »). Lorsque vous utilisez ces méthodes d'authentification, nous vous conseillons d'utiliser une communication chiffrée entre le client et le service de données à l'aide de SSL (Secure Sockets Layer). <br /><br /> Microsoft Internet Information Services (IIS) fournit une implémentation de ces deux basic et les demandes d’authentification digest HTTP dans une application ASP.NET. L'implémentation de ce fournisseur d'authentification Windows permet à une application cliente .NET Framework de fournir les informations d'identification dans l'en-tête HTTP de la demande au service de données pour négocier de façon transparente l'authentification d'un utilisateur Windows. Pour plus d’informations, consultez [référence technique de l’authentification Digest](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Lorsque vous souhaitez avoir vos données service utiliser l’authentification de base selon certaines pas les informations d’identification Windows et le service d’authentification personnalisé, vous devez implémenter un Module HTTP de ADP.NET personnalisé pour l’authentification.<br /><br /> Pour obtenir un exemple montrant comment utiliser un schéma d’authentification personnalisé avec WCF Data Services, consultez le blog [OData et authentification-partie 6-authentification de base personnalisée](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Authentification Windows|Les informations d'identification basées sur Windows sont échangées à l'aide de NTLM ou Kerberos. Ce mécanisme est plus sécurisé que l’authentification de base ou Digest, mais requiert que le client soit une application basée sur Windows. IIS fournit également une implémentation de l’authentification Windows pour les requêtes HTTP dans une application ASP.NET. Pour plus d’informations, consultez [vue d’ensemble de l’authentification de formulaires ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Pour obtenir un exemple montrant comment utiliser l’authentification Windows avec WCF Data Services, consultez le blog [OData et l’authentification Windows de l’authentification – partie 2 –](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|Authentification par formulaire ASP.NET|L'authentification par formulaire vous permet d'authentifier des utilisateurs à l'aide de votre propre code puis de conserver un jeton d'authentification dans un cookie ou dans l'URL de la page. Vous authentifiez le nom d'utilisateur et le mot de passe de vos utilisateurs en créant un formulaire de connexion. Les demandes non authentifiées sont redirigées vers une page de connexion, où l'utilisateur fournit des informations d'identification et envoie le formulaire. Si l'application authentifie la demande, le système délivre un ticket qui contient une clé pour rétablir l'identité pour les demandes suivantes. Pour plus d’informations, consultez [fournisseur d’authentification Forms](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Note de sécurité :**  Par défaut, le cookie qui contient le ticket d’authentification de formulaires n’est pas sécurisé lorsque vous utilisez l’authentification par formulaire dans une application Web ASP.NET. Vous devriez considérer l'utilisation de SSL pour protéger le ticket d'authentification et les informations d'identification de la connexion initiale. <br /><br /> Pour un exemple montrant comment utiliser des formulaires d’authentification avec WCF Data Services, consultez le billet de blog [OData et l’authentification par formulaire de l’authentification – partie 7 –](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Authentification basée sur les revendications|Dans l’authentification basée sur les revendications, le service de données s’appuie sur un service de fournisseur d’identité « tiers » approuvé pour authentifier l’utilisateur. Le fournisseur d'identité authentifie positivement l'utilisateur qui demande l'accès aux ressources du service de données et émet un jeton qui accorde l'accès aux ressources demandées. Ce jeton est ensuite présenté au service de données, qui accorde ensuite l'accès à l'utilisateur en fonction de la relation d'approbation avec le service d'identité qui émet le jeton d'accès.<br /><br /> L'avantage d'utiliser un fournisseur d'authentification basée sur les revendications est que celles-ci peuvent être utilisées pour authentifier différents types de clients entre plusieurs domaines approuvés. En utilisant un tel fournisseur tiers, un service de données peut décharger les revendications de gestion et authentification des utilisateurs. OAuth 2.0 est un protocole d'authentification basée sur les revendications pris en charge par le contrôle d'accès Microsoft Azure AppFabric pour l'autorisation fédérée en tant que service. Ce protocole prend en charge les services REST. Pour obtenir un exemple montrant comment utiliser OAuth 2.0 avec WCF Data Services, consultez le blog [OData et authentification – partie 8 – OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Authentification dans la bibliothèque cliente  
 Par défaut, la bibliothèque de client WCF Data Services ne fournit pas les informations d’identification lorsque vous élaborez une demande à un service OData. Lorsque les informations de connexions sont demandées par le service de données pour authentifier un utilisateur, elles peuvent être fournies par un <xref:System.Net.NetworkCredential> accédé depuis la propriété <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> du <xref:System.Data.Services.Client.DataServiceContext>, comme dans l'exemple suivant :  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Pour plus d'informations, voir [Procédure : Spécifiez les informations d’identification du Client pour une demande de Service de données](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Lorsque le service de données demande des informations de connexion qui ne peuvent pas être spécifiées à l'aide d'un objet <xref:System.Net.NetworkCredential>, comme un jeton ou un cookie basé sur des revendications, vous devez définir manuellement les en-têtes, généralement les en-têtes `Authorization` et `Cookie`, dans la demande HTTP. Pour plus d’informations sur ce type de scénario d’authentification, consultez le blog [ OData et authentification – partie 3 – ClientSide Hooks](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Pour obtenir un exemple montrant comment définir des en-têtes HTTP dans un message de demande, consultez [Comment : Définir des en-têtes dans la demande du Client](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>emprunt d'identité  
 Généralement, le service de données accède aux ressources demandées, comme les fichiers sur le serveur ou la base de données, à l'aide des informations d'authentification du processus de travail qui héberge actuellement le service de données. Lorsque vous utilisez l’emprunt d’identité, les applications ASP.NET peuvent s’exécuter avec l’identité Windows (compte d’utilisateur) de l’utilisateur qui effectue la requête. L'emprunt d'identité est utilisé couramment dans les applications qui reposent sur IIS pour authentifier l'utilisateur et les informations d'identification de ce principal sont utilisées pour accéder aux ressources demandées. Pour plus d’informations, consultez [emprunt d’identité ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Configuration de l'autorisation du service de données  
 L'autorisation est le fait d'autoriser l'accès aux ressources d'une application à un principal ou à un processus identifié sur la base d'une authentification précédemment réussie. En règle générale, vous ne devriez accorder aux utilisateurs du service de données que des droits suffisants pour exécuter les opérations requises par les applications clientes.  
  
### <a name="restrict-access-to-data-service-resources"></a>Restriction d'accès aux ressources du service de données  
 Par défaut, WCF Data Services vous permet d’accorder courantes accès en lecture et écriture sur les ressources de service de données (entité définie et les opérations de service) à n’importe quel utilisateur qui est en mesure d’accéder au service de données. Les règles qui définissent l'accès en lecture et écriture peuvent être définies séparément pour chaque jeu d'entité exposé par le service de données, tout comme toute opération de service. Nous vous recommandons de limiter l'accès en lecture et écriture aux seules ressources requises par l'application cliente. Pour plus d’informations, consultez [exigences d’accès Minimum ressource](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implémentation d'intercepteurs basés sur le rôle  
 Les intercepteurs vous permettent d'intercepter les demandes adressées aux ressources du service de données avant qu'elles ne soient traitées par le service de données. Pour plus d’informations, consultez [intercepteurs](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Les intercepteurs vous permettent de prendre des décisions d'autorisation en fonction de l'utilisateur authentifié qui effectue la demande. Pour obtenir un exemple montrant comment restreindre l’accès aux ressources de service de données basés sur une identité de l’utilisateur authentifié, consultez [Comment : Intercepter les Messages de Service de données](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Restriction d'accès aux ressources d'un magasin de données persistantes ou aux ressources locales  
 Les comptes que vous utilisez pour accéder au magasin de données persistantes doivent disposer uniquement des autorisations minimales pour prendre en charge les spécifications du service de données dans la base de données ou le système de fichiers. Lorsque vous utilisez une authentification anonyme, il s'agit du compte utilisé pour exécuter l'application d'hébergement. Pour plus d'informations, voir [Procédure : Développer un Service de données WCF s’exécutant sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Lorsque vous utilisez l'emprunt d'identité, les utilisateurs authentifiés doivent être autorisés à accéder à ces ressources, généralement dans le cadre d'un groupe Windows.  
  
## <a name="other-security-considerations"></a>Autres considérations à propos de la sécurité  
  
### <a name="secure-the-data-in-the-payload"></a>Sécurisation des données dans la charge utile  
OData est basée sur le protocole HTTP. Dans un message HTTP, l'en-tête peut contenir des informations d'identification utiles concernant l'utilisateur, selon l'authentification implémentée par le service de données. Le corps du message peut également contenir des données utiles sur le client, qu'il convient de protéger. Dans ces deux cas, nous vous recommandons d'utiliser SSL pour protéger ces informations lors de la transmission.  
  
### <a name="ignored-message-headers-and-cookies"></a>En-têtes et cookies de message ignorés  
 Les en-têtes des demandes HTTP autres que celles qui déclarent des types de contenu et des emplacements de ressources, sont ignorés et ne sont jamais définis par le service de données.  
  
 Les cookies utilisable comme partie d’un schéma d’authentification, comme avec l’authentification par formulaire ASP.NET. Toutefois, les cookies HTTP définis sur une demande entrante sont ignorés par DataServices de WCF. L’hôte d’un service de données peut traiter le cookie, mais le runtime WCF Data Services jamais analyse ni ne retourne les cookies. La bibliothèque de client WCF Data Services ne traite pas les cookies envoyés dans la réponse.  
  
### <a name="custom-hosting-requirements"></a>Conditions d’hébergement personnalisé  
 Par défaut, WCF Data Services est créé comme une application ASP.NET hébergée dans IIS. Cela permet au service de données de tirer parti des comportements de sécurité de cette plateforme. Vous pouvez définir les Services de données WCF qui sont hébergées par un hôte personnalisé. Pour plus d’informations, consultez [qui héberge le Service de données](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Les composants et la plateforme qui hébergent un service de données doivent assurer les comportements de sécurité suivants pour empêcher des attaques sur le service de données :  
  
- Limiter la longueur de l'URI accepté dans une demande de service de données pour toutes les opérations possibles.  
  
- Limiter la taille des messages HTTP entrants et sortants.  
  
- Limiter le nombre total de demandes sortantes à tout moment.  
  
- Limiter la taille des en-têtes HTTP et leurs valeurs et fournir un accès aux données d’en-tête WCF Data Services.  
  
- Détecter et répertorier les attaques connues, telles que TCP SYN et les attaques de relecture de message.  
  
### <a name="values-are-not-further-encoded"></a>Les valeurs ne sont pas encodées ultérieurement.  
 Les valeurs de propriété envoyées au service de données ne sont pas encodées ultérieurement par le runtime WCF Data Services. Par exemple, lorsqu’une propriété de chaîne d’une entité inclut un contenu HTML formaté, les étiquettes ne sont pas encodées en HTML par le service de données. De même, le service de données n'encode pas ultérieurement les valeurs de propriété dans la réponse. La bibliothèque du client n'exécute aucun encodage supplémentaire.  
  
### <a name="considerations-for-client-applications"></a>Considérations pour les applications clientes  
 Les considérations de sécurité suivantes s’appliquent aux applications qui utilisent le client WCF Data Services pour accéder aux services OData :  
  
- La bibliothèque du client suppose que les protocoles utilisés pour accéder au service de données fournissent un niveau de sécurité suffisant.  
  
- La bibliothèque du client utilise toutes les valeurs par défaut des délais d'attente et des options d'analyse des piles de transport fournies par la plateforme sous-jacente.  
  
- La bibliothèque du client ne lit aucun paramètre des fichiers de configuration de l'application.  
  
- La bibliothèque du client n'implémente aucun mécanisme d'accès entre domaines. En revanche, elle utilise les mécanismes fournis par la pile HTTP sous-jacente.  
  
- La bibliothèque du client ne dispose d'aucun élément d'interface utilisateur et elle ne tente jamais d'afficher ou de restituer les données qu'elle reçoit ou envoie.  
  
- Nous recommandons que les applications clientes valident toujours les entrées utilisateur et les données acceptées provenant de services non approuvés.  
  
## <a name="see-also"></a>Voir aussi

- [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
