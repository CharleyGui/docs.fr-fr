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
ms.openlocfilehash: 67330962382e768849cbf67d5f412ea80f65569d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501987"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="03a74-103">Utilisation du protocole Secure Sockets Layer</span><span class="sxs-lookup"><span data-stu-id="03a74-103">Using Secure Sockets Layer</span></span>
<span data-ttu-id="03a74-104">Les classes <xref:System.Net> utilisent le protocole SSL (Secure Sockets Layer) pour chiffrer les connexions avec différents protocoles réseau.</span><span class="sxs-lookup"><span data-stu-id="03a74-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="03a74-105">Pour les connexions HTTP, les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> utilisent SSL pour communiquer avec les hôtes web qui prennent en charge SSL.</span><span class="sxs-lookup"><span data-stu-id="03a74-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="03a74-106">L’utilisation du protocole SSL est déterminée par la classe <xref:System.Net.WebRequest> en fonction de l’URI fourni.</span><span class="sxs-lookup"><span data-stu-id="03a74-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="03a74-107">Si l’URI commence par « https: », SSL est utilisé ; si l’URI commence par « http: », une connexion non chiffrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="03a74-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="03a74-108">Pour utiliser SSL avec le protocole FTP (File Transfer Protocol), définissez la propriété <xref:System.Net.FtpWebRequest.EnableSsl> sur true avant d’appeler <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="03a74-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="03a74-109">De la même façon, pour utiliser SSL avec le protocole SMTP (Simple Mail Transport Protocol), définissez la propriété <xref:System.Net.Mail.SmtpClient.EnableSsl> sur true avant d’envoyer l’e-mail.</span><span class="sxs-lookup"><span data-stu-id="03a74-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="03a74-110">La classe <xref:System.Net.Security.SslStream> fournit une abstraction de flux de données pour le protocole SSL et offre de nombreuses façons de configurer la connexion SSL.</span><span class="sxs-lookup"><span data-stu-id="03a74-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a74-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a74-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="03a74-112">Code</span><span class="sxs-lookup"><span data-stu-id="03a74-112">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="03a74-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="03a74-113">Compiling the Code</span></span>  
 <span data-ttu-id="03a74-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="03a74-114">This example requires:</span></span>  
  
- <span data-ttu-id="03a74-115">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="03a74-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a74-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03a74-116">See also</span></span>

- [<span data-ttu-id="03a74-117">Sécurité dans la programmation réseau</span><span class="sxs-lookup"><span data-stu-id="03a74-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="03a74-118">Programmation réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03a74-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="03a74-119">Sélection et validation de certificats</span><span class="sxs-lookup"><span data-stu-id="03a74-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
