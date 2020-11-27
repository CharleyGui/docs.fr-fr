---
title: 'Procédure : exposer un flux en tant que flux Atom et RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 1b03434e4f9552b714b40d54ba36c8468d0e2ccd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265360"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Procédure : exposer un flux en tant que flux Atom et RSS

Windows Communication Foundation (WCF) vous permet de créer un service qui expose un flux de syndication. Cette rubrique explique comment créer un service de syndication qui expose un flux de syndication à l'aide d'Atom 1.0 et de RSS 2.0. Ce service expose un point de terminaison qui peut retourner l'un ou l'autre format de syndication. Pour simplifier, le service utilisé dans cet exemple est auto-hébergé. Dans un environnement de production, un service de ce type est hébergé sous IIS ou WAS. Pour plus d’informations sur les différentes options d’hébergement WCF, consultez [hébergement](hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Pour créer un service de syndication de base  
  
1. Définissez un contrat de service utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>. Chaque opération exposée comme un flux de syndication retourne un objet <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Notez les paramètres de <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` spécifie l'URL utilisée pour appeler cette opération de service. La chaîne pour ce paramètre contient des littéraux et une variable entre accolades ({*format*}). Cette variable correspond au paramètre `format` de l'opération de service. Pour plus d’informations, consultez <xref:System.UriTemplate>. `BodyStyle` affecte la façon dont les messages que cette opération de service envoie et reçoit sont écrits. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> spécifie que les données envoyées vers et depuis cette opération de service ne sont pas renvoyées à la ligne par les éléments XML définis dans l'infrastructure. Pour plus d’informations, consultez <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > Utilisez <xref:System.ServiceModel.ServiceKnownTypeAttribute> pour spécifier les types retournés par les opérations de service dans cette interface.  
  
2. Implémentez le contrat de service.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. Créez un objet <xref:System.ServiceModel.Syndication.SyndicationFeed> et ajoutez un auteur, une catégorie et une description.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. Créez plusieurs objets <xref:System.ServiceModel.Syndication.SyndicationItem>.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. Ajoutez les objets <xref:System.ServiceModel.Syndication.SyndicationItem> au flux.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. Utilisez le paramètre de format pour retourner le format demandé.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Pour héberger le service  
  
1. Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>. La classe <xref:System.ServiceModel.Web.WebServiceHost> ajoute automatiquement un point de terminaison à l'adresse de base du service, sauf si un point est spécifié dans le code ou la configuration. Dans cet exemple, aucun point de terminaison n'est spécifié. De ce fait, c'est le point de terminaison par défaut qui est exposé.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. Ouvrez l'hôte de service, chargez le flux à partir du service, affichez le flux et attendez que l'utilisateur appuie sur ENTRÉE.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Pour appeler GetBlog avec un HTTP GET  
  
1. Ouvrez Internet Explorer, tapez l’URL suivante, puis appuyez sur entrée : `http://localhost:8000/BlogService/GetBlog` .
  
     L’URL contient l’adresse de base du service ( `http://localhost:8000/BlogService` ), l’adresse relative du point de terminaison et l’opération de service à appeler.  
  
### <a name="to-call-getblog-from-code"></a>Pour appeler GetBlog() à partir d'un code  
  
1. Créez un <xref:System.Xml.XmlReader> avec l'adresse de base et la méthode que vous appelez.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. Appelez la méthode <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statique, en passant dans le <xref:System.Xml.XmlReader> que vous venez de créer.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Cela appelle l'opération de service et remplit un nouvel objet <xref:System.ServiceModel.Syndication.SyndicationFeed> avec le module de formatage retourné à partir de l'opération de service.  
  
3. Accédez à l'objet de flux.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a> Exemple  

 Les éléments suivants représentent l'intégralité du code pour cet exemple.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Lors de la compilation du code précédent, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
