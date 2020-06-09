---
title: Meilleures pratiques pour la sécurité dans WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c99ab5e1e72aefc688df1692091e60caf930d5e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597616"
---
# <a name="best-practices-for-security-in-wcf"></a>Meilleures pratiques pour la sécurité dans WCF
Les sections suivantes répertorient les bonnes pratiques à prendre en compte durant la création d’applications sécurisées à l’aide de WCF (Windows Communication Foundation). Pour plus d’informations sur la sécurité, consultez [Considérations relatives à la sécurité](security-considerations-in-wcf.md), [Considérations sur la sécurité des données](security-considerations-for-data.md) et [Considérations sur la sécurité des métadonnées](security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identifier les services d'authentification Windows avec les SPN  
 Les services peuvent être identifiés avec les noms d'utilisateur principaux (UPN) ou les noms de principaux du service (SPN). Les services qui s'exécutent sous des comptes d'ordinateur, tels que les services réseau, ont une identité SPN qui correspond à l'ordinateur en question. Les services qui s'exécutent sous des comptes d'utilisateur ont une identité UPN qui correspond à l'utilisateur en question, bien que l'outil `setspn` puisse être utilisé pour assigner un SPN au compte d'utilisateur. La configuration d'un service de sorte qu'il puisse être identifié par son SPN et la configuration des clients qui se connectent au service pour utiliser ce SPN peuvent compliquer certaines attaques. Cette recommandation s’applique aux liaisons utilisant la négociation SSPI ou Kerberos.  Les clients doivent toujours spécifier un SPN dans le cas où SSPI revient à NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Vérifier les identités des services dans WSDL  
 WS-SecurityPolicy permet aux services de publier des informations concernant leurs propres identités dans les métadonnées. Quand elles sont récupérées via `svcutil` ou d’autres méthodes telles que <xref:System.ServiceModel.Description.WsdlImporter>, ces informations d’identité sont traduites en propriétés d’identité des adresses du point de terminaison de service WCF. Les clients qui ne vérifient pas l'exactitude et la validité de ces identités de service contournent efficacement l'authentification des services. Un service malveillant peut exploiter ces clients pour transférer des informations d'identification et exécuter d'autres attaques « de l'intercepteur » en modifiant l'identité prétendue dans son WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Utiliser des certificats X509 au lieu de NTLM  
 WCF propose deux mécanismes d’authentification pair à pair : les certificats X509 (utilisés par le canal homologue) et l’authentification Windows, où une négociation SSPI passe à une version antérieure, de Kerberos à NTLM.  L'authentification basée sur des certificats utilisant des tailles de clé de 1 024 bits ou plus est préférée à NTLM pour plusieurs raisons :  
  
- la disponibilité de l'authentification mutuelle ;  
  
- l'utilisation d'algorithmes de chiffrement plus robustes ;  
  
- la plus grande complexité liée à l'utilisation des informations d'identification X509 transférées.  

## <a name="always-revert-after-impersonation"></a>Toujours rétablir après l'emprunt d'identité  
 Lorsque vous utilisez des API qui activent l'emprunt d'identité d'un client, veillez à rétablir l'identité d'origine. Par exemple, quand vous utilisez <xref:System.Security.Principal.WindowsIdentity> et <xref:System.Security.Principal.WindowsImpersonationContext>, employez l’instruction C# `using` ou l’instruction Visual Basic `Using`, comme indiqué dans le code suivant. La classe <xref:System.Security.Principal.WindowsImpersonationContext> implémente l'interface <xref:System.IDisposable>, et par conséquent, le common language runtime (CLR) rétablit automatiquement l'identité d'origine dès que le code quitte le bloc `using`.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Personnifier uniquement si nécessaire  
 À l'aide de la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> de la classe <xref:System.Security.Principal.WindowsIdentity>, il est possible d'utiliser l'emprunt d'identité dans une étendue très contrôlée. Cette approche s'oppose à l'utilisation de la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> du <xref:System.ServiceModel.OperationBehaviorAttribute> qui autorise l'emprunt d'identité pour l'étendue de l'opération entière. Si possible, contrôlez l'étendue de l'emprunt d'identité en utilisant la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> plus précise.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Obtenir des métadonnées de sources fiables  
 Soyez sûr de la source de vos métadonnées et vérifiez qu'elles n'ont pas été falsifiées. Les métadonnées récupérées à l'aide du protocole HTTP sont envoyées en texte clair et peuvent être falsifiées. Si le service utilise les propriétés <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> et <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>, utilisez l'URL que le créateur du service vous a fournie pour télécharger les données à l'aide du protocole HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publier des métadonnées à l'aide de la sécurité  
 Pour empêcher la falsification des métadonnées publiées d'un service, sécurisez le point de terminaison d'échange de métadonnées avec la sécurité de transport ou au niveau du message. Pour plus d’informations, consultez [Publication de points de terminaison de métadonnées](../publishing-metadata-endpoints.md) et [Guide pratique pour publier les métadonnées d’un service à l’aide de code](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Utiliser un émetteur local  
 Si une liaison et une adresse d’émetteur sont spécifiées pour une liaison donnée, l’émetteur local n’est pas utilisé pour les points de terminaison qui utilisent cette liaison. Les clients qui prévoient d’utiliser systématiquement l’émetteur local doivent s’assurer de ne pas utiliser de liaison de ce type ou de modifier la liaison afin que l’adresse de l’émetteur ait la valeur null.  
  
## <a name="saml-token-size-quotas"></a>Quotas de taille de jeton SAML  
 Lorsque les jetons SAML (Security Assertions Markup Language) sont sérialisés dans des messages, soit lorsqu'ils sont délivrés par un service de jeton de sécurité (STS), soit lorsque les clients les présentent à des services dans le cadre de l'authentification, le quota de taille maximale de message doit être suffisamment grand pour accommoder le jeton SAML et les autres parties de message. Dans un cas normal, les quotas de taille de message par défaut sont suffisants. Toutefois, dans les cas où un jeton SAML est grand parce qu'il contient des centaines de revendications, les quotas doivent être augmentés pour accommoder le jeton sérialisé. Pour plus d’informations sur les quotas, consultez [Considérations sur la sécurité des données](security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Affectation de la valeur True à SecurityBindingElement.IncludeTimestamp sur des liaisons personnalisées  
 Lorsque vous créez une liaison personnalisée, vous devez affecter la valeur <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> à `true`. Sinon, si <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> a la valeur `false` et que le client utilise un jeton basé sur une clé asymétrique comme un certificat X509, le message ne sera pas signé.  
  
## <a name="see-also"></a>Voir aussi

- [Security Considerations](security-considerations-in-wcf.md)
- [Considérations relatives à la sécurité des données](security-considerations-for-data.md)
- [Considérations sur la sécurité des métadonnées](security-considerations-with-metadata.md)
