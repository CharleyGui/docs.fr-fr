---
title: Authentification NTLM et Kerberos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: b05cd88fcb492ab27e1d311045b72208167508f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963921"
---
# <a name="ntlm-and-kerberos-authentication"></a>Authentification NTLM et Kerberos
Par défaut, l’authentification NTLM et l’authentification Kerberos utilisent les informations d’identification utilisateur de Microsoft Windows NT qui sont associées à l’application appelante pour tenter l’authentification auprès du serveur. Lorsque vous utilisez l’authentification NTLM qui n’est pas celle par défaut, l’application définit le type d’authentification sur NTLM et utilise un objet <xref:System.Net.NetworkCredential> pour passer le nom d’utilisateur, le mot de passe et le domaine à l’hôte, comme indiqué dans l’exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 Les applications qui doivent se connecter aux services Internet à l’aide des informations d’identification de l’utilisateur de l’application peuvent le faire en utilisant les informations d’identification par défaut de l’utilisateur, comme indiqué dans l’exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 Le module d’authentification par négociation détermine si le serveur distant utilise l’authentification NTLM ou l’authentification Kerberos, et envoie sa réponse.  
  
> [!NOTE]
> L’authentification NTLM ne fonctionne pas via un serveur proxy.  
  
## <a name="see-also"></a>Voir aussi

- [Authentification de base et authentification Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [Authentification Internet](../../../docs/framework/network-programming/internet-authentication.md)
