---
title: 'Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596927"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées
Svcutil.exe vous permet de télécharger des métadonnées à partir de systèmes en cours d'exécution et de les enregistrer dans des fichiers locaux. Pour les schémas d’URL HTTP et HTTPs, Svcutil. exe tente de récupérer les métadonnées à l’aide de WS-MetadataExchange et de la [découverte de service Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)). Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS-MetadataExchange.  
  
 Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Pour configurer la liaison utilisée pour WS-MetadataExchange, vous devez définir un point de terminaison client dans le fichier de configuration de Svcutil.exe (svcutil.exe.config) qui utilise le contrat `IMetadataExchange` et qui porte le même nom que le schéma d’URI (Uniform Resource Identifier) de l’adresse du point de terminaison des métadonnées.  
  
> [!CAUTION]
> Lors de l’exécution de Svcutil. exe pour obtenir les métadonnées d’un service qui expose deux contrats de service différents qui contiennent chacun une opération du même nom, Svcutil. exe affiche une erreur indiquant « impossible d’obtenir les métadonnées à partir de... ». Par exemple, si vous avez un service qui expose un contrat de service appelé `ICarService` qui a une opération `Get(Car c)` et le même service expose un contrat de service appelé `IBookService` qui a une opération `Get(Book b)` . Pour contourner ce problème, procédez comme suit :
>
> - Renommez l'une des opérations.
> - Affectez au <xref:System.ServiceModel.OperationContractAttribute.Name%2A> un nom différent.
> - Affectez à l'un des espaces de noms des opérations un espace de noms différent à l'aide de la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Pour télécharger les métadonnées à l'aide de Svcutil.exe  
  
1. Localisez l'outil Svcutil.exe à l'emplacement suivant :  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. À l'invite de commandes, lancez l'outil en utilisant le format suivant.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Vous devez spécifier l'option `/t:metadata` pour télécharger les métadonnées. Sinon, la configuration et le code client seront générés.  
  
3. L' `url` argument <>spécifie l’URL d’un point de terminaison de service qui fournit des métadonnées ou à un document de métadonnées hébergé en ligne. L' `epr` argument <> spécifie le chemin d’accès à un fichier XML qui contient un WS-Addressing `EndpointAddress` pour un point de terminaison de service qui prend en charge WS-MetadataExchange.  
  
 Pour plus d’options sur l’utilisation de cet outil pour le téléchargement de métadonnées, consultez [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Exemple  
 La commande suivante télécharge des documents de métadonnées à partir d'un service en cours d'exécution.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Voir aussi

- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
