---
title: ASP.NET Compatibility
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 01329769b74c8a5841b5a2024d3ed674c108be1c
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487670"
---
# <a name="aspnet-compatibility"></a>ASP.NET Compatibility
Cet exemple montre comment activer le mode de compatibilité ASP.NET dans Windows Communication Foundation (WCF). Utilisent des services qui s’exécutent dans la compatibilité ASP.NET participent pleinement le pipeline d’application ASP.NET de mode et peut rendre des fonctionnalités ASP.NET telles que l’autorisation de fichier/URL, l’état de session et le <xref:System.Web.HttpContext> classe. Le <xref:System.Web.HttpContext> classe permet d’accéder aux cookies, les sessions et les autres fonctionnalités ASP.NET. Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.  
  
 Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
Cet exemple requiert pour fonctionner un pool d'applications [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.  

1. Ouvrez le **Panneau de configuration**.  Ouvrez le **outils d’administration** applet sous le **système et sécurité** titre. Ouvrez le **Internet Information Services (IIS) Manager** applet.  

2. Développez l’arborescence dans le **connexions** volet. Sélectionnez le **Pools d’applications** nœud.  

3. Pour définir le pool d’applications par défaut à utiliser [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (ce qui peut provoquer des problèmes d’incompatibilité avec des sites existants), avec le bouton droit le **DefaultAppPool** élément de liste et sélectionnez **paramètres de base...** . Définir le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).  

4. Pour créer un nouveau pool d’applications qui utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pour préserver la compatibilité avec d’autres applications), avec le bouton droit le **Pools d’applications** nœud et sélectionnez **ajouter un Pool d’applications...** . Nommez le nouveau pool d’applications et définissez le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure). Une fois que le programme d’installation en cours d’exécution les étapes ci-dessous, cliquez sur le **ServiceModelSamples** application et sélectionnez **gérer l’Application**, **paramètres avancés...** . Définir le **Pool d’applications** au nouveau pool d’applications.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente un service de calculatrice. Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Le service conserve l’état de chaque client (à l’aide de la fonctionnalité correspondante) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul. Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.  
  
 Le service utilise la session ASP.NET pour stocker le résultat pour chaque session client. Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.  
  
> [!NOTE]
> État de session ASP.NET et des sessions WCF sont des aspects très différents. Consultez [Session](../../../../docs/framework/wcf/samples/session.md) pour plus d’informations sur les sessions de WCF.
  
 Le service a une dépendance approfondie sur l’état de session ASP.NET et nécessite le mode de compatibilité ASP.NET pour fonctionner correctement. Ces exigences sont définies de manière déclarative en appliquant l’attribut `AspNetCompatibilityRequirements`.  
  
```csharp  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Une fois la solution a été créée, exécutez Setup.bat pour installer l’Application ServiceModelSamples dans IIS 7.0. Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’Application IIS 7.0.  
  
4. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://go.microsoft.com/fwlink/?LinkId=193961)
