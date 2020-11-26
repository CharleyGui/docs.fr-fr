---
title: Authentification Windows intégrée avec protection étendue
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: 74f421131da0e5b11fd676ff23229f5ff6ec7eca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241621"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Authentification Windows intégrée avec protection étendue

Certaines améliorations apportées changent la manière dont l’authentification Windows intégrée est gérée par les classes <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream> et les classes associées dans l’espace de noms <xref:System.Net> et les espaces de noms associés. La prise en charge de la protection étendue a été ajoutée pour renforcer la sécurité.  
  
 Ces modifications peuvent affecter les applications qui utilisent ces classes pour effectuer des demandes web et recevoir des réponses quand l’authentification Windows intégrée est utilisée. Elles peuvent aussi avoir un impact sur les serveurs web et les applications clientes configurés pour utiliser l’authentification Windows intégrée.  
  
 Ces modifications peuvent affecter les applications qui utilisent ces classes pour effectuer d’autres types de demandes et recevoir des réponses quand l’authentification Windows intégrée est utilisée.  
  
 Les modifications pour la prise en charge de la protection étendue concernent uniquement les applications s’exécutant sur Windows 7 et Windows Server 2008 R2. Les fonctionnalités de protection étendue ne sont pas disponibles dans les versions antérieures de Windows.  
  
## <a name="overview"></a>Vue d'ensemble  

 La conception de l’authentification Windows intégrée permet à certaines réponses aux demandes d’informations d’identification d’être universelles, ce qui signifie qu’elles peuvent être réutilisées ou transférées. Les réponses aux demandes doivent être construites au minimum avec des informations spécifiques à la cible et, de préférence, avec également des informations spécifiques au canal. Les services peuvent alors fournir une protection étendue pour garantir que les réponses aux demandes d’informations d’identification contiennent des informations propres aux services, telles qu’un nom de principal du service (SPN). Grâce à la présence de ces informations dans les échanges d’informations d’identification, les services assurent une meilleure protection contre l’utilisation malveillante de certaines réponses aux demandes d’informations d’identification qui ont été utilisées de manière incorrecte.  
  
 La conception de la protection étendue est une amélioration apportée aux protocoles d’authentification qui vise à atténuer les risques d’attaques par relais d’authentification. Elle repose sur le concept d’informations de liaison de service et de canal.  
  
 Les objectifs généraux sont les suivants :  
  
1. Si le client est mis à jour pour prendre en charge la protection étendue, les applications doivent fournir des informations de liaison de service et de canal à tous les protocoles d’authentification pris en charge. Les informations de liaison de canal peuvent uniquement être fournies s’il y a un canal TLS auquel effectuer la liaison. Les informations de liaison de service doivent toujours être fournies.  
  
2. S’ils sont configurés de manière appropriée, les serveurs mis à jour vérifient les informations de liaison de service et de canal contenues dans le jeton d’authentification client et rejettent la tentative d’authentification si les liaisons de canal ne correspondent pas. Selon le scénario de déploiement, les serveurs vérifient la liaison de canal ou la liaison de service, ou les deux liaisons.  
  
3. Les serveurs mis à jour ont la possibilité d’accepter ou de rejeter les demandes de client de bas niveau qui ne contiennent pas les informations de liaison de canal basées sur la stratégie.  
  
 Les informations utilisées par la protection étendue sont constituées d’au moins un des deux éléments suivants :  
  
1. Un jeton de liaison de canal.  
  
2. Des informations de liaison de service sous la forme d’un nom de principal du service (SPN).  
  
 Les informations de liaison de service sont une indication de l’intention d’un client de s’authentifier auprès d’un point de terminaison de service particulier. Elles sont transmises du client au serveur avec les propriétés suivantes :  
  
- La valeur du SPN doit être fournie au serveur d’authentification client au format texte en clair.  
  
- La valeur du SPN est publique.  
  
- Le SPN doit être protégé par chiffrement pendant son transfert pour empêcher l’insertion, la suppression ou la modification de sa valeur par une attaque de l’intercepteur.  
  
 Un jeton de liaison de canal est une propriété du canal sécurisé externe (par exemple, TLS) qui permet de lier ce canal à une conversation sur un canal interne authentifié par le client. Le jeton de liaison de canal doit avoir les propriétés suivantes (qui sont également définies dans la norme RFC 5056 publiée par l’IETF) :  
  
- Quand un canal externe existe, la valeur du jeton de liaison de canal doit être une propriété qui identifie le canal externe ou le point de terminaison de serveur, arrivés indépendamment côté client et côté serveur d’une conversation.  
  
