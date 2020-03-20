---
title: Requêtes asynchrones
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
ms.openlocfilehash: a49233596bafebd4f07372e59f29ea77afb21458
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180723"
---
# <a name="making-asynchronous-requests"></a><span data-ttu-id="81f74-102">Requêtes asynchrones</span><span class="sxs-lookup"><span data-stu-id="81f74-102">Making Asynchronous Requests</span></span>
<span data-ttu-id="81f74-103">Les classes <xref:System.Net> utilisent le modèle de programmation asynchrone standard du .NET Framework pour l’accès asynchrone à des ressources Internet.</span><span class="sxs-lookup"><span data-stu-id="81f74-103">The <xref:System.Net> classes use the .NET Framework's standard asynchronous programming model for asynchronous access to Internet resources.</span></span> <span data-ttu-id="81f74-104">Les méthodes <xref:System.Net.WebRequest.BeginGetResponse%2A> et <xref:System.Net.WebRequest.EndGetResponse%2A> de la classe <xref:System.Net.WebRequest> démarrent et terminent les demandes asynchrones pour une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="81f74-104">The <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods of the <xref:System.Net.WebRequest> class start and complete asynchronous requests for an Internet resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81f74-105">L’utilisation d’appels synchrones dans des méthodes de rappel asynchrone peut entraîner des performances fortement pénalisées.</span><span class="sxs-lookup"><span data-stu-id="81f74-105">Using synchronous calls in asynchronous callback methods can result in severe performance penalties.</span></span> <span data-ttu-id="81f74-106">Les demandes Internet effectuées avec **WebRequest** et ses descendants doivent utiliser <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> pour lire le flux retourné par la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81f74-106">Internet requests made with **WebRequest** and its descendants must use <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> to read the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="81f74-107">L’exemple de code suivant montre comment utiliser des appels asynchrones avec la classe **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="81f74-107">The following sample code demonstrates how to use asynchronous calls with the **WebRequest** class.</span></span> <span data-ttu-id="81f74-108">L’exemple est un programme de console qui prend un URI sur la ligne de commande, demande la ressource correspondant à l’URI, puis imprime les données sur la console quand elles sont reçues d’Internet.</span><span class="sxs-lookup"><span data-stu-id="81f74-108">The sample is a console program that takes a URI from the command line, requests the resource at the URI, and then prints data to the console as it is received from the Internet.</span></span>  
  
 <span data-ttu-id="81f74-109">Le programme définit deux classes pour sa propre utilisation, la classe **RequestState**, qui passe les données entre les appels asynchrones, et la classe **ClientGetAsync**, qui implémente la demande asynchrone faite à une ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="81f74-109">The program defines two classes for its own use, the **RequestState** class, which passes data across asynchronous calls, and the **ClientGetAsync** class, which implements the asynchronous request to an Internet resource.</span></span>  
  
 <span data-ttu-id="81f74-110">La classe **RequestState** conserve l’état de la demande entre les appels aux méthodes asynchrones qui traitent la demande.</span><span class="sxs-lookup"><span data-stu-id="81f74-110">The **RequestState** class preserves the state of the request across calls to the asynchronous methods that service the request.</span></span> <span data-ttu-id="81f74-111">Elle contient les instances de **WebRequest** et de <xref:System.IO.Stream> qui contiennent la demande en cours à la ressource et le flux reçu en réponse, une mémoire tampon qui contient les données actuellement reçues de la ressource Internet, et un <xref:System.Text.StringBuilder> qui contient la réponse complète.</span><span class="sxs-lookup"><span data-stu-id="81f74-111">It contains **WebRequest** and <xref:System.IO.Stream> instances that contain the current request to the resource and the stream received in response, a buffer that contains the data currently received from the Internet resource, and a <xref:System.Text.StringBuilder> that contains the complete response.</span></span> <span data-ttu-id="81f74-112">Un **RequestState** est passé comme paramètre *state* quand la méthode <xref:System.AsyncCallback> est inscrite auprès de **WebRequest.BeginGetResponse**.</span><span class="sxs-lookup"><span data-stu-id="81f74-112">A **RequestState** is passed as the *state* parameter when the <xref:System.AsyncCallback> method is registered with **WebRequest.BeginGetResponse**.</span></span>  
  
 <span data-ttu-id="81f74-113">La classe **ClientGetAsync** implémente une demande asynchrone à une ressource Internet et écrit la réponse résultante sur la console.</span><span class="sxs-lookup"><span data-stu-id="81f74-113">The **ClientGetAsync** class implements an asynchronous request to an Internet resource and writes the resulting response to the console.</span></span> <span data-ttu-id="81f74-114">Elle contient les méthodes et les propriétés décrites dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="81f74-114">It contains the methods and properties described in the following list.</span></span>  
  
