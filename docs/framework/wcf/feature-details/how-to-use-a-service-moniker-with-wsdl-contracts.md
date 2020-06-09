---
title: 'Comment : utiliser un moniker de service avec des contrats WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70d7e9ff45616f832597ebc48db00198967935c6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601138"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Comment : utiliser un moniker de service avec des contrats WSDL
Dans certains cas, vous pouvez avoir besoin d'un client COM Interop entièrement autonome. Le service que vous souhaitez appeler peut ne pas exposer de point de terminaison MEX et la DLL du client WCF risque de ne pas être enregistrée pour COM Interop. Le cas échéant, vous pouvez créer un fichier WSDL qui décrit le service et le transmet au moniker de service WCF. Cette rubrique décrit la manière d'appeler l'exemple de mise en route WCF à l'aide d'un moniker WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Utilisation du moniker de service WSDL  
  
1. Ouvrez et créez l'exemple de solution de mise en route.  
  
2. Ouvrez Internet Explorer et accédez à `http://localhost/ServiceModelSamples/Service.svc` pour vous assurer que le service fonctionne.  
  
3. Dans le fichier Service.cs, ajoutez l'attribut suivant sur la classe CalculatorService :  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Ajoutez un espace de noms de liaison au service App.config :  

5. Créez un fichier WSDL pour que l'application le lise. Étant donné que les espaces de noms ont été ajoutés aux étapes 3 et 4, vous pouvez utiliser IE pour Rechercher l’intégralité de la description WSDL du service en accédant à `http://localhost/ServiceModelSamples/Service.svc?wsdl` . Vous pouvez ensuite enregistrer le fichier à partir d'Internet Explorer en tant que serviceWSDL.xml. Si vous ne spécifiez pas les espaces de noms lors des étapes 3 et 4, le document WSDL renvoyé à l'issue de l'interrogation de l'URL ci-dessus ne sera pas le document WSDL complet. Le document WSDL renvoyé inclura plusieurs instructions import qui permettent d'importer d'autres documents WSDL. Vous devrez parcourir chaque instruction import et générer le document WSDL complet, en associant le WSDL renvoyé par le service avec le WSDL importé.  
  
6. Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard. Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > Si le moniker est mal formé ou si le service n'est pas disponible, l'appel de `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.  Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
7. Exécutez l'application Visual Basic. Un message s'affiche avec les résultats de l'appel de Subtract(145, 76.54).  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](../samples/getting-started-sample.md)
- [Vue d'ensemble de l'intégration à des applications COM](integrating-with-com-applications-overview.md)
