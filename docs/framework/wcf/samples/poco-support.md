---
title: Prise en charge POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183413"
---
# <a name="poco-support"></a>Prise en charge POCO
Cet exemple illustre la prise en charge de la sérialisation pour les types non marqués, c'est-à-dire les types auxquels aucun attribut de sérialisation n'a été appliqué. Ces types sont parfois appelés types POCO (Plain Old CLR Object). L’infère <xref:System.Runtime.Serialization.DataContractSerializer> un contrat de données pour tous les types publics non marqués qui ont un constructeur sans paramètres. Les contrats de données vous permettent de transférer des données structurées vers des services et à partir de ceux-ci. Pour plus d’informations sur les types non marqués, voir [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), mais utilise des nombres complexes au lieu de types numériques primitifs. Il est également similaire à l’échantillon <xref:System.Runtime.Serialization.DataContractAttribute> du <xref:System.Runtime.Serialization.DataMemberAttribute> contrat de données [de base,](../../../../docs/framework/wcf/samples/basic-data-contract.md) sauf que les attributs et les attributs ne sont pas utilisés.  
  
 Le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La classe `ComplexNumber` est utilisée dans `ServiceContract`. Le type `ComplexNumber` ne comporte pas les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>, comme indiqué dans l'exemple de code suivant. Par défaut, l'ensemble des propriétés et des champs publics sont sérialisés.  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md)
