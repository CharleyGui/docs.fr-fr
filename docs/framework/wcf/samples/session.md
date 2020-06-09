---
title: Session
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 283c8b9641dcce8b0207d3be0024b57369d125ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591447"
---
# <a name="session"></a>Session
L'exemple Session montre comment implémenter un contrat qui requiert une session. Une session fournit le contexte pour effectuer plusieurs opérations. Cela permet à un service d'associer l'état à une session donnée ; ainsi les opérations suivantes peuvent utiliser l'état d'une opération précédente. Cet exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente un service de calculatrice. Le contrat `ICalculator` a été modifié afin de permettre l'exécution d'un ensemble d'opérations arithmétiques, tout en conservant un résultat en cours. Cette fonctionnalité est définie par le contrat `ICalculatorSession`. Le service maintient l'état pou un client tandis que plusieurs opérations de service sont appelées pour effectuer un calcul. Le client peut récupérer le résultat actuel en appelant `Result()` et remettre le résultat à zéro en appelant `Clear()`.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fait de définir le mode <xref:System.ServiceModel.SessionMode> pour  le contrat `Required` garantit que lorsque le contrat est exposé sur une liaison particulière, la liaison prend en charge les sessions. Si la liaison ne prend pas en charge les sessions, une exception est levée. L'interface `ICalculatorSession` est définie de telle sorte qu'une ou plusieurs opérations puissent être appelées, ce qui modifie le résultat en cours, comme le montre l'exemple de code suivant.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Le service utilise le <xref:System.ServiceModel.InstanceContextMode><xref:System.ServiceModel.InstanceContextMode.PerSession> pour lier un contexte d'instance de service donné à chaque session entrante. Cela permet au service de maintenir le résultat en cours pour chaque session dans une variable membre locale.  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 Lorsque vous exécutez l'exemple, le client fait plusieurs demandes au serveur et demande le résultat, qu'il affiche ensuite dans la fenêtre de console cliente. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
