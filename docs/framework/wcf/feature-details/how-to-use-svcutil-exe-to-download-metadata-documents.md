---
title: 'Procédure : utiliser Svcutil.exe pour télécharger des documents de métadonnées'
description: Découvrez comment utiliser Svcutil.exe pour télécharger des métadonnées à partir de services en cours d’exécution et les enregistrer dans des fichiers locaux.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 449dd3023b5d688ed0de22e3651cccf16bee0c52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280674"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Procédure : utiliser Svcutil.exe pour télécharger des documents de métadonnées

Svcutil.exe vous permet de télécharger des métadonnées à partir de systèmes en cours d'exécution et de les enregistrer dans des fichiers locaux. Pour les schémas d’URL HTTP et HTTPs, Svcutil.exe tente de récupérer des métadonnées à l’aide de WS-MetadataExchange et de la [découverte de service Web XML](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)). Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS-MetadataExchange.  
  
 Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Pour configurer la liaison utilisée pour WS-MetadataExchange, vous devez définir un point de terminaison client dans le fichier de configuration de Svcutil.exe (svcutil.exe.config) qui utilise le contrat `IMetadataExchange` et qui porte le même nom que le schéma d’URI (Uniform Resource Identifier) de l’adresse du point de terminaison des métadonnées.  
  
> [!CAUTION]
> Lors de l’exécution de Svcutil.exe pour obtenir les métadonnées d’un service qui expose deux contrats de service différents qui contiennent chacun une opération du même nom, Svcutil.exe affiche une erreur indiquant « impossible d’obtenir les métadonnées à partir de... ». Par exemple, si vous avez un service qui expose un contrat de service appelé `ICarService` qui a une opération `Get(Car c)` et le même service expose un contrat de service appelé `IBookService` qui a une opération `Get(Book b)` . Pour contourner ce problème, procédez comme suit :
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
  
 Pour plus d’options sur l’utilisation de cet outil pour le téléchargement de métadonnées, consultez [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a> Exemple  

 La commande suivante télécharge des documents de métadonnées à partir d'un service en cours d'exécution.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Voir aussi

- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
