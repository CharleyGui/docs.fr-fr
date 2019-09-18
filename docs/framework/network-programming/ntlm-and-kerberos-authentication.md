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
ms.openlocfilehash: ca9e1b9bf6235fdaeea25b8975155af429848ae3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047527"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="49e65-102">Authentification NTLM et Kerberos</span><span class="sxs-lookup"><span data-stu-id="49e65-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="49e65-103">Par défaut, l’authentification NTLM et l’authentification Kerberos utilisent les informations d’identification utilisateur de Microsoft Windows NT qui sont associées à l’application appelante pour tenter l’authentification auprès du serveur.</span><span class="sxs-lookup"><span data-stu-id="49e65-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="49e65-104">Lorsque vous utilisez l’authentification NTLM qui n’est pas celle par défaut, l’application définit le type d’authentification sur NTLM et utilise un objet <xref:System.Net.NetworkCredential> pour passer le nom d’utilisateur, le mot de passe et le domaine à l’hôte, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="49e65-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="49e65-105">Les applications qui doivent se connecter aux services Internet à l’aide des informations d’identification de l’utilisateur de l’application peuvent le faire en utilisant les informations d’identification par défaut de l’utilisateur, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="49e65-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="49e65-106">Le module d’authentification par négociation détermine si le serveur distant utilise l’authentification NTLM ou l’authentification Kerberos, et envoie sa réponse.</span><span class="sxs-lookup"><span data-stu-id="49e65-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49e65-107">L’authentification NTLM ne fonctionne pas via un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="49e65-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e65-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49e65-108">See also</span></span>

- [<span data-ttu-id="49e65-109">Authentification de base et authentification Digest</span><span class="sxs-lookup"><span data-stu-id="49e65-109">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="49e65-110">Authentification Internet</span><span class="sxs-lookup"><span data-stu-id="49e65-110">Internet Authentication</span></span>](internet-authentication.md)
