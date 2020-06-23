---
title: 'Procédure : créer un service Web HTTP WCF de base'
description: Découvrez comment créer un service qui expose un point de terminaison Web dans WCF. Les points de terminaison Web envoient des données à l’aide de XML ou JSON. Il n’existe aucune enveloppe SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247102"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Procédure : créer un service Web HTTP WCF de base

Windows Communication Foundation (WCF) vous permet de créer un service qui expose un point de terminaison Web. Les points de terminaison Web envoient des données par XML ou JSON, il n'y a aucune enveloppe SOAP. Cette rubrique explique comment exposer un tel point de terminaison.

> [!NOTE]
> La seule méthode pour sécuriser un point de terminaison Web est de l'exposer à travers HTTPS, à l'aide de la sécurité de transport. Lors de l'utilisation de la sécurité basée sur message, les informations de sécurité sont placées habituellement dans les en-têtes SOAP, et comme les messages envoyés aux points de terminaison non-SOAP ne contiennent aucune enveloppe SOAP, on ne peut placer les informations de sécurité nulle part et vous devez compter sur la sécurité de transport.

## <a name="to-create-a-web-endpoint"></a>Pour créer un point de terminaison Web

1. Définissez un contrat de service à l'aide d'une interface marquée avec les attributs <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> et <xref:System.ServiceModel.Web.WebGetAttribute>.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Par défaut, <xref:System.ServiceModel.Web.WebInvokeAttribute> mappe des appels POST à l'opération. Vous pouvez, toutefois, spécifier la méthode HTTP (par exemple, HEAD, PUT ou DELETE) pour le mappage à l'opération en spécifiant un paramètre « method= ». <xref:System.ServiceModel.Web.WebGetAttribute> n'a pas de paramètre « method= » et mappe uniquement des appels GET à l'opération de service.

2. Implémentez le contrat de service.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Pour héberger le service

1. Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.Description.WebHttpBehavior>.

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Si vous n'ajoutez pas de point de terminaison, <xref:System.ServiceModel.Web.WebServiceHost> crée automatiquement un point de terminaison par défaut. <xref:System.ServiceModel.Web.WebServiceHost> ajoute également <xref:System.ServiceModel.Description.WebHttpBehavior> et désactive la page d'aide HTTP et la fonctionnalité WSDL (Web Services Description Language) GET afin que le point de terminaison des métadonnées n'interfère pas avec le point de terminaison HTTP par défaut.
    >
    >  Ajouter un point de terminaison non-SOAP avec une URL "" provoque un comportement inattendu en cas de tentative d'appeler une opération sur le point de terminaison. Cela est dû au fait que l’URI d’écoute du point de terminaison est identique à l’URI de la page d’aide (la page qui s’affiche lorsque vous accédez à l’adresse de base d’un service WCF).

     Vous pouvez recourir à l'une des actions suivantes pour l'empêcher :

    - Spécifiez toujours un URI non vierge pour un point de terminaison non-SOAP.

    - Désactivez la page d'aide. Pour ce faire, vous pouvez utiliser le code suivant :

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Ouvrez l'hôte de service et attendez jusqu'à ce que l'utilisateur appuie sur ENTRÉE.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Cet exemple montre comment héberger un service de style Web avec une application console. Vous pouvez également héberger un tel service dans IIS. Pour cela, spécifiez la classe <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans un fichier .svc, comme indiqué dans le code suivant.

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Pour appeler des opérations de service mappées à GET dans Internet Explorer

1. Ouvrez Internet Explorer et tapez « `http://localhost:8000/EchoWithGet?s=Hello, world!` », puis appuyez sur entrée. L’URL contient l’adresse de base du service ( `http://localhost:8000/` ), l’adresse relative du point de terminaison (« »), l’opération de service à appeler («EchoWithGet ») et un point d’interrogation suivi d’une liste de paramètres nommés séparés par une esperluette (&).

## <a name="to-call-service-operations-in-code"></a>Pour appeler des opérations de service dans le code

1. Créez une instance de <xref:System.ServiceModel.ChannelFactory%601> dans un bloc `using`.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Ajoutez <xref:System.ServiceModel.Description.WebHttpBehavior> au point de terminaison appelé par le <xref:System.ServiceModel.ChannelFactory%601>.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Créez le canal et appelez le service.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Fermez le <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Exemple

Les éléments suivants représentent l'intégralité du code pour cet exemple.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Compilation du code

Lors de la compilation de Service.cs, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Modèle de programmation HTTP Web WCF](wcf-web-http-programming-model.md)
