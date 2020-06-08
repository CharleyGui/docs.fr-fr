---
title: 'Comment : envoyer des données à l’aide de la classe WebRequest'
description: Découvrez comment envoyer des données à un serveur à l’aide de la classe WebRequest dans le .NET Framework. Cette procédure est couramment utilisée pour envoyer des données vers une page Web.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502442"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="8b594-104">Comment : envoyer des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="8b594-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="8b594-105">La procédure suivante décrit les étapes nécessaires pour envoyer des données à un serveur.</span><span class="sxs-lookup"><span data-stu-id="8b594-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="8b594-106">Cette procédure est couramment utilisée pour publier des données sur une page web.</span><span class="sxs-lookup"><span data-stu-id="8b594-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="8b594-107">Pour envoyer des données à un serveur hôte</span><span class="sxs-lookup"><span data-stu-id="8b594-107">To send data to a host server</span></span>

1. <span data-ttu-id="8b594-108">Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> avec l’URI d’une ressource, comme un script ou une page ASP.NET, qui accepte des données.</span><span class="sxs-lookup"><span data-stu-id="8b594-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="8b594-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="8b594-110">Le .NET Framework fournit des classes spécifiques du protocole dérivées des classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> pour les URI qui commencent par *http:*, *https:*, *ftp:* et *file:*.</span><span class="sxs-lookup"><span data-stu-id="8b594-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="8b594-111">Si vous avez besoin de définir ou lire des propriétés spécifiques du protocole, vous devez caster votre objet <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> en type d’objet spécifique du protocole.</span><span class="sxs-lookup"><span data-stu-id="8b594-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="8b594-112">Pour plus d’informations, consultez [Programmation de protocoles enfichables](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="8b594-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="8b594-113">Définissez les valeurs des propriétés dont vous avez besoin dans votre objet `WebRequest`.</span><span class="sxs-lookup"><span data-stu-id="8b594-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="8b594-114">Par exemple, pour activer l’authentification, définissez la propriété <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> sur une instance de la classe <xref:System.Net.NetworkCredential> :</span><span class="sxs-lookup"><span data-stu-id="8b594-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="8b594-115">Spécifiez une méthode de protocole qui autorise l’envoi de données à l’aide d’une demande, comme la méthode `POST` HTTP :</span><span class="sxs-lookup"><span data-stu-id="8b594-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="8b594-116">Affectez à la propriété <xref:System.Web.HttpRequest.ContentLength> la valeur du nombre d’octets que vous insérez dans votre demande.</span><span class="sxs-lookup"><span data-stu-id="8b594-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="8b594-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="8b594-118">Affectez à la propriété <xref:System.Web.HttpRequest.ContentType> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="8b594-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="8b594-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="8b594-120">Obtenez le flux qui contient les données de la demande en appelant la méthode <xref:System.Net.WebRequest.GetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b594-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="8b594-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="8b594-122">Écrivez les données dans l’objet <xref:System.IO.Stream> retourné par la méthode `GetRequestStream`.</span><span class="sxs-lookup"><span data-stu-id="8b594-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="8b594-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="8b594-124">Fermez le flux de la demande en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b594-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b594-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="8b594-126">Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b594-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b594-127">Cette méthode retourne un objet contenant la réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="8b594-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="8b594-128">Le type de l’objet `WebResponse` retourné est déterminé par le schéma d’URI de la demande.</span><span class="sxs-lookup"><span data-stu-id="8b594-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="8b594-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="8b594-130">Vous pouvez accéder aux propriétés de votre objet `WebResponse` ou le caster en instance spécifique du protocole pour lire les propriétés propres au protocole.</span><span class="sxs-lookup"><span data-stu-id="8b594-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="8b594-131">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, castez votre objet `WebResponse` en référence <xref:System.Net.HttpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="8b594-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="8b594-132">L’exemple de code suivant montre comment afficher la propriété <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> propre à HTTP envoyée avec une réponse :</span><span class="sxs-lookup"><span data-stu-id="8b594-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="8b594-133">Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> de votre objet `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="8b594-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="8b594-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="8b594-135">Une fois que vous avez lu les données à partir de l’objet de réponse, fermez-le avec la méthode <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou fermez le flux de réponse avec la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b594-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b594-136">Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8b594-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="8b594-137">Étant donné que la méthode `WebResponse.Close` appelle `Stream.Close` quand elle ferme la réponse, il n’est pas nécessaire d’appeler `Close` sur les objets de réponse et de flux, même si cela ne porte pas à préjudice.</span><span class="sxs-lookup"><span data-stu-id="8b594-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="8b594-138">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b594-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="8b594-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b594-139">Example</span></span>

<span data-ttu-id="8b594-140">L’exemple suivant montre comment envoyer des données à un serveur web et lire les données dans sa réponse :</span><span class="sxs-lookup"><span data-stu-id="8b594-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="8b594-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b594-141">See also</span></span>

- [<span data-ttu-id="8b594-142">Création de requêtes Internet</span><span class="sxs-lookup"><span data-stu-id="8b594-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="8b594-143">Utilisation de flux sur le réseau</span><span class="sxs-lookup"><span data-stu-id="8b594-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="8b594-144">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="8b594-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="8b594-145">Demande de données</span><span class="sxs-lookup"><span data-stu-id="8b594-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="8b594-146">Comment : demander des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="8b594-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
