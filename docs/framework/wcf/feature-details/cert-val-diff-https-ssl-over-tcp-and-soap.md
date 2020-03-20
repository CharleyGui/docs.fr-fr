---
title: Différences de validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0e82d1898bec7cda474a5a92958b5af1b30c9de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185408"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Différences de validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP
Vous pouvez utiliser des certificats dans Windows Communication Foundation (WCF) avec la sécurité de la couche de message (SOAP) en plus de la sécurité des couches de transport (TLS) sur HTTP (HTTPS) ou TCP. Cette rubrique décrit les différences dans la façon dont ces certificats sont validés.  
  
## <a name="validation-of-https-client-certificates"></a>Validation des certificats clients HTTPS  
 Lors de l'utilisation du protocole HTTPS pour communiquer entre un client et un service, le certificat que le client utilise pour s'authentifier auprès du service doit prendre en charge l'approbation de chaîne. Autrement dit, il doit être chaîné à une autorité de certification racine approuvée. Dans le cas contraire, la couche HTTP lève une exception <xref:System.Net.WebException> avec le message "Le serveur distant a retourné une erreur : (403) Interdit". WCF fait surface <xref:System.ServiceModel.Security.MessageSecurityException>cette exception comme un .  
  
## <a name="validation-of-https-service-certificates"></a>Validation des certificats de service HTTPS  
 Lors de l'utilisation du protocole HTTPS pour communiquer entre un client et un service, le certificat avec lequel le serveur effectue l'authentification doit prendre en charge l'approbation de chaîne par défaut. Autrement dit, il doit être chaîné à une autorité de certification racine approuvée. Aucun contrôle en ligne n'est effectué pour voir si le certificat a été révoqué. Vous pouvez compenser ce comportement en enregistrant un rappel <xref:System.Net.Security.RemoteCertificateValidationCallback>, comme illustré dans le code ci-dessous.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 où la signature pour `ValidateServerCertificate` est comme suit :  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 L'implémentation de `ValidateServerCertificate` peut effectuer toutes les vérifications que le développeur d'une application cliente juge nécessaires pour valider le certificat de service.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Validation de certificats clients dans SSL sur TCP ou la sécurité SOAP  
 Lors de l'utilisation du protocole SSL (Secure Sockets Layer) sur TCP ou de la sécurité (SOAP) de message, les certificats clients sont validés en fonction de la valeur de propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>. La propriété a l'une des valeurs <xref:System.ServiceModel.Security.X509CertificateValidationMode>. La vérification de la révocation est effectuée en fonction des valeurs de la valeur de propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>. La propriété a l'une des valeurs <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Validation d’un certificat de service dans SSL sur TCP et la sécurité SOAP  
 Lors de l'utilisation du protocole SSL sur TCP ou de la sécurité de message (SOAP), les certificats de service sont validés en fonction de la valeur de propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>. La propriété a l'une des valeurs <xref:System.ServiceModel.Security.X509CertificateValidationMode>.  
  
 La vérification de la révocation est effectuée en fonction des valeurs de la valeur de propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> de la classe <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>. La propriété a l'une des valeurs <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
