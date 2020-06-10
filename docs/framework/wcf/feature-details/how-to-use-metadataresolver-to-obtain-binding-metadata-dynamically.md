---
title: 'Comment : utiliser MetadataResolver pour obtenir des métadonnées de liaison dynamiquement'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 98fe4977f270b008c51039af19261ca86b8d6642
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601125"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Comment : utiliser MetadataResolver pour obtenir des métadonnées de liaison dynamiquement
Cette rubrique indique comment utiliser la classe <xref:System.ServiceModel.Description.MetadataResolver> pour obtenir des métadonnées de liaison dynamiquement.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Pour obtenir des métadonnées de liaison dynamiquement  
  
1. Créez un objet <xref:System.ServiceModel.EndpointAddress> avec l'adresse du point de terminaison de métadonnées.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Appelez <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, qui passe le type de service et l'adresse du point de terminaison de métadonnées. Une collection de points de terminaison qui implémentent le contrat spécifié est alors retournée. Seules les informations de liaison sont importées à partir des métadonnées, les informations de contrat ne le sont pas. Le contrat fourni est utilisé à la place.  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Vous pouvez ensuite itérer au sein de la collection de points de terminaison de service afin d'extraire les informations de liaison dont vous avez besoin. Le code suivant itère au sein des points de terminaison, crée un objet client de service qui passe la liaison et l’adresse associée au point de terminaison actuel, puis appelle une méthode sur le service.  
  
    ```csharp  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées](metadata.md)
