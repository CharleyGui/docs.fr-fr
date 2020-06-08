---
title: Authentification NTLM et Kerberos
description: Découvrez comment l’authentification NTLM par défaut et l’authentification Kerberos fonctionnent pour une application .NET Framework et en savoir plus sur l’authentification NTLM non définie par défaut.
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
ms.openlocfilehash: d91ebca084d84acd4eb8facb82ff08679ec35cd0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502234"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="1869b-103">Authentification NTLM et Kerberos</span><span class="sxs-lookup"><span data-stu-id="1869b-103">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="1869b-104">Par défaut, l’authentification NTLM et l’authentification Kerberos utilisent les informations d’identification utilisateur de Microsoft Windows NT qui sont associées à l’application appelante pour tenter l’authentification auprès du serveur.</span><span class="sxs-lookup"><span data-stu-id="1869b-104">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="1869b-105">Lorsque vous utilisez l’authentification NTLM qui n’est pas celle par défaut, l’application définit le type d’authentification sur NTLM et utilise un objet <xref:System.Net.NetworkCredential> pour passer le nom d’utilisateur, le mot de passe et le domaine à l’hôte, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1869b-105">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1869b-106">Les applications qui doivent se connecter aux services Internet à l’aide des informations d’identification de l’utilisateur de l’application peuvent le faire en utilisant les informations d’identification par défaut de l’utilisateur, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1869b-106">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1869b-107">Le module d’authentification par négociation détermine si le serveur distant utilise l’authentification NTLM ou l’authentification Kerberos, et envoie sa réponse.</span><span class="sxs-lookup"><span data-stu-id="1869b-107">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1869b-108">L’authentification NTLM ne fonctionne pas via un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="1869b-108">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1869b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1869b-109">See also</span></span>

- [<span data-ttu-id="1869b-110">Authentification de base et Digest</span><span class="sxs-lookup"><span data-stu-id="1869b-110">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="1869b-111">Authentification Internet</span><span class="sxs-lookup"><span data-stu-id="1869b-111">Internet Authentication</span></span>](internet-authentication.md)
