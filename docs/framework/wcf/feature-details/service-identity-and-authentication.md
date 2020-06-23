---
title: Identité du service et authentification
description: En savoir plus sur l’identité de point de terminaison d’un service, valeur générée à partir du service WSDL, que WCF utilise pour authentifier le service.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: ae217b4a2c3432321c7ef2e663922a87b82acbea
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246569"
---
# <a name="service-identity-and-authentication"></a>Identité du service et authentification
L’identité du *point de terminaison* d’un service est une valeur générée à partir du service Web Services Description Language (WSDL). Cette valeur, propagée à tout client, est utilisée pour authentifier le service. Une fois que le client a initialisé une communication à un point de terminaison et le service s'authentifie au client, le client compare la valeur de l'identité du point de terminaison avec la valeur réelle que le processus d'authentification du point de terminaison a retournée. Si elles correspondent, le client est assuré qu'il a contacté le point de terminaison du service attendu. Cela fonctionne comme une protection contre le *phishing* en empêchant un client d’être redirigé vers un point de terminaison hébergé par un service malveillant.  
  
 Pour obtenir un exemple d’application illustrant le paramètre d’identité, consultez [exemple d’identité de service](../samples/service-identity-sample.md). Pour plus d’informations sur les points de terminaison et les adresses de point de terminaison, consultez [adresses](endpoint-addresses.md).  
  
> [!NOTE]
> Lorsque vous utilisez NT LanMan (NTLM) pour l'authentification, l'identité du service n'est pas vérifiée parce que, sous NTLM, le client ne peut pas authentifier le serveur. NTLM est utilisé lorsque les ordinateurs font partie d'un groupe de travail Windows, ou lors de l'exécution d'une version antérieure de Windows qui ne prend pas en charge l'authentification Kerberos.  
  
 Lorsque le client initie un canal sécurisé pour envoyer un message à un service sur celui-ci, l’infrastructure Windows Communication Foundation (WCF) authentifie le service et envoie le message uniquement si l’identité du service correspond à l’identité spécifiée dans l’adresse du point de terminaison utilisée par le client.  
  
 Le traitement de l'identité inclut les étapes suivantes :  
  
- Au moment du design, le développeur d'applications détermine l'identité du service à partir des métadonnées du point de terminaison (exposé à travers WSDL).  
  
- Pendant l'exécution, l'application cliente vérifie les revendications des informations d'identification de sécurité du service avant d'envoyer des messages au service.  
  
 Le traitement de l'identité sur le client est analogue à l'authentification du client sur le service. Un service sécurisé n'exécute pas de code jusqu'à ce que les informations d'identification du client aient été authentifiées. De la même façon, le client n'envoie pas de messages au service jusqu'à ce que les informations d'identification du service aient été authentifiées sur la base de ce qui est déjà connu via métadonnées du service.  
  
 La propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> de la classe <xref:System.ServiceModel.EndpointAddress> représente l'identité du service appelé par le client. Le service publie <xref:System.ServiceModel.EndpointAddress.Identity%2A> dans ses métadonnées. Lorsque le développeur client exécute l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) sur le point de terminaison de service, la configuration générée contient la valeur de la propriété du service <xref:System.ServiceModel.EndpointAddress.Identity%2A> . L’infrastructure WCF (si elle est configurée avec la sécurité) vérifie que le service possède l’identité spécifiée.  
  
