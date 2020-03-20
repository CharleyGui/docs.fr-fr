---
title: 'Comment : Demander des données en utilisant la classe WebRequest'
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048167"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="44c60-102">Comment : Demander des données en utilisant la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="44c60-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="44c60-103">La procédure suivante décrit les étapes nécessaires pour demander une ressource, comme une page web ou un fichier, auprès d’un serveur.</span><span class="sxs-lookup"><span data-stu-id="44c60-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="44c60-104">La ressource doit être identifiée par un URI.</span><span class="sxs-lookup"><span data-stu-id="44c60-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="44c60-105">Pour demander des données à partir d’un serveur hôte</span><span class="sxs-lookup"><span data-stu-id="44c60-105">To request data from a host server</span></span>

1. <span data-ttu-id="44c60-106">Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> avec l’URI d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="44c60-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="44c60-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="44c60-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="44c60-108">Le .NET Framework fournit des classes spécifiques du protocole dérivées des classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> pour les URI qui commencent par *http:*, *https:*, *ftp:* et *file:*.</span><span class="sxs-lookup"><span data-stu-id="44c60-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="44c60-109">Si vous avez besoin de définir ou lire des propriétés spécifiques du protocole, vous devez caster votre objet <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> en type d’objet spécifique du protocole.</span><span class="sxs-lookup"><span data-stu-id="44c60-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="44c60-110">Pour plus d’informations, consultez [Programmation de protocoles enfichables](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="44c60-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="44c60-111">Définissez les valeurs des propriétés dont vous avez besoin dans votre objet `WebRequest`.</span><span class="sxs-lookup"><span data-stu-id="44c60-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="44c60-112">Par exemple, pour activer l’authentification, définissez la propriété <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> sur une instance de la classe <xref:System.Net.NetworkCredential> :</span><span class="sxs-lookup"><span data-stu-id="44c60-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="44c60-113">Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44c60-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44c60-114">Cette méthode retourne un objet contenant la réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="44c60-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="44c60-115">Le type de l’objet <xref:System.Net.WebResponse> retourné est déterminé par le schéma d’URI de la demande.</span><span class="sxs-lookup"><span data-stu-id="44c60-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="44c60-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="44c60-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="44c60-117">Vous pouvez accéder aux propriétés de votre objet `WebResponse` ou le caster en instance spécifique du protocole pour lire les propriétés propres au protocole.</span><span class="sxs-lookup"><span data-stu-id="44c60-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="44c60-118">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, castez votre objet `WebResponse` en référence `HttpWebResponse`.</span><span class="sxs-lookup"><span data-stu-id="44c60-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="44c60-119">L’exemple de code suivant montre comment afficher la propriété <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> propre à HTTP envoyée avec une réponse :</span><span class="sxs-lookup"><span data-stu-id="44c60-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="44c60-120">Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44c60-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="44c60-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="44c60-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="44c60-122">Une fois que vous avez lu les données à partir de l’objet de réponse, fermez-le avec la méthode <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou fermez le flux de réponse avec la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44c60-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="44c60-123">Si vous ne fermez pas l’objet de réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="44c60-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="44c60-124">Étant donné que la méthode `WebResponse.Close` appelle `Stream.Close` quand elle ferme la réponse, il n’est pas nécessaire d’appeler `Close` sur les objets de réponse et de flux, même si cela ne porte pas à préjudice.</span><span class="sxs-lookup"><span data-stu-id="44c60-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="44c60-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="44c60-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="44c60-126"> Exemple</span><span class="sxs-lookup"><span data-stu-id="44c60-126">Example</span></span>

<span data-ttu-id="44c60-127">L’exemple de code suivant montre comment créer une demande auprès d’un serveur web et lire les données dans sa réponse :</span><span class="sxs-lookup"><span data-stu-id="44c60-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="44c60-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44c60-128">See also</span></span>

- [<span data-ttu-id="44c60-129">Création de demandes sur Internet</span><span class="sxs-lookup"><span data-stu-id="44c60-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="44c60-130">Utilisation de streams sur le réseau</span><span class="sxs-lookup"><span data-stu-id="44c60-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="44c60-131">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="44c60-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="44c60-132">Demande de données</span><span class="sxs-lookup"><span data-stu-id="44c60-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="44c60-133">Comment : Envoyer des données en utilisant la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="44c60-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
