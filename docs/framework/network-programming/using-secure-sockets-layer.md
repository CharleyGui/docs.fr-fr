---
title: Utilisation du protocole Secure Sockets Layer
description: En savoir plus sur la façon dont System.Net et l’extension des classes utilisent le protocole SSL pour chiffrer la connexion de plusieurs protocoles réseau dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 1309e9dc594869cec7bce81ef666d9f5e06f13b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265178"
---
# <a name="using-secure-sockets-layer"></a>Utilisation du protocole Secure Sockets Layer

Les classes <xref:System.Net> utilisent le protocole SSL (Secure Sockets Layer) pour chiffrer les connexions avec différents protocoles réseau.  
  
 Pour les connexions HTTP, les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> utilisent SSL pour communiquer avec les hôtes web qui prennent en charge SSL. L’utilisation du protocole SSL est déterminée par la classe <xref:System.Net.WebRequest> en fonction de l’URI fourni. Si l’URI commence par « https: », SSL est utilisé ; si l’URI commence par « http: », une connexion non chiffrée est utilisée.  
  
 Pour utiliser SSL avec le protocole FTP (File Transfer Protocol), définissez la propriété <xref:System.Net.FtpWebRequest.EnableSsl> sur true avant d’appeler <xref:System.Net.FtpWebRequest.GetResponse>. De la même façon, pour utiliser SSL avec le protocole SMTP (Simple Mail Transport Protocol), définissez la propriété <xref:System.Net.Mail.SmtpClient.EnableSsl> sur true avant d’envoyer l’e-mail.  
  
 La classe <xref:System.Net.Security.SslStream> fournit une abstraction de flux de données pour le protocole SSL et offre de nombreuses façons de configurer la connexion SSL.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Cet exemple nécessite :  
  
- Références à l’espace de noms **System.Net**.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité dans la programmation réseau](security-in-network-programming.md)
- [Programmation réseau dans le .NET Framework](index.md)
- [Sélection et validation de certificats](certificate-selection-and-validation.md)
