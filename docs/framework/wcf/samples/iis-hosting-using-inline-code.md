---
title: IIS Hosting Using Inline Code
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 47d056e35b92654c8e47647c7273c5d69b37bd97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594645"
---
# <a name="iis-hosting-using-inline-code"></a>IIS Hosting Using Inline Code

Cet exemple montre comment implémenter un service hébergé par les services IIS (Internet Information Services), où le code de service est contenu en ligne dans un fichier .svc et est compilé à la demande. Le code de service peut également être implémenté directement dans les fichiers de code source localisés dans le répertoire de \App_Code de l'application, ou être compilé dans l'assembly déployé dans \bin. Cet exemple ne présente pas ces techniques.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

L’exemple présente un service standard qui implémente un contrat définissant un modèle de communication demande-réponse. Le service est hébergé dans IIS et le code de service est entièrement contenu dans le fichier Service.svc. Le service est activé par l'hôte et est compilé à la demande par le premier message envoyé au service. Aucune précompilation n'est nécessaire. Le service implémente un contrat `ICalculator` tel que défini dans le code suivant :

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

L'implémentation de service calcule et retourne le résultat approprié.

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Une fois la solution générée, exécutez Setup. bat pour configurer l’application ServiceModelSamples dans IIS 7,0. Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’application IIS 7,0.

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md). Pour obtenir un exemple de création d’une application cliente qui peut appeler ce service, consultez [procédure : créer un client](../how-to-create-a-wcf-client.md).

## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