- La valeur du jeton de liaison de canal envoyé par le client ne doit pas être une valeur falsifiable par un attaquant.  
  
- La confidentialité de la valeur du jeton de liaison de canal n’est pas garantie. Toutefois, cela ne signifie pas que la valeur de la liaison de service ou que les informations de liaison de canal seront toujours exposées à d’autres parties que le serveur effectuant l’authentification, car elles sont parfois chiffrées par le protocole de transport du jeton de liaison de canal.  
  
- L’intégrité du jeton de liaison de canal doit être protégée par chiffrement pendant le transfert du jeton pour empêcher l’insertion, la suppression ou la modification de sa valeur par un attaquant.  
  
 La liaison de canal s’effectue par le client qui transfère le SPN et le jeton de liaison de canal au serveur de manière infalsifiable. Le serveur valide les informations de liaison de canal conformément à sa stratégie et rejette les tentatives d’authentification pour lesquelles il ne pense pas être la cible prévue. Les deux canaux sont ainsi liés par chiffrement.  
  
 Pour garantir la compatibilité avec les clients et applications existants, un serveur peut être configuré pour autoriser les tentatives d’authentification effectuées par des clients qui ne prennent pas encore en charge la protection étendue. Cette configuration est « partiellement sécurisée », au lieu d’être « entièrement sécurisée ».  
  
 Plusieurs composants des espaces de noms <xref:System.Net> et <xref:System.Net.Security> effectuent l’authentification Windows intégrée pour le compte d’une application appelante. Cette section décrit les modifications apportées aux composants System.Net pour ajouter une protection étendue lors de l’utilisation de l’authentification Windows intégrée.  
  
 La protection étendue est prise en charge sur Windows 7. Un mécanisme intégré permet à une application de déterminer si le système d’exploitation prend en charge la protection étendue.  
  
## <a name="changes-to-support-extended-protection"></a>Modifications pour prendre en charge la protection étendue  

 Selon le protocole d’authentification choisi, le processus d’authentification utilisé avec l’authentification Windows intégrée inclut souvent une réponse émise par l’ordinateur de destination et renvoyée à l’ordinateur client. La protection étendue ajoute de nouvelles fonctionnalités à ce processus d’authentification.  
  
 L’espace de noms <xref:System.Security.Authentication.ExtendedProtection> fournit la prise en charge de l’authentification avec protection étendue pour les applications. Dans cet espace de noms, la classe <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> représente une liaison de canal. Dans cet espace de noms, la classe <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> représente la stratégie de protection étendue utilisée par le serveur pour valider les connexions client entrantes. D’autres membres de classe sont utilisés avec la protection étendue.  
  
 Pour les applications serveur, ces classes comportent les éléments suivants :  
  
 Une classe <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> qui a les éléments suivants :  
  
- Une propriété <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> qui indique si le système d’exploitation prend en charge l’authentification Windows intégrée avec protection étendue.  
  
- Une valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> qui indique quand la stratégie de protection étendue doit être appliquée.  
  
- Une valeur <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> qui spécifie le scénario de déploiement. Cette valeur détermine la façon dont la protection étendue est vérifiée.  
  
- Un élément <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> facultatif qui contient la liste des noms de principal de service personnalisés auxquels est comparé le nom de principal du service fourni par le client comme cible de l’authentification.  
  
- Un élément <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> facultatif qui contient une liaison de canal personnalisée à utiliser pour la validation. Ce scénario n’est pas courant.  
  
 L’espace de noms <xref:System.Security.Authentication.ExtendedProtection.Configuration> fournit la prise en charge de la configuration de l’authentification avec protection étendue pour les applications.  
  
 Plusieurs modifications ont été apportées aux fonctionnalités pour permettre la prise en charge de la protection étendue dans l’espace de noms <xref:System.Net> existant. Elles incluent notamment les suivantes :  
  
- Ajout d’une nouvelle classe <xref:System.Net.TransportContext> à l’espace de noms <xref:System.Net> qui représente un contexte de transport.  
  
- Ajout des nouvelles méthodes de surcharge <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> et <xref:System.Net.HttpWebRequest.GetRequestStream%2A> dans la classe <xref:System.Net.HttpWebRequest> qui permettent la récupération du <xref:System.Net.TransportContext> pour prendre en charge la protection étendue dans les applications clientes.  
  
- Ajouts aux classes <xref:System.Net.HttpListener> et <xref:System.Net.HttpListenerRequest> pour prendre en charge les applications serveur.  
  
 Pour prendre en charge la protection étendue dans les applications clientes SMTP, une fonctionnalité a été modifiée dans l’espace de noms <xref:System.Net.Mail> :  
  
