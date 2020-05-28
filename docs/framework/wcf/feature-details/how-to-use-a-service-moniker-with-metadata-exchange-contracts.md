---
title: "Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées"
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 8894fdc4fd085b9d55a8fc25043e5258c306024c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143476"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées
Après avoir développé de nouveaux services WCF, vous pouvez décider que vous souhaitez être en mesure d’appeler ces services à partir d’un script ou d’une application Visual Basic 6,0. Une méthode consisterait à générer un assembly client WCF, à inscrire l’assembly auprès de COM, à installer l’assembly dans le GAC, puis à référencer les types COM à partir de votre code Visual Basic. Lorsque vous distribuez l’application, vous devez également distribuer l’assembly client WCF. L'utilisateur devra ensuite inscrire l'assembly client WCF avec COM et le placer dans le GAC. L’interopérabilité COM WCF vous permet également d’effectuer les mêmes appels de service sans compter sur un assembly client WCF. Le moniker WCF vous permet d’appeler n’importe quel service WCF à partir de n’importe quel langage compatible COM (Visual Basic, VBScript, Visual Basic pour Applications (VBA), etc.) en spécifiant un URI de point de terminaison MEX (Metadata Exchange) utilisé par le moniker de service pour extraire les informations de type relatives au service. Cette rubrique explique comment appeler l’exemple WCF Prise en main à l’aide d’un moniker WCF qui spécifie un point de terminaison MEX.  
  
> [!NOTE]
> Les types définis par l’assembly client WCF ne sont jamais instanciés en fait. L'assembly est utilisé uniquement pour les métadonnées.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Utilisation du moniker de service avec une adresse Mex  
  
1. Générez l’exemple de Prise en main et utilisez Internet Explorer pour accéder à son URL ( `http://localhost/ServiceModelSamples/Service.svc` ) afin de vérifier que le service fonctionne.  
  
2. Créez un script Visual Basic ou une application Visual Basic qui contient le code suivant :  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Exécutez l'application ou le script Visual Basic.  
  
    > [!NOTE]
    > Le service que vous appelez doit exposer un point de terminaison Mex pour que le moniker soit en mesure de lire les métadonnées du service. Pour plus d’informations, consultez [Comment : publier des métadonnées pour un service à l’aide d’un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    > Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.  Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : utiliser le moniker de service Windows Communication Foundation sans inscription](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Comment : utiliser un moniker de service avec des contrats WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
