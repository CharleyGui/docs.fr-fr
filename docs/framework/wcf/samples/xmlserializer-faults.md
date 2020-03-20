---
title: Erreurs XmlSerializer
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: adb14fdb45aa71bbaf4585cbfba55059df7cddf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183152"
---
# <a name="xmlserializer-faults"></a>Erreurs XmlSerializer
L'exemple de contrat d'erreur <xref:System.Xml.Serialization.XmlSerializer> illustre comment transmettre les informations relatives à une erreur d'un service à un client à l'aide de <xref:System.Xml.Serialization.XmlSerializer>. L’échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), avec un certain code supplémentaire ajouté au service pour convertir une exception interne à un défaut. Le client tente d'effectuer une opération de division par zéro pour imposer la génération d'une erreur sur le service.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le contrat de calculatrice a été modifié afin d'y inclure un <xref:System.ServiceModel.FaultContractAttribute>, tel qu'illustré dans l'exemple de code suivant. En outre, <xref:System.ServiceModel.XmlSerializerFormatAttribute> est utilisé pour activer la sérialisation à l'aide de <xref:System.Xml.Serialization.XmlSerializer>. La propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> a la valeur `true` dans cet attribut, ce qui demande au sérialiseur d'utiliser <xref:System.Xml.Serialization.XmlSerializer> pour lire et écrire les erreurs.  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Lorsque vous généez du code pour le proxy client, vous devez appliquer le drapeau **/UseSerializerForFaults** à [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