> [!IMPORTANT]
> Les métadonnées contiennent l'identité attendue du service, il est par conséquent recommandé d'exposer les métadonnées du service de manière sécurisée, par exemple, en créant un point de terminaison HTTPS. Pour plus d’informations, consultez [Comment : sécuriser des points de terminaison de métadonnées](how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Types d'identité  
 Un service peut fournir six types d’identités. Chaque type d'identité correspond à un élément qui peut être contenu à l'intérieur de l'élément `<identity>` dans la configuration. Le type utilisé dépend du scénario et des exigences de sécurité du service. Le tableau suivant décrit chaque type d'identité.  
  
|Type d'identité|Description|Scénario typique|  
|-------------------|-----------------|----------------------|  
|DNS (Domain Name System)|Utilisez cet élément avec les certificats X.509 ou les comptes Windows. Il compare le nom DNS spécifié dans l'information d'identification avec la valeur spécifiée dans cet élément.|Un contrôle DNS vous permet d'utiliser des certificats avec les noms DNS ou de sujet. Si un certificat est réédité avec le même nom DNS ou de sujet, le contrôle d'identité est encore valide. Lorsqu'un certificat est réédité, il obtient une nouvelle clé RSA mais conserve le même nom DNS ou de sujet. Cela signifie que les clients n'ont pas à mettre à jour les informations d'identité relatives du service.|  
|Certificat. Il s'agit de la valeur par défaut lorsque la valeur de certificat a été attribuée à la propriété `ClientCredentialType`.|Cet élément spécifie une valeur de certificat X.509 encodée en base 64 qui sera comparée avec le client.<br /><br /> Utilisez également cet élément lors de l’utilisation d’un CardSpace comme informations d’identification pour authentifier le service.|Cet élément restreint l'authentification à un certificat unique basé sur sa valeur d'empreinte numérique. Cela permet une authentification plus stricte parce que les valeurs d'empreinte numérique sont uniques. Il convient cependant de noter que si le certificat est réédité avec le même nom de sujet, il a également une nouvelle empreinte numérique. Par conséquent, les clients ne sont pas en mesure de valider le service à moins que la nouvelle empreinte numérique soit connue. Pour plus d’informations sur la recherche de l’empreinte numérique d’un certificat, consultez [Comment : récupérer l’empreinte numérique d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Référence de certificat|Identique à l'option de certificat décrite précédemment. Toutefois, cet élément vous permet de spécifier un nom de certificat et l'emplacement du magasin à partir duquel vous pouvez le récupérer.|Identique au scénario de certificat décrit précédemment.<br /><br /> L'avantage est que l'emplacement du magasin du certificat peut changer.|  
|RSA|Cet élément spécifie une valeur de clé RSA à comparer avec le client. Il est similaire à l'option de certificat mais la clé RSA est utilisée au lieu de l'empreinte numérique du certificat.|Un contrôle RSA vous permet de restreindre spécifiquement l'authentification à un certificat unique en fonction de sa clé RSA. Cela permet l'authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.|  
|Nom d’utilisateur principal. Il s'agit de la valeur par défaut lorsque la valeur Windows est attribuée à `ClientCredentialType` et le processus du service ne s'exécute pas sous l'un des comptes système.|Cet élément spécifie l'UPN sous lequel le service s'exécute. Consultez la section protocole et identité Kerberos de [remplacement de l’identité d’un service pour l’authentification](../extending/overriding-the-identity-of-a-service-for-authentication.md).|Cela garantit que le service s'exécute sous un compte d'utilisateur Windows spécifique. Le compte d'utilisateur peut être l'utilisateur actuellement connecté ou le service qui s'exécute sous un compte d'utilisateur particulier.<br /><br /> Ce paramètre tire parti de la sécurité Windows Kerberos si le service s'exécute sous un compte de domaine dans un environnement Active Directory.|  
|Nom de principal du service (SPN). Valeur par défaut lorsque le `ClientCredentialType` a la valeur Windows et le processus du service s'exécute sous l'un des comptes système LocalService, LocalSystem ou NetworkService.|Cet élément spécifie le SPN associé au compte du service. Consultez la section protocole et identité Kerberos de [remplacement de l’identité d’un service pour l’authentification](../extending/overriding-the-identity-of-a-service-for-authentication.md).|Cela garantit que le SPN et le compte Windows spécifique, associé au SPN, identifient le service.<br /><br /> Vous pouvez utiliser l'outil Setspn.exe pour associer un compte d'ordinateur pour le compte d'utilisateur du service.<br /><br /> Ce paramètre tire parti de la sécurité Windows Kerberos si le service s'exécute sous l'un des comptes système ou sous un compte de domaine qui a un nom SPN associé et si l'ordinateur est un membre d'un domaine dans un environnement Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Spécification de l'identité au service  
 Généralement, vous n'avez pas besoin de définir l'identité sur un service car la sélection d'un type d'informations d'identification du client impose le type d'identité exposé dans les métadonnées du service. Pour plus d’informations sur la façon de remplacer ou de spécifier l’identité du service, consultez [substitution de l’identité d’un service pour l’authentification](../extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Utilisation \<identity> de l’élément dans la configuration  
 Si vous remplacez le type d’information d’identification du client dans la liaison présentée précédemment par `Certificate,`, alors le fichier WSDL généré contient un certificat X.509 sérialisé en base 64 pour la valeur d’identité, tel qu’indiqué dans le code suivant. Il s'agit de la valeur par défaut pour tous les types d'informations d'identification du client autres que Windows.  

 Vous pouvez modifier la valeur de l’identité de service par défaut ou modifier le type de l’identité à l’aide de l' `<identity>` élément dans la configuration ou en définissant l’identité dans le code. Le code de configuration suivant affecte à une identité DNS (Domain Name System) la valeur `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Définition de l'identité par programme  
 Votre service n’a pas besoin de spécifier explicitement une identité, car WCF le détermine automatiquement. Toutefois, WCF vous permet de spécifier une identité sur un point de terminaison, si nécessaire. Le code suivant ajoute un point de terminaison de service avec une identité DNS spécifique.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Spécification de l'identité au client  
 Au moment du design, un développeur client utilise généralement l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer la configuration du client. Le fichier de configuration généré (prévu pour une utilisation par le client) contient l'identité du serveur. Par exemple, le code suivant est généré à partir d'un service qui spécifie une identité DNS, comme illustré dans l'exemple précédent. Notez que la valeur de l'identité du point de terminaison du client correspond à celle du service. Dans ce cas, lorsque le client reçoit les informations d'identification Windows (Kerberos) pour le service, il s'attend à ce que la valeur soit `contoso.com`.  

 Si, au lieu de Windows, le service spécifie un certificat pour le type d'information d'identification du client, alors, la propriété DNS du certificat est supposée être la valeur `contoso.com`. (Ou si la propriété DNS est `null`, le nom de sujet du certificat doit être `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Utilisation d'une valeur spécifique pour l'identité  
 Le fichier de configuration client suivant illustre comment l'identité du service est supposée être une valeur spécifique. Dans l'exemple suivant, le client peut communiquer avec deux points de terminaison. Le premier est identifié par une empreinte numérique de certificat et le second par une clé RSA de certificat. Autrement dit, il s'agit d'un certificat qui contient uniquement une paire clé publique/clé privée, mais n'est pas publié par une autorité approuvée.  

## <a name="identity-checking-at-run-time"></a>Contrôle d'identité au moment de l'exécution  
 Au moment du design, un développeur d'applications détermine l'identité du serveur via ses métadonnées. Pendant l'exécution, le contrôle d'identité est effectué avant d'appeler un point de terminaison sur le service.  
  
 La valeur d'identité est attachée au type d'authentification spécifié par les métadonnées, en d'autres termes, le type d'information d'identification utilisé pour le service.  
  
 Si le canal est configuré pour authentifier à l'aide du message ou d'un SSL (Secure Sockets Layer) au niveau du transport avec des certificats X.509 pour l'authentification, les valeurs d'identité suivantes sont valides :  
  
- DNS. WCF s’assure que le certificat fourni pendant la négociation SSL contient un attribut DNS ou `CommonName` (CN) égal à la valeur spécifiée dans l’identité DNS sur le client. Notez que ces contrôles sont complémentaires à la détermination de la validé du certificat du serveur. Par défaut, WCF valide que le certificat de serveur est émis par une autorité racine approuvée.  
  
- Certificat. Pendant la négociation SSL, WCF s’assure que le point de terminaison distant fournit la valeur de certificat exacte spécifiée dans l’identité.  
  
- Référence de certificat. Identique au certificat.  
  
- RSA. Pendant la négociation SSL, WCF s’assure que le point de terminaison distant fournit la clé RSA exacte spécifiée dans l’identité.  
  
 Si le service authentifie en utilisant le message - ou un SSL au niveau du transport avec des informations d'identification Windows pour l'authentification, et négocie l'information d'identification, les valeurs d'identité suivantes sont valides :  
  
- DNS. La négociation passe le SPN du service afin que le nom DNS puisse être vérifié. Le SPN se présente sous la forme `host/<dns name>`.  
  
- SPN. Un service SPN explicite est retourné, par exemple, `host/myservice`.  
  
- UPN. L'UPN du compte de service. L’UPN se présente sous la forme `username` @ `domain` . Par exemple, lorsque le service s'exécute dans un compte d'utilisateur, cela peut être `username@contoso.com`.  
  
 La spécification de l'identité par programmation (à l'aide de la propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> ) est facultative. Si aucune identité n'est spécifiée et si le type d'information d'identification du client est Windows, la valeur par défaut est SPN et la valeur définie dans la partie correspondant au nom d'hôte de l'adresse du point de terminaison du service est préfixée avec la valeur littérale "host/". Si aucune identité n'est spécifiée et si le type d'information d'identification du client est un certificat, la valeur par défaut est `Certificate`. Cela s'applique à la fois à la sécurité au niveau du message et au niveau du transport.  
  
## <a name="identity-and-custom-bindings"></a>Identité et liaisons personnalisées  
 Parce que l'identité d'un service dépend du type de liaison utilisé, assurez-vous qu'une identité appropriée est exposée lors de la création d'une liaison personnalisée. Par exemple, dans l’exemple de code suivant, l’identité exposée n’est pas compatible avec le type de sécurité parce que l’identité de la liaison de démarrage de conversation sécurisée ne correspond pas à l’identité de la liaison sur le point de terminaison. La liaison de conversation sécurisée définit l'identité DNS, tandis que <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> définit l'identité UPN ou SPN.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Pour plus d’informations sur la façon de repiler correctement les éléments de liaison pour une liaison personnalisée, consultez [création de liaisons définies par l’utilisateur](../extending/creating-user-defined-bindings.md). Pour plus d’informations sur la création d’une liaison personnalisée avec le <xref:System.ServiceModel.Channels.SecurityBindingElement> , consultez [Comment : créer un SecurityBindingElement pour un mode d’authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Guide pratique pour créer un vérificateur d’identité du client personnalisé](../extending/how-to-create-a-custom-client-identity-verifier.md)
- [Sélection d'un type d'informations d'identification](selecting-a-credential-type.md)
- [Working with Certificates](working-with-certificates.md)
- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Création de liaisons définies par l’utilisateur](../extending/creating-user-defined-bindings.md)
- [Comment : récupérer l'empreinte numérique d'un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md)
