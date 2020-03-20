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
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Comment : Demander des données en utilisant la classe WebRequest

La procédure suivante décrit les étapes nécessaires pour demander une ressource, comme une page web ou un fichier, auprès d’un serveur. La ressource doit être identifiée par un URI.

## <a name="to-request-data-from-a-host-server"></a>Pour demander des données à partir d’un serveur hôte

1. Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> avec l’URI d’une ressource. Par exemple :

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Cette méthode retourne un objet contenant la réponse du serveur. Le type de l’objet <xref:System.Net.WebResponse> retourné est déterminé par le schéma d’URI de la demande. Par exemple :

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Vous pouvez accéder aux propriétés de votre objet `WebResponse` ou le caster en instance spécifique du protocole pour lire les propriétés propres au protocole.

    Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, castez votre objet `WebResponse` en référence `HttpWebResponse`. L’exemple de code suivant montre comment afficher la propriété <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> propre à HTTP envoyée avec une réponse :

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>. Par exemple :

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Une fois que vous avez lu les données à partir de l’objet de réponse, fermez-le avec la méthode <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou fermez le flux de réponse avec la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Si vous ne fermez pas l’objet de réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires. Étant donné que la méthode `WebResponse.Close` appelle `Stream.Close` quand elle ferme la réponse, il n’est pas nécessaire d’appeler `Close` sur les objets de réponse et de flux, même si cela ne porte pas à préjudice. Par exemple :

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a> Exemple

L’exemple de code suivant montre comment créer une demande auprès d’un serveur web et lire les données dans sa réponse :

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Voir aussi

- [Création de demandes sur Internet](creating-internet-requests.md)
- [Utilisation de streams sur le réseau](using-streams-on-the-network.md)
- [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)
- [Demande de données](requesting-data.md)
- [Comment : Envoyer des données en utilisant la classe WebRequest](how-to-send-data-using-the-webrequest-class.md)
