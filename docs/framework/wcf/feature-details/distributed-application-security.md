---
title: Sécurité des applications distribuées
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
ms.openlocfilehash: 3cae20cfe8d52497646ca173740533a22326c8f8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599143"
---
# <a name="distributed-application-security"></a>Sécurité des applications distribuées
La sécurité Windows Communication Foundation (WCF) est divisée en trois zones fonctionnelles principales : la sécurité de transfert, le contrôle d’accès et l’audit. La sécurité de transfert fournit l'intégrité, la confidentialité et l'authentification. La sécurité de transfert est fournie par l'un des éléments suivants : sécurité de transport, sécurité de message ou `TransportWithMessageCredential`.  
  
 Pour obtenir une vue d’ensemble de la sécurité des messages WCF, consultez [vue d’ensemble](security-overview.md)de la sécurité. Pour plus d’informations sur les deux autres parties de la sécurité WCF, consultez [autorisations](authorization-in-wcf.md) et [audit](auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Scénarios de sécurité de transfert  
 Les scénarios courants qui utilisent la sécurité de transfert WCF sont les suivants :  
  
- Transfert sécurisé à l'aide de Windows. Un client et un service WCF sont déployés dans un domaine Windows (ou une forêt Windows). Les messages contenant des données personnelles, les exigences incluent donc l’authentification mutuelle du client et du service, l’intégrité et la confidentialité des messages. En outre, la preuve est requise qu'une transaction spécifique s'est produite ; à titre d'exemple, le récepteur du message doit enregistrer les informations de signature.  
  
- Transfert sécurisé à l'aide de `UserName` et HTTPS. Un client et un service WCF doivent être développés pour fonctionner sur Internet. Les informations d'identification du client permettent d'effectuer l'authentification par rapport à une base de données de paires nom d'utilisateur/mot de passe. Le service est déployé à une adresse HTTPS à l'aide d'un certificat SSL (Secure Sockets Layer) approuvé. Les messages transitant sur Internet, le client et le service doivent donc être mutuellement authentifiés, et la confidentialité et l'intégrité des messages doivent être conservées pendant le transfert.  
  
- Transfert sécurisé à l'aide de certificats. Un client et un service WCF doivent être développés pour fonctionner sur l’Internet public. Le client et le service ont tous deux des certificats qui permettent de sécuriser les messages. Le client et le service utilisent Internet pour communiquer l’un avec l’autre et exécuter des transactions à forte valeur qui requièrent l’intégrité des messages, la confidentialité et l’authentification mutuelle.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Intégrité, confidentialité et authentification  
 Ces trois fonctions (intégrité, confidentialité et authentification) forment ensemble la « sécurité de transfert ». La sécurité de transfert fournit les fonctions permettant de limiter les menaces auxquelles est exposée une application distribuée. Le tableau suivant décrit brièvement les trois fonctions qui composent la sécurité de transfert.  
  
|Fonction|Description|  
|--------------|-----------------|  
|Intégrité|L' *intégrité* est l’assurance que les données sont complètes et précises, en particulier après avoir parcouru un point vers un autre, et éventuellement lues par de nombreux acteurs. L'intégrité doit être maintenue afin d'empêcher toute falsification à l'aide des données, et elle est généralement assurée par la signature numérique d'un message.|  
|Confidentialité|La *confidentialité* est l’assurance qu’un message n’a pas été lu par une personne autre que le lecteur prévu. Par exemple, un numéro de carte de crédit doit rester confidentiel lorsqu'il est envoyé sur Internet. La confidentialité est souvent fournie par le chiffrement des données à l'aide d'un schéma de clé publique/clé privée.|  
|Authentification|L' *authentification* est la vérification d’une identité revendiquée. Par exemple, lors de l'utilisation d'un compte bancaire, il est impératif que seul le propriétaire réel de ce compte soit autorisé à retirer des fonds. L'authentification peut être fournie par divers moyens. L'une des méthodes fréquemment utilisées est le système nom d'utilisateur/mot de passe. Une autre consiste à utiliser un certificat X.509 fourni par un tiers.|  
  
## <a name="security-modes"></a>Modes de sécurité  
 WCF offre plusieurs modes de sécurité de transfert, décrits dans le tableau suivant.  
  
|Mode|Description|  
|----------|-----------------|  
|None|Aucune sécurité n'est fournie au niveau de la couche de transport ou de la couche de message. Aucune des liaisons prédéfinies n’utilise ce mode par défaut, à l’exception de l' [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) élément ou, lors de l’utilisation de code, la <xref:System.ServiceModel.BasicHttpBinding> classe.|  
|Transport|Utilise un transport sécurisé tel que HTTPS pour l'intégrité, la confidentialité et l'authentification mutuelle.|  
|Message|Utilise la sécurité de message SOAP pour l'intégrité, la confidentialité et l'authentification mutuelle. Les messages SOAP sont sécurisés conformément aux standards WS-Security.|  
|Mode mixte|Utilise la sécurité de transport pour l'intégrité, la confidentialité et l'authentification du serveur. Utilise la sécurité de message (WS-Security et autres standards) pour l'authentification du client.<br /><br /> (Cette énumération pour ce mode est `TransportWithMessageCredential`.)|  
|Les deux|Effectue la protection et l'authentification aux deux niveaux. Ce mode est disponible uniquement dans l' [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) élément.|  
  
## <a name="credentials-and-transfer-security"></a>Informations d'identification et sécurité de transfert  
 Les *informations d’identification* sont des données qui sont présentées pour établir une identité ou des fonctionnalités demandées. La présentation d'informations d'identification implique la présentation à la fois des données et la preuve de la propriété de ces données. WCF prend en charge divers types d’informations d’identification au niveau du transport et de la sécurité des messages. Vous pouvez spécifier un type d’informations d’identification pour une liaison WCF.  
  
 Dans de nombreux pays ou régions, le permis de conduire est un exemple d'information d'identification. Un permis contient des données qui représentent l'identité d'une personne et des fonctions. Elle contient la preuve de propriété sous la forme de la photographie du propriétaire. Le permis est délivré par une autorité approuvée, généralement un service public chargé de cette fonction. Le permis est scellé et peut contenir un hologramme qui indique qu'il n'a pas été falsifié.  
  
 Par exemple, considérez deux types d’informations d’identification pris en charge dans WCF : le nom d’utilisateur et les informations d’identification de certificat (X. 509).  
  
 Concernant les informations d'identification de nom d'utilisateur, le nom d'utilisateur représente l'identité déclarée et le mot de passe présente la preuve de la propriété. L'autorité approuvée dans ce cas est le système qui valide le nom d'utilisateur et le mot de passe.  
  
 Dans l'information d'identification de certificat, le nom du sujet, le nom de substitution du sujet ou des champs spécifiques inclus dans le certificat peuvent être utilisés pour représenter l'identité déclarée et/ou les fonctions. La preuve de la propriété des données dans l'information d'identification est établie en utilisant la clé privée associée pour générer une signature.  
  
 Pour plus d’informations sur la programmation de la sécurité de transfert et la spécification des informations d’identification, consultez [liaisons et sécurité](bindings-and-security.md) et [comportements de sécurité](security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Types d'informations d'identification du client de transport  
 Le tableau suivant présente les valeurs possibles utilisées lors de la création d'une application utilisant la sécurité de transfert. Vous pouvez utiliser ces valeurs dans le code ou les paramètres de liaison.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|None|Spécifie que le client n'a pas besoin de présenter d'informations d'identification. Cela se traduit en un client anonyme.|  
|De base|Spécifie l'authentification de base. Pour plus d’informations, consultez RFC2617, «[authentification http : authentification de base et Digest](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)».|  
|Digest|Spécifie l’authentification Digest. Pour plus d’informations, consultez RFC2617, «[authentification http : authentification de base et Digest](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)».|  
|Ntlm|Spécifie l'authentification Windows à l'aide de la négociation SSPI sur un domaine Windows.<br /><br /> La négociation SSPI entraîne l'utilisation du protocole Kerberos ou NTLM (NT LanMan).|  
|Windows|Spécifie l'authentification Windows à l'aide de SSPI sur un domaine Windows. SSPI sélectionne le protocole Kerberos ou NTLM comme service d'authentification.<br /><br /> SSPI tente d'abord d'utiliser le protocole Kerberos ; en cas d'échec, il utilise NTLM.|  
|Certificat|Exécute l'authentification du client à l'aide d'un certificat, en général X.509.|  
  
### <a name="message-client-credential-types"></a>Types d'informations d'identification du client de message  
 Le tableau suivant présente les valeurs possibles utilisées lors de la création d'une application utilisant la sécurité de message. Vous pouvez utiliser ces valeurs dans le code ou les paramètres de liaison.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|None|Autorise le service à interagir avec des clients anonymes.|  
|Windows|Autorise les échanges de messages SOAP à se produire sous le contexte authentifié d'une information d'identification Windows. Utilise le mécanisme de négociation SSPI pour sélectionner le protocole Kerberos ou NTLM comme service d'authentification.|  
|Nom d’utilisateur|Autorise le service à exiger que le client soit authentifié avec des informations d'identification de nom d'utilisateur. Notez que WCF n’autorise pas les opérations de chiffrement avec le nom d’utilisateur, telles que la génération d’une signature ou le chiffrement des données. Par conséquent, WCF garantit que le transport est sécurisé lors de l’utilisation des informations d’identification de nom d’utilisateur.|  
|Certificat|Autorise le service à exiger une authentification du client via un certificat.|  
|CardSpace|Autorise le service à exiger que le client soit authentifié à l’aide d’un CardSpace.|  
  
### <a name="programming-credentials"></a>Programmation d'informations d'identification  
 Pour chacun des types d’informations d’identification du client, le modèle de programmation WCF vous permet de spécifier les valeurs d’informations d’identification et les validateurs d’informations d’identification à l’aide de comportements de service et de canaux.  
  
 La sécurité WCF a deux types d’informations d’identification : les comportements d’informations d’identification de service et les comportements d’informations d’identification de canal. Les comportements d’informations d’identification dans WCF spécifient les données réelles, à savoir, les informations d’identification utilisées pour satisfaire les exigences de sécurité exprimées par les liaisons. Dans WCF, une classe de client est le composant d’exécution qui effectue la conversion entre l’appel de l’opération et les messages. Tous les clients héritent de la classe <xref:System.ServiceModel.ClientBase%601>. La propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> sur la classe de base vous permet de spécifier différentes valeurs d'informations d'identification du client.  
  
 Dans WCF, les comportements de service sont des attributs appliqués à la classe qui implémente un contrat de service (interface) pour contrôler le service par programme. La classe <xref:System.ServiceModel.Description.ServiceCredentials> vous permet de spécifier des certificats pour les informations d'identification du service et des paramètres de validation de client pour divers types d'informations d'identification du client.  
  
### <a name="negotiation-model-for-message-security"></a>Modèle de négociation pour la sécurité de message  
 Le mode de sécurité du message vous permet d'exécuter la sécurité de transfert afin que les informations d'identification du service soient configurées au niveau du client hors bande. Par exemple, si vous utilisez un certificat stocké dans le magasin de certificats Windows, vous devez utiliser un outil tel qu'un composant logiciel enfichable MMC (Microsoft Management Console).  
  
 Le mode de sécurité du message vous permet également d'exécuter la sécurité de transfert afin que les informations d'identification du service soient échangées avec le client dans le cadre d'une négociation initiale. Pour activer la négociation, affectez <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> à la propriété `true`.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la création de points de terminaison](../endpoint-creation-overview.md)
- [Liaisons fournies par le système](../system-provided-bindings.md)
- [Présentation de la sécurité](security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