- <span data-ttu-id="81f74-115">La propriété `allDone` contient une instance de la classe <xref:System.Threading.ManualResetEvent> qui signale la fin de la demande.</span><span class="sxs-lookup"><span data-stu-id="81f74-115">The `allDone` property contains an instance of the <xref:System.Threading.ManualResetEvent> class that signals the completion of the request.</span></span>  
  
- <span data-ttu-id="81f74-116">La méthode `Main()` lit la ligne de commande et démarre la demande pour la ressource Internet spécifiée.</span><span class="sxs-lookup"><span data-stu-id="81f74-116">The `Main()` method reads the command line and begins the request for the specified Internet resource.</span></span> <span data-ttu-id="81f74-117">Elle crée la **WebRequest** `wreq` et le **RequestState** `rs`, appelle **BeginGetResponse** pour commencer à traiter la demande, puis appelle la méthode `allDone.WaitOne()` afin que l’application ne quitte pas jusqu’à la fin du rappel.</span><span class="sxs-lookup"><span data-stu-id="81f74-117">It creates the **WebRequest** `wreq` and the **RequestState** `rs`, calls **BeginGetResponse** to begin processing the request, and then calls the `allDone.WaitOne()`method so that the application will not exit until the callback is complete.</span></span> <span data-ttu-id="81f74-118">Une fois que la réponse est lue à partir de la ressource Internet, `Main()` l’écrit sur la console et l’application se termine.</span><span class="sxs-lookup"><span data-stu-id="81f74-118">After the response is read from the Internet resource, `Main()` writes it to the console and the application ends.</span></span>  
  
- <span data-ttu-id="81f74-119">La méthode `showusage()` écrit un exemple de ligne de commande sur la console.</span><span class="sxs-lookup"><span data-stu-id="81f74-119">The `showusage()` method writes an example command line on the console.</span></span> <span data-ttu-id="81f74-120">Elle est appelée par `Main()` quand un URI n’est pas spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="81f74-120">It is called by `Main()` when no URI is provided on the command line.</span></span>  
  
- <span data-ttu-id="81f74-121">La méthode `RespCallBack()` implémente la méthode de rappel asynchrone pour la demande Internet.</span><span class="sxs-lookup"><span data-stu-id="81f74-121">The `RespCallBack()` method implements the asynchronous callback method for the Internet request.</span></span> <span data-ttu-id="81f74-122">Elle crée l’instance de **WebResponse** contenant la réponse de la ressource Internet, obtient le flux de réponse et démarre la lecture des données du flux en mode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="81f74-122">It creates the **WebResponse** instance containing the response from the Internet resource, gets the response stream, and then starts reading the data from the stream asynchronously.</span></span>  
  
- <span data-ttu-id="81f74-123">La méthode `ReadCallBack()` implémente la méthode de rappel asynchrone pour la lecture du flux de réponse.</span><span class="sxs-lookup"><span data-stu-id="81f74-123">The `ReadCallBack()` method implements the asynchronous callback method for reading the response stream.</span></span> <span data-ttu-id="81f74-124">Elle transfère les données reçues de la ressource Internet dans la propriété **ResponseData** de l’instance de **RequestState**, puis démarre une autre lecture asynchrone du flux de réponse jusqu’à ce qu’aucune donnée ne soit retournée.</span><span class="sxs-lookup"><span data-stu-id="81f74-124">It transfers data received from the Internet resource into the **ResponseData** property of the **RequestState** instance, then starts another asynchronous read of the response stream until no more data is returned.</span></span> <span data-ttu-id="81f74-125">Une fois que toutes les données ont été lues, `ReadCallBack()` ferme le flux de réponse et appelle la méthode `allDone.Set()` pour indiquer que la réponse complète est présente dans **ResponseData**.</span><span class="sxs-lookup"><span data-stu-id="81f74-125">Once all the data has been read, `ReadCallBack()` closes the response stream and calls the `allDone.Set()` method to indicate that the entire response is present in **ResponseData**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="81f74-126">Il est essentiel que tous les flux réseau soient fermés.</span><span class="sxs-lookup"><span data-stu-id="81f74-126">It is critical that all network streams are closed.</span></span> <span data-ttu-id="81f74-127">Si vous ne fermez pas chaque demande et chaque flux de réponse, votre application n’aura plus suffisamment de connexions au serveur pour traiter des demandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="81f74-127">If you do not close each request and response stream, your application will run out of connections to the server and be unable to process additional requests.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)
   {  
      if (args.Length < 1)
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));
  
         // Continue reading data until
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(
            rs.BufferRead, 0, BUFFER_SIZE,
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();
      }  
      return;  
   }
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the response stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)
  
         ' Append the recently read data to the RequestData stringbuilder
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="81f74-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81f74-128">See also</span></span>

- [<span data-ttu-id="81f74-129">Demande de données</span><span class="sxs-lookup"><span data-stu-id="81f74-129">Requesting Data</span></span>](requesting-data.md)
