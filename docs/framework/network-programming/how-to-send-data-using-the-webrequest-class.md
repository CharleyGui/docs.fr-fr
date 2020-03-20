---
title: 'Comment : Envoyer des données en utilisant la classe WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040830"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Comment : Envoyer des données en utilisant la classe WebRequest

La procédure suivante décrit les étapes nécessaires pour envoyer des données à un serveur. Cette procédure est couramment utilisée pour publier des données sur une page web.

## <a name="to-send-data-to-a-host-server"></a>Pour envoyer des données à un serveur hôte

1. Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> avec l’URI d’une ressource, comme un script ou une page ASP.NET, qui accepte des données. Par exemple :

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > Le .NET Framework fournit des classes spécifiques du protocole dérivées des classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> pour les URI qui commencent par *http:*, *https:*, *ftp:* et *file:*.

    Si vous avez besoin de définir ou lire des propriétés spécifiques du protocole, vous devez caster votre objet <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> en type d’objet spécifique du protocole. Pour plus d’informations, consultez [Programmation de protocoles enfichables](programming-pluggable-protocols.md).

2. Définissez les valeurs des propriétés dont vous avez besoin dans votre objet `WebRequest`. Par exemple, pour activer l’authentification, définissez la propriété <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> sur une instance de la classe <xref:System.Net.NetworkCredential> :

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Spécifiez une méthode de protocole qui autorise l’envoi de données à l’aide d’une demande, comme la méthode `POST` HTTP :

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Affectez à la propriété <xref:System.Web.HttpRequest.ContentLength> la valeur du nombre d’octets que vous insérez dans votre demande. Par exemple :

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. Affectez à la propriété <xref:System.Web.HttpRequest.ContentType> une valeur appropriée. Par exemple :

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Obtenez le flux qui contient les données de la demande en appelant la méthode <xref:System.Net.WebRequest.GetRequestStream%2A>. Par exemple :

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Écrivez les données dans l’objet <xref:System.IO.Stream> retourné par la méthode `GetRequestStream`. Par exemple :

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Fermez le flux de la demande en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Par exemple :

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Cette méthode retourne un objet contenant la réponse du serveur. Le type de l’objet `WebResponse` retourné est déterminé par le schéma d’URI de la demande. Par exemple :

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Vous pouvez accéder aux propriétés de votre objet `WebResponse` ou le caster en instance spécifique du protocole pour lire les propriétés propres au protocole.

    Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, castez votre objet `WebResponse` en référence <xref:System.Net.HttpWebResponse>. L’exemple de code suivant montre comment afficher la propriété <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> propre à HTTP envoyée avec une réponse :

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> de votre objet `WebResponse`. Par exemple :

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Une fois que vous avez lu les données à partir de l’objet de réponse, fermez-le avec la méthode <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou fermez le flux de réponse avec la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires. Étant donné que la méthode `WebResponse.Close` appelle `Stream.Close` quand elle ferme la réponse, il n’est pas nécessaire d’appeler `Close` sur les objets de réponse et de flux, même si cela ne porte pas à préjudice. Par exemple :

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a> Exemple

L’exemple suivant montre comment envoyer des données à un serveur web et lire les données dans sa réponse :

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Voir aussi

- [Création de demandes sur Internet](creating-internet-requests.md)
- [Utilisation de flux sur le réseau](using-streams-on-the-network.md)
- [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)
- [Demande de données](requesting-data.md)
- [Comment : Demander des données en utilisant la classe WebRequest](how-to-request-data-using-the-webrequest-class.md)
