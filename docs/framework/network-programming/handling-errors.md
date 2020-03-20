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
# <a name="handling-errors"></a>Gestion des erreurs

Les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> lèvent à la fois les exceptions système (comme <xref:System.ArgumentException>) et les exceptions spécifiques au web (qui sont des <xref:System.Net.WebException> levées par la méthode <xref:System.Net.WebRequest.GetResponse%2A>).  
  
Chaque **WebException** comprend une propriété <xref:System.Net.WebException.Status%2A> qui contient une valeur de l’énumération <xref:System.Net.WebExceptionStatus>. Vous pouvez examiner la propriété **Status** afin d’identifier l’erreur qui s’est produite et de prendre les mesures appropriées pour la résoudre.  
  
Le tableau suivant décrit les valeurs possibles pour la propriété **Status**.  
  
|Statut|Description|  
|------------|-----------------|  
|ConnectFailure|Le service distant n’a pas pu être contacté au niveau du transport.|  
|ConnectionClosed|La connexion a été interrompue prématurément.|  
|KeepAliveFailure|Le serveur a fermé une connexion établie avec l’en-tête Keep-alive défini.|  
|NameResolutionFailure|Le service de noms n’a pas pu résoudre le nom d’hôte.|  
|ProtocolError|La réponse reçue du serveur était complète, mais indiquait une erreur au niveau du protocole.|  
|ReceiveFailure|Aucune réponse complète n’a été reçue du serveur distant.|  
|RequestCanceled|La demande a été annulée.|  
|SecureChannelFailure|Une erreur s’est produite dans un lien de canal sécurisé.|  
|SendFailure|Une demande complète n’a pas pu être envoyée au serveur distant.|  
|ServerProtocolViolation|La réponse du serveur n’était pas une réponse HTTP valide.|  
|Succès|Aucune erreur n’a été rencontrée.|  
|Délai d'expiration|Aucune réponse n’a été reçue pendant le délai défini pour la demande.|  
|TrustFailure|Un certificat de serveur n’a pas pu être validé.|  
|MessageLengthLimitExceeded|Un message a été reçu qui dépassait la limite spécifiée lors de l’envoi d’une demande ou de la réception d’une réponse du serveur.|  
|Pending|Une demande asynchrone interne est en attente.|  
|PipelineFailure|Cette valeur prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement dans votre code.|  
|ProxyNameResolutionFailure|Le service de résolution de nom n’a pas pu résoudre le nom d’hôte proxy.|  
|UnknownError|Une exception de type inconnu s’est produite.|  
  
Quand la propriété **Status** a la valeur **WebExceptionStatus.ProtocolError**, une **WebResponse** qui contient la réponse du serveur est disponible. Vous pouvez examiner cette réponse afin de déterminer la source réelle de l’erreur de protocole.  
  
L’exemple suivant indique comment intercepter une **WebException**.  
  
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
  
Les applications qui utilisent la classe <xref:System.Net.Sockets.Socket> lèvent des <xref:System.Net.Sockets.SocketException> quand des erreurs se produisent sur le socket Windows. Les classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> et <xref:System.Net.Sockets.UdpClient> sont générées sur la classe **Socket** et lèvent également des **SocketExceptions**.  
  
Quand une **SocketException** est levée, la classe **SocketException** affecte à la propriété <xref:System.Net.Sockets.SocketException.ErrorCode%2A> la dernière erreur de socket du système d’exploitation s’étant produite. Pour plus d’informations sur les codes d’erreur de socket, consultez la documentation relative aux codes d’erreur des API Winsock 2.0 dans MSDN.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion et levée d’exceptions dans .NET](../../standard/exceptions/index.md)
- [Demande de données](requesting-data.md)
