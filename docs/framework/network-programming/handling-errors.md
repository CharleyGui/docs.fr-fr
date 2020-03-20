---
title: Gestion des erreurs
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: f5be5d8e14d7aa2d98009fc10c9cce314e745ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180873"
---
# <a name="handling-errors"></a><span data-ttu-id="1dde5-102">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="1dde5-102">Handling Errors</span></span>

<span data-ttu-id="1dde5-103">Les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> lèvent à la fois les exceptions système (comme <xref:System.ArgumentException>) et les exceptions spécifiques au web (qui sont des <xref:System.Net.WebException> levées par la méthode <xref:System.Net.WebRequest.GetResponse%2A>).</span><span class="sxs-lookup"><span data-stu-id="1dde5-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="1dde5-104">Chaque **WebException** comprend une propriété <xref:System.Net.WebException.Status%2A> qui contient une valeur de l’énumération <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="1dde5-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="1dde5-105">Vous pouvez examiner la propriété **Status** afin d’identifier l’erreur qui s’est produite et de prendre les mesures appropriées pour la résoudre.</span><span class="sxs-lookup"><span data-stu-id="1dde5-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="1dde5-106">Le tableau suivant décrit les valeurs possibles pour la propriété **Status**.</span><span class="sxs-lookup"><span data-stu-id="1dde5-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="1dde5-107">Statut</span><span class="sxs-lookup"><span data-stu-id="1dde5-107">Status</span></span>|<span data-ttu-id="1dde5-108">Description</span><span class="sxs-lookup"><span data-stu-id="1dde5-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1dde5-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-109">ConnectFailure</span></span>|<span data-ttu-id="1dde5-110">Le service distant n’a pas pu être contacté au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="1dde5-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="1dde5-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="1dde5-111">ConnectionClosed</span></span>|<span data-ttu-id="1dde5-112">La connexion a été interrompue prématurément.</span><span class="sxs-lookup"><span data-stu-id="1dde5-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="1dde5-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-113">KeepAliveFailure</span></span>|<span data-ttu-id="1dde5-114">Le serveur a fermé une connexion établie avec l’en-tête Keep-alive défini.</span><span class="sxs-lookup"><span data-stu-id="1dde5-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="1dde5-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-115">NameResolutionFailure</span></span>|<span data-ttu-id="1dde5-116">Le service de noms n’a pas pu résoudre le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="1dde5-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="1dde5-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="1dde5-117">ProtocolError</span></span>|<span data-ttu-id="1dde5-118">La réponse reçue du serveur était complète, mais indiquait une erreur au niveau du protocole.</span><span class="sxs-lookup"><span data-stu-id="1dde5-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="1dde5-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-119">ReceiveFailure</span></span>|<span data-ttu-id="1dde5-120">Aucune réponse complète n’a été reçue du serveur distant.</span><span class="sxs-lookup"><span data-stu-id="1dde5-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="1dde5-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="1dde5-121">RequestCanceled</span></span>|<span data-ttu-id="1dde5-122">La demande a été annulée.</span><span class="sxs-lookup"><span data-stu-id="1dde5-122">The request was canceled.</span></span>|  
|<span data-ttu-id="1dde5-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-123">SecureChannelFailure</span></span>|<span data-ttu-id="1dde5-124">Une erreur s’est produite dans un lien de canal sécurisé.</span><span class="sxs-lookup"><span data-stu-id="1dde5-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="1dde5-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-125">SendFailure</span></span>|<span data-ttu-id="1dde5-126">Une demande complète n’a pas pu être envoyée au serveur distant.</span><span class="sxs-lookup"><span data-stu-id="1dde5-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="1dde5-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="1dde5-127">ServerProtocolViolation</span></span>|<span data-ttu-id="1dde5-128">La réponse du serveur n’était pas une réponse HTTP valide.</span><span class="sxs-lookup"><span data-stu-id="1dde5-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="1dde5-129">Succès</span><span class="sxs-lookup"><span data-stu-id="1dde5-129">Success</span></span>|<span data-ttu-id="1dde5-130">Aucune erreur n’a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="1dde5-130">No error was encountered.</span></span>|  
|<span data-ttu-id="1dde5-131">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="1dde5-131">Timeout</span></span>|<span data-ttu-id="1dde5-132">Aucune réponse n’a été reçue pendant le délai défini pour la demande.</span><span class="sxs-lookup"><span data-stu-id="1dde5-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="1dde5-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-133">TrustFailure</span></span>|<span data-ttu-id="1dde5-134">Un certificat de serveur n’a pas pu être validé.</span><span class="sxs-lookup"><span data-stu-id="1dde5-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="1dde5-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="1dde5-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="1dde5-136">Un message a été reçu qui dépassait la limite spécifiée lors de l’envoi d’une demande ou de la réception d’une réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="1dde5-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="1dde5-137">Pending</span><span class="sxs-lookup"><span data-stu-id="1dde5-137">Pending</span></span>|<span data-ttu-id="1dde5-138">Une demande asynchrone interne est en attente.</span><span class="sxs-lookup"><span data-stu-id="1dde5-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="1dde5-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-139">PipelineFailure</span></span>|<span data-ttu-id="1dde5-140">Cette valeur prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1dde5-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="1dde5-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="1dde5-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="1dde5-142">Le service de résolution de nom n’a pas pu résoudre le nom d’hôte proxy.</span><span class="sxs-lookup"><span data-stu-id="1dde5-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="1dde5-143">UnknownError</span><span class="sxs-lookup"><span data-stu-id="1dde5-143">UnknownError</span></span>|<span data-ttu-id="1dde5-144">Une exception de type inconnu s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1dde5-144">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="1dde5-145">Quand la propriété **Status** a la valeur **WebExceptionStatus.ProtocolError**, une **WebResponse** qui contient la réponse du serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="1dde5-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="1dde5-146">Vous pouvez examiner cette réponse afin de déterminer la source réelle de l’erreur de protocole.</span><span class="sxs-lookup"><span data-stu-id="1dde5-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="1dde5-147">L’exemple suivant indique comment intercepter une **WebException**.</span><span class="sxs-lookup"><span data-stu-id="1dde5-147">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try
{  
    // Create a request instance.  
    WebRequest myRequest =
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,
    //   there has been a protocol error and a WebResponse
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,
    '   there has been a protocol error and a WebResponse
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
<span data-ttu-id="1dde5-148">Les applications qui utilisent la classe <xref:System.Net.Sockets.Socket> lèvent des <xref:System.Net.Sockets.SocketException> quand des erreurs se produisent sur le socket Windows.</span><span class="sxs-lookup"><span data-stu-id="1dde5-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="1dde5-149">Les classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> et <xref:System.Net.Sockets.UdpClient> sont générées sur la classe **Socket** et lèvent également des **SocketExceptions**.</span><span class="sxs-lookup"><span data-stu-id="1dde5-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="1dde5-150">Quand une **SocketException** est levée, la classe **SocketException** affecte à la propriété <xref:System.Net.Sockets.SocketException.ErrorCode%2A> la dernière erreur de socket du système d’exploitation s’étant produite.</span><span class="sxs-lookup"><span data-stu-id="1dde5-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="1dde5-151">Pour plus d’informations sur les codes d’erreur de socket, consultez la documentation relative aux codes d’erreur des API Winsock 2.0 dans MSDN.</span><span class="sxs-lookup"><span data-stu-id="1dde5-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dde5-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dde5-152">See also</span></span>

- [<span data-ttu-id="1dde5-153">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="1dde5-153">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="1dde5-154">Demande de données</span><span class="sxs-lookup"><span data-stu-id="1dde5-154">Requesting Data</span></span>](requesting-data.md)
