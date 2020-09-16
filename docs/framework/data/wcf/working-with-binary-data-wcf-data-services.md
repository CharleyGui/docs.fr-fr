---
title: Utilisation de données binaires (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 3c391e641df52d9143630406a40e17c6bc853865
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551749"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Utilisation de données binaires (services de données WCF)

La bibliothèque cliente WCF Data Services vous permet de récupérer et de mettre à jour des données binaires à partir d’un flux Open Data Protocol (OData) de l’une des manières suivantes :

- Comme une propriété de type primitif d'entité. Il s'agit de la méthode conseillée lors de l'utilisation de petits objets de données binaires, faciles à charger en mémoire. Dans ce cas, la propriété binaire est une propriété d'entité exposée par le modèle de données, et le service de données sérialise les données binaires sous forme de XML binaire encodé Base 64 dans le message de réponse.

- Comme un flux distinct de ressources binaires. Ceci est la méthode conseillée pour l'accès et la modification de données d'objet BLOB (binary large object) qui peuvent représenter des photos, des vidéos ou tout autre type de données binaires encodées.

WCF Data Services implémente la diffusion en continu de données binaires à l’aide du protocole HTTP, tel que défini dans OData. Dans ce mécanisme, les données binaires sont traitées comme une ressource multimédia distincte mais liée à une entité, appelée une entrée de lien média. Pour plus d’informations, consultez la page [fournisseur de streaming](streaming-provider-wcf-data-services.md).

> [!TIP]
> Pour obtenir un exemple pas à pas de création d’une application cliente Windows Presentation Foundation (WPF) qui télécharge des fichiers image binaires à partir d’un service OData qui stocke des photos, consultez la série publication d’un [fournisseur de diffusion en continu Data Services, partie 2 : accès à un flux de ressources multimédia à partir du client](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Pour télécharger l’exemple de code pour le service Stream Photo service dans le billet de blog, consultez l' [exemple streaming photo service](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) dans github.

## <a name="entity-metadata"></a>Métadonnées d'entité

Une entité qui possède un flux de ressources multimédia lié est signalée dans les métadonnées du service de données par l'attribut `HasStream` appliqué à un type d'entité qui est l'entrée de lien média. Dans l’exemple suivant, l' `PhotoInfo` entité est une entrée de lien média qui a une ressource multimédia associée, indiquée par l' `HasStream` attribut.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Les autres exemples de cette rubrique indiquent comment accéder et modifier le flux de ressources multimédia. Pour obtenir un exemple complet de consommation d’un flux de ressources multimédia dans une application cliente .NET Framework à l’aide de la WCF Data Services bibliothèque cliente, consultez la publication [accès à un flux de ressources multimédia à partir du client](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client).

## <a name="accessing-the-binary-resource-stream"></a>Accès au flux de ressources binaires

La bibliothèque cliente WCF Data Services fournit des méthodes permettant d’accéder aux flux de ressources binaires à partir d’un service de données basé sur OData. Lors du téléchargement d'une ressource multimédia, vous pouvez utiliser l'URI de la ressource multimédia ou bien vous pouvez obtenir un flux binaire qui contient les données de la ressource multimédia elle-même. Vous pouvez également télécharger les données de la ressource multimédia sous la forme d'un flux binaire.

> [!TIP]
> Pour obtenir un exemple pas à pas de création d’une application cliente Windows Presentation Foundation (WPF) qui télécharge des fichiers image binaires à partir d’un service OData qui stocke des photos, consultez la série publication d’un [fournisseur de diffusion en continu Data Services, partie 2 : accès à un flux de ressources multimédia à partir du client](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Pour télécharger l’exemple de code pour le service Stream Photo service dans le billet de blog, consultez l' [exemple streaming photo service](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) dans github.

### <a name="getting-the-uri-of-the-binary-stream"></a>Obtenir l'URI du flux binaire

Lorsque vous récupérez certains types de ressources multimédia, tels que des images et d'autres fichiers multimédia, il est souvent plus facile d'utiliser l'URI de la ressource média de votre application que le flux de données binaires lui-même. Pour obtenir l'URI d'un flux de ressources associé à une entrée de lien média donnée, vous devez appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui suit l'entité. L'exemple suivant illustre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> pour obtenir l'URI d'un flux de ressources multimédia utilisé pour créer une nouvelle image sur le client :

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Téléchargement d'un flux de ressources binaires

Lorsque vous récupérez un flux de ressources binaires, vous devez appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui effectue le suivi de l'entrée de lien média. Cette méthode envoie une demande au service de données qui retourne un objet <xref:System.Data.Services.Client.DataServiceStreamResponse>, lequel possède une référence au flux de données qui contient la ressource. Utilisez cette méthode lorsque votre application nécessite que la ressource binaire soit un <xref:System.IO.Stream>. L'exemple suivant illustre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> pour récupérer un flux utilisé pour créer une nouvelle image sur le client :

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> L'en-tête Content-Length du message de réponse qui contient le flux binaire en continu n'est pas défini par le service de données. Cette valeur ne peut pas refléter la longueur réelle du flux de données binaires en continu.

### <a name="uploading-a-media-resource-as-a-stream"></a>Téléchargement d'une ressource multimédia comme un flux

Pour insérer ou mettre à jour une ressource multimédia, appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui effectue le suivi de l'entité. Cette méthode envoie une demande au service de données qui contient la ressource multimédia lue depuis le flux de données fourni. L'exemple suivant indique comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> pour envoyer une image au service de données :

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

Dans cet exemple, la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> est appelée en fournissant une valeur `true` pour le paramètre `closeStream`. Cela garantit que l'objet <xref:System.Data.Services.Client.DataServiceContext> ferme le flux de données une fois les données binaires téléchargées sur le service de données.

> [!NOTE]
> Lorsque vous appelez <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, le flux n'est pas transmis au service de données jusqu'à ce que la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> soit appelée.

## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
- [Liaison de données à des contrôles](binding-data-to-controls-wcf-data-services.md)