- Une propriété <xref:System.Net.Mail.SmtpClient.TargetName%2A> dans la classe <xref:System.Net.Mail.SmtpClient> qui représente le nom de principal du service à utiliser lors de l’authentification avec protection étendue dans les applications clientes SMTP.  
  
 Plusieurs modifications ont été apportées aux fonctionnalités pour permettre la prise en charge de la protection étendue dans l’espace de noms <xref:System.Net.Security> existant. Elles incluent notamment les suivantes :  
  
- Ajout des nouvelles méthodes de surcharge <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> et <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> dans la classe <xref:System.Net.Security.NegotiateStream> qui permettent le passage d’un jeton de liaison de canal pour prendre en charge la protection étendue dans les applications clientes.  
  
- Ajout des nouvelles méthodes de surcharge <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> et <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> dans la classe <xref:System.Net.Security.NegotiateStream> qui permettent le passage d’un <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> pour prendre en charge la protection étendue dans les applications serveur.  
  
- Ajout d’une nouvelle propriété <xref:System.Net.Security.SslStream.TransportContext%2A> dans la classe <xref:System.Net.Security.SslStream> pour prendre en charge la protection étendue dans les applications clientes et serveur.  
  
 Une nouvelle propriété <xref:System.Net.Configuration.SmtpNetworkElement> a été ajoutée dans l’espace de noms <xref:System.Net.Security> pour prendre en charge la configuration de la protection étendue pour les clients SMTP.  
  
## <a name="extended-protection-for-client-applications"></a>Protection étendue pour les applications clientes  

 La prise en charge de la protection étendue est automatique pour la plupart des applications clientes. Les classes <xref:System.Net.HttpWebRequest> et <xref:System.Net.Mail.SmtpClient> prennent en charge la protection étendue quand la version sous-jacente de Windows la prend en charge. Une instance <xref:System.Net.HttpWebRequest> envoie un nom de principal du service construit à partir de l’<xref:System.Uri>. Par défaut, une instance <xref:System.Net.Mail.SmtpClient> envoie un nom de principal du service construit à partir du nom d’hôte du serveur de messagerie SMTP.  
  
 Pour l’authentification personnalisée, les applications clientes peuvent utiliser les méthodes <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> ou <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> de la classe <xref:System.Net.HttpWebRequest> qui permettent de récupérer le <xref:System.Net.TransportContext> et le jeton de liaison de canal à l’aide de la méthode <xref:System.Net.TransportContext.GetChannelBinding%2A>.  
  
 Le nom de principal du service à utiliser pour l’authentification Windows intégrée et envoyé par une instance <xref:System.Net.HttpWebRequest> à un service donné peut être substitué en définissant la propriété <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A>.  
  
 La propriété <xref:System.Net.Mail.SmtpClient.TargetName%2A> permet de définir un nom principal de service personnalisé à utiliser pour l’authentification Windows intégrée de la connexion SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Protection étendue pour les applications serveur  

 <xref:System.Net.HttpListener> fournit automatiquement des mécanismes de validation des liaisons de service pendant l’authentification HTTP.  
  
 Le scénario le plus sécurisé consiste à activer la protection étendue pour les `HTTPS://` préfixes. Dans ce cas, définissez <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> à <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>, où <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> a la valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> ou <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> et où <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> a la valeur <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected>. La valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> met <xref:System.Net.HttpListener> en mode partiellement sécurisé, tandis que <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> correspond au mode entièrement sécurisé.  
  
 Dans cette configuration, quand une demande est envoyée au serveur via un canal sécurisé externe, celui-ci est interrogé pour fournir une liaison de canal. Cette liaison de canal est passée aux appels d’authentification SSPI, qui vérifient ensuite la correspondance avec la liaison de canal dans l’objet blob d’authentification. Il y a trois cas possibles :  
  
