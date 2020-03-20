---
title: Authentification de base et authentification Digest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048899"
---
# <a name="basic-and-digest-authentication"></a>Authentification de base et authentification Digest
L’implémentation <xref:System.Net> de l’authentification de base et Digest est conforme à RFC2617 – Authentification HTTP : authentification de base et authentification Digest (disponible sur site web du [World Wide Web Consortium](https://www.w3.org)).  
  
 Pour utiliser l’authentification de base et l’authentification Digest, une application doit fournir un nom d’utilisateur et un mot de passe dans la propriété <xref:System.Net.WebRequest.Credentials%2A> de l’objet <xref:System.Net.WebRequest> qu’elle utilise pour demander des données à partir d’Internet, comme indiqué dans l’exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> Les données transmises avec une authentification de base et Digest ne sont pas chiffrées, par conséquent les données sont visibles par tous. De plus, les informations d'authentification de base (nom d'utilisateur et mot de passe) sont envoyées en texte clair et peuvent être interceptées.  
  
## <a name="see-also"></a>Voir aussi

- [Authentification du NTLM et de Kerberos](ntlm-and-kerberos-authentication.md)
- [Authentification Internet](internet-authentication.md)
