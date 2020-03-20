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
ms.openlocfilehash: e09007e786772e838a9aaa76eb8ef7a3fe2b7cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174652"
---
# <a name="securing-wcf-data-services"></a>Sécurisation de WCF Data Services
Ce sujet décrit les considérations de sécurité spécifiques au développement, au déploiement et à l’exécution des services de données et des applications WCF qui accèdent aux services qui prennent en charge le Protocole de données ouvertes (OData). Vous devez également suivre les recommandations pour la création d’applications cadre .NET sécurisées.  
  
Lors de la planification de la façon d’obtenir un service OData basé sur les services de données WCF, vous devez aborder à la fois l’authentification, le processus de découverte et de vérification de l’identité d’un mandant et l’autorisation, le processus de détermination de la question de savoir si un mandant authentifié est d’accéder aux ressources demandées. Vous devez également déterminer si chiffrer le message à l'aide de SSL.  
  
## <a name="authenticating-client-requests"></a>Authentification des demandes du client  
WCF Data Services ne met pas en œuvre son propre authentification, mais s’appuie plutôt sur les dispositions d’authentification de l’hébergeur de services de données. Cela signifie que le service suppose que toute demande qu’il reçoit a déjà été authentifiée par l’hôte du réseau et que l’hôte a correctement identifié le principe de la demande de manière appropriée via les interfaces fournies par WCF Data Services. Ces options et approches d’authentification sont détaillées dans la [série multiparte OData et Authentification.](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Options d'authentification pour un service de données WCF  
 Le tableau suivant répertorie une partie des mécanismes d'authentification qui s'offrent à vous pour authentifier les demandes à un service de données WCF.  
  
|Options d’authentification|Description|  
|----------------------------|-----------------|  
|Authentification anonyme|Lorsque l'authentification anonyme HTTP est activée, n'importe quel principal est en mesure de se connecter au service de données. Les informations d'identification ne sont pas requises pour un accès anonyme. Utilisez cette option uniquement lorsque vous souhaitez autoriser tout le monde à accéder au service de données.|  
|Authentification de base et Digest|Les informations d'identification comprenant un nom d'utilisateur et un mot de passe sont requises pour l'authentification. Prend en charge l'authentification des clients non Windows. **Note de sécurité:**  Les informations d’authentification de base (nom d’utilisateur et mot de passe) sont envoyées en clair et peuvent être interceptées. L’authentification Digest envoie un hachage en fonction des informations d’identification fournies, les sécurisant davantage par rapport à une authentification basique. Ces deux authentifications sont vulnérables aux attaques de l'intercepteur (« Man-in-the-Middle »). Lorsque vous utilisez ces méthodes d'authentification, nous vous conseillons d'utiliser une communication chiffrée entre le client et le service de données à l'aide de SSL (Secure Sockets Layer). <br /><br /> Microsoft Internet Information Services (IIS) fournit une implémentation de base et de digest authentification des demandes HTTP dans une application ASP.NET. L'implémentation de ce fournisseur d'authentification Windows permet à une application cliente .NET Framework de fournir les informations d'identification dans l'en-tête HTTP de la demande au service de données pour négocier de façon transparente l'authentification d'un utilisateur Windows. Pour plus d’informations, voir [Digest Authentication Technical Reference](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10)).<br /><br /> Lorsque vous souhaitez que votre service de données utilise l’authentification de base basée sur un service d’authentification personnalisé et non sur des informations d’identification Windows, vous devez implémenter un module HTTP personnalisé ADP.NET pour l’authentification.<br /><br /> Pour un exemple de la façon d’utiliser un système d’authentification de base personnalisé avec WCF Data Services, voir le blog [OData and Authentication - Partie 6 - Authentification de base personnalisée](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Authentification Windows|Les informations d'identification basées sur Windows sont échangées à l'aide de NTLM ou Kerberos. Ce mécanisme est plus sécurisé que l’authentification de base ou Digest, mais requiert que le client soit une application basée sur Windows. IIS fournit également une implémentation de l’authentification Windows pour les demandes HTTP dans une application ASP.NET. Pour plus d’informations, voir [ASP.NET Forms Authentication Aperçu](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Pour un exemple de la façon d’utiliser l’authentification Windows avec WCF Data Services, voir le blog [OData et Authentication - Partie 2 - Authentification windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|ASP.NET forme l’authentification|L'authentification par formulaire vous permet d'authentifier des utilisateurs à l'aide de votre propre code puis de conserver un jeton d'authentification dans un cookie ou dans l'URL de la page. Vous authentifiez le nom d'utilisateur et le mot de passe de vos utilisateurs en créant un formulaire de connexion. Les demandes non authentifiées sont redirigées vers une page de connexion, où l'utilisateur fournit des informations d'identification et envoie le formulaire. Si l'application authentifie la demande, le système délivre un ticket qui contient une clé pour rétablir l'identité pour les demandes suivantes. Pour plus d’informations, voir [Forms Authentication Provider](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Note de sécurité:**  Par défaut, le cookie qui contient le billet d’authentification des formulaires n’est pas sécurisé lorsque vous utilisez des formulaires d’authentification dans une application Web ASP.NET. Vous devriez considérer l'utilisation de SSL pour protéger le ticket d'authentification et les informations d'identification de la connexion initiale. <br /><br /> Pour un exemple de la façon d’utiliser l’authentification des formulaires avec WCF Data Services, voir le billet de blog [OData et Authentification - Partie 7 - Forms Authentification](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Authentification basée sur les revendications|Dans l’authentification fondée sur les revendications, le service de données s’appuie sur un service de fournisseur d’identité « tiers » de confiance pour authentifier l’utilisateur. Le fournisseur d'identité authentifie positivement l'utilisateur qui demande l'accès aux ressources du service de données et émet un jeton qui accorde l'accès aux ressources demandées. Ce jeton est ensuite présenté au service de données, qui accorde ensuite l'accès à l'utilisateur en fonction de la relation d'approbation avec le service d'identité qui émet le jeton d'accès.<br /><br /> L'avantage d'utiliser un fournisseur d'authentification basée sur les revendications est que celles-ci peuvent être utilisées pour authentifier différents types de clients entre plusieurs domaines approuvés. En utilisant un tel fournisseur tiers, un service de données peut décharger les revendications de gestion et authentification des utilisateurs. OAuth 2.0 est un protocole d'authentification basée sur les revendications pris en charge par le contrôle d'accès Microsoft Azure AppFabric pour l'autorisation fédérée en tant que service. Ce protocole prend en charge les services REST. Pour un exemple de la façon d’utiliser OAuth 2.0 avec WCF Data Services, voir le blog [OData and Authentication - Partie 8 - OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>
### <a name="authentication-in-the-client-library"></a>Authentification dans la bibliothèque cliente  
 Par défaut, la bibliothèque client de WCF Data Services ne fournit pas d’informations d’identification lors de la demande d’un service OData. Lorsque les informations de connexions sont demandées par le service de données pour authentifier un utilisateur, elles peuvent être fournies par un <xref:System.Net.NetworkCredential> accédé depuis la propriété <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> du <xref:System.Data.Services.Client.DataServiceContext>, comme dans l'exemple suivant :  
  
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
  
 Pour plus d’informations, voir [Comment : Spécifier les informations d’identification des clients pour une demande de service de données](specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Lorsque le service de données demande des informations de connexion qui ne peuvent pas être spécifiées à l'aide d'un objet <xref:System.Net.NetworkCredential>, comme un jeton ou un cookie basé sur des revendications, vous devez définir manuellement les en-têtes, généralement les en-têtes `Authorization` et `Cookie`, dans la demande HTTP. Pour plus d’informations sur ce genre de scénario d’authentification, voir le blog [OData et Authentication - Partie 3 - ClientSide Crochets](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Pour un exemple de la façon de définir les en-têtes HTTP dans un message de demande, voir [Comment : Définir les en-têtes dans la demande de client](how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Emprunt d'identité  
 Généralement, le service de données accède aux ressources demandées, comme les fichiers sur le serveur ou la base de données, à l'aide des informations d'authentification du processus de travail qui héberge actuellement le service de données. Lors de l’utilisation de l’usurpation d’identité, ASP.NET applications peuvent s’exécuter avec l’identité Windows (compte utilisateur) de l’utilisateur effectuant la demande. L'emprunt d'identité est utilisé couramment dans les applications qui reposent sur IIS pour authentifier l'utilisateur et les informations d'identification de ce principal sont utilisées pour accéder aux ressources demandées. Pour plus d’informations, voir [ASP.NET’usurpation d’identité](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Configuration de l'autorisation du service de données  
 L'autorisation est le fait d'autoriser l'accès aux ressources d'une application à un principal ou à un processus identifié sur la base d'une authentification précédemment réussie. En règle générale, vous ne devriez accorder aux utilisateurs du service de données que des droits suffisants pour exécuter les opérations requises par les applications clientes.  
  
### <a name="restrict-access-to-data-service-resources"></a>Restriction d'accès aux ressources du service de données  
 Par défaut, WCF Data Services vous permet d’accorder un accès commun à la lecture et à l’écriture des ressources de services de données (ensemble d’entités et opérations de service) à tout utilisateur capable d’accéder au service de données. Les règles qui définissent l'accès en lecture et écriture peuvent être définies séparément pour chaque jeu d'entité exposé par le service de données, tout comme toute opération de service. Nous vous recommandons de limiter l'accès en lecture et écriture aux seules ressources requises par l'application cliente. Pour plus d’informations, voir [exigences minimales en matière d’accès aux ressources](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implémentation d'intercepteurs basés sur le rôle  
 Les intercepteurs vous permettent d'intercepter les demandes adressées aux ressources du service de données avant qu'elles ne soient traitées par le service de données. Pour plus d’informations, voir [Interceptors](interceptors-wcf-data-services.md). Les intercepteurs vous permettent de prendre des décisions d'autorisation en fonction de l'utilisateur authentifié qui effectue la demande. Pour un exemple de la façon de restreindre l’accès aux ressources de service de données en fonction d’une identité d’utilisateur authentifiée, voir [Comment : Intercepter les messages de service de données](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Restriction d'accès aux ressources d'un magasin de données persistantes ou aux ressources locales  
 Les comptes que vous utilisez pour accéder au magasin de données persistantes doivent disposer uniquement des autorisations minimales pour prendre en charge les spécifications du service de données dans la base de données ou le système de fichiers. Lorsque vous utilisez une authentification anonyme, il s'agit du compte utilisé pour exécuter l'application d'hébergement. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md). Lorsque vous utilisez l'emprunt d'identité, les utilisateurs authentifiés doivent être autorisés à accéder à ces ressources, généralement dans le cadre d'un groupe Windows.  
  
## <a name="other-security-considerations"></a>Autres considérations à propos de la sécurité  
  
### <a name="secure-the-data-in-the-payload"></a>Sécurisation des données dans la charge utile  
OData est basé sur le protocole HTTP. Dans un message HTTP, l'en-tête peut contenir des informations d'identification utiles concernant l'utilisateur, selon l'authentification implémentée par le service de données. Le corps du message peut également contenir des données utiles sur le client, qu'il convient de protéger. Dans ces deux cas, nous vous recommandons d'utiliser SSL pour protéger ces informations lors de la transmission.  
  
### <a name="ignored-message-headers-and-cookies"></a>En-têtes et cookies de message ignorés  
 Les en-têtes des demandes HTTP autres que celles qui déclarent des types de contenu et des emplacements de ressources, sont ignorés et ne sont jamais définis par le service de données.  
  
 Les cookies peuvent être utilisés dans le cadre d’un système d’authentification, comme avec ASP.NET Forms Authentication. Cependant, tous les cookies HTTP définis sur une demande entrante sont ignorés par WCF DataServices. L’hôte d’un service de données peut traiter le cookie, mais l’exécution WCF Data Services n’analyse jamais ou ne renvoie jamais les cookies. La bibliothèque clientE de WCF Data Services ne traite pas non plus les cookies envoyés dans la réponse.  
  
### <a name="custom-hosting-requirements"></a>Conditions d’hébergement personnalisé  
 Par défaut, WCF Data Services est créé en tant qu’application ASP.NET hébergée dans IIS. Cela permet au service de données de tirer parti des comportements de sécurité de cette plateforme. Vous pouvez définir les services de données WCF hébergés par un hôte personnalisé. Pour plus d’informations, voir [Hébergement du service de données](hosting-the-data-service-wcf-data-services.md). Les composants et la plateforme qui hébergent un service de données doivent assurer les comportements de sécurité suivants pour empêcher des attaques sur le service de données :  
  
- Limiter la longueur de l'URI accepté dans une demande de service de données pour toutes les opérations possibles.  
  
- Limiter la taille des messages HTTP entrants et sortants.  
  
- Limiter le nombre total de demandes sortantes à tout moment.  
  
- Limitez la taille des en-têtes HTTP et leurs valeurs, et fournissez aux services de données WCF l’accès aux données d’en-tête.  
  
- Détecter et répertorier les attaques connues, telles que TCP SYN et les attaques de relecture de message.  
  
### <a name="values-are-not-further-encoded"></a>Les valeurs ne sont pas encodées ultérieurement.  
 Les valeurs des propriétés envoyées au service de données ne sont pas codées par l’exécution des services de données WCF. Par exemple, lorsqu’une propriété de chaîne d’une entité inclut un contenu HTML formaté, les étiquettes ne sont pas encodées en HTML par le service de données. De même, le service de données n'encode pas ultérieurement les valeurs de propriété dans la réponse. La bibliothèque du client n'exécute aucun encodage supplémentaire.  
  
### <a name="considerations-for-client-applications"></a>Considérations pour les applications clientes  
 Les considérations de sécurité suivantes s’appliquent aux applications qui utilisent le client WCF Data Services pour accéder aux services OData :  
  
- La bibliothèque du client suppose que les protocoles utilisés pour accéder au service de données fournissent un niveau de sécurité suffisant.  
  
- La bibliothèque du client utilise toutes les valeurs par défaut des délais d'attente et des options d'analyse des piles de transport fournies par la plateforme sous-jacente.  
  
- La bibliothèque du client ne lit aucun paramètre des fichiers de configuration de l'application.  
  
- La bibliothèque du client n'implémente aucun mécanisme d'accès entre domaines. En revanche, elle utilise les mécanismes fournis par la pile HTTP sous-jacente.  
  
- La bibliothèque du client ne dispose d'aucun élément d'interface utilisateur et elle ne tente jamais d'afficher ou de restituer les données qu'elle reçoit ou envoie.  
  
- Nous recommandons que les applications clientes valident toujours les entrées utilisateur et les données acceptées provenant de services non approuvés.  
  
## <a name="see-also"></a>Voir aussi

- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