1. Le système d’exploitation sous-jacent du serveur ne prend pas en charge la protection étendue. La demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
2. L’appel SSPI échoue. Cela signifie que le client a spécifié une liaison de canal qui ne correspond pas à la valeur attendue récupérée à partir du canal externe, ou que le client n’a pas pu fournir de liaison de canal alors que la stratégie de protection étendue sur le serveur est configurée avec le paramètre <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. Dans les deux cas, la demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
3. Le client spécifie la liaison de canal appropriée ou bien il est autorisé à se connecter sans spécifier de liaison de canal du fait que la stratégie de protection étendue sur le serveur est configurée avec le paramètre <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported>. La demande est retournée à l’application pour être traitée. Aucune vérification de nom de service n’est effectuée automatiquement. Une application peut choisir d’effectuer elle-même la validation des noms de service à l’aide de la propriété <xref:System.Net.HttpListenerRequest.ServiceName%2A>, mais dans ce cas, cela est inutile.  
  
 Si une application effectue elle-même des appels SSPI dans le cadre d’une authentification basée sur les objets blob échangés dans le corps d’une requête HTTP et qu’elle souhaite prendre en charge la liaison de canal, elle doit récupérer la liaison de canal attendue du canal sécurisé externe en utilisant <xref:System.Net.HttpListener> pour la passer ensuite à la fonction [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) Win32. Pour cela, utilisez la propriété <xref:System.Net.HttpListenerRequest.TransportContext%2A> et appelez la méthode <xref:System.Net.TransportContext.GetChannelBinding%2A> qui permet de récupérer le jeton de liaison de canal. Seules les liaisons de point de terminaison sont prises en charge. Si une autre liaison que la liaison <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> est spécifiée, une <xref:System.NotSupportedException> est levée. Si le système d’exploitation sous-jacent prend en charge la liaison de canal, la <xref:System.Net.TransportContext.GetChannelBinding%2A> méthode retourne un <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> wrapper d’un pointeur vers une liaison de canal pouvant être passée à la fonction [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) en tant que membre pvBuffer d’une structure SecBuffer passée dans le `pInput` paramètre. La propriété <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> contient la longueur, en octets, de la liaison de canal. Si le système d’exploitation sous-jacent ne prend pas en charge les liaisons de canal, la fonction retourne la valeur `null`.  
  
 Un autre scénario possible consiste à activer la protection étendue pour les `HTTP://` préfixes lorsque les proxies ne sont pas utilisés. Dans ce cas, définissez <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> à <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>, où <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> a la valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> ou <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> et où <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> a la valeur <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected>. La valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> met <xref:System.Net.HttpListener> en mode partiellement sécurisé, tandis que <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> correspond au mode entièrement sécurisé.  
  
 Une liste par défaut de noms de service autorisés est créée à partir des préfixes qui ont été inscrits avec <xref:System.Net.HttpListener>. Cette liste par défaut peut être examinée à l’aide de la propriété <xref:System.Net.HttpListener.DefaultServiceNames%2A>. Si cette liste n’est pas complète, une application peut spécifier une collection de noms de service personnalisés dans le constructeur de la classe <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>. Cette collection est alors utilisée à la place de la liste de noms de service par défaut.  
  
 Dans cette configuration, quand une demande est faite au serveur sans canal sécurisé externe, l’authentification s’effectue normalement, sans vérification de la liaison de canal. Si l’authentification réussit, le contexte est interrogé pour retourner le nom de service que le client a fourni et validé par rapport à la liste des noms de service autorisés. Il y a quatre cas possibles :  
  
1. Le système d’exploitation sous-jacent du serveur ne prend pas en charge la protection étendue. La demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
2. Le système d’exploitation sous-jacent du client ne prend pas en charge la protection étendue. Dans la configuration <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported>, la tentative d’authentification réussit et la demande est retournée à l’application. Dans la configuration <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, la tentative d’authentification échoue. La demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
3. Le système d’exploitation sous-jacent du client prend en charge la protection étendue, mais l’application n’a pas spécifié de liaison de service. La demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
4. Le client a spécifié une liaison de service. La liaison de service est comparée à la liste des liaisons de service autorisées. Si elle correspond à une liaison de la liste, la demande est retournée à l’application. Sinon, la demande n’est pas exposée à l’application, et une réponse d’autorisation refusée (401) est automatiquement retournée au client. Un message est consigné dans la source de la trace <xref:System.Net.HttpListener> indiquant la raison de l’échec.  
  
 Si cette approche simple basée sur une liste de noms de service autorisés est inappropriée, une application peut effectuer elle-même la validation des noms de service en interrogeant la propriété <xref:System.Net.HttpListenerRequest.ServiceName%2A>. Dans les cas 1 et 2 ci-dessus, la propriété retourne `null`. Dans le cas 3, elle retourne une chaîne vide. Dans le cas 4, elle retourne le nom de service spécifié par le client.  
  
 Ces fonctionnalités de protection étendue peuvent également être utilisées par les applications serveur pour l’authentification avec d’autres types de demandes et quand des proxies approuvés sont utilisés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
