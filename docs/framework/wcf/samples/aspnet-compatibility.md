---
title: ASP.NET Compatibility
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 23930e0756d3fbefc28a8f650b5a056106145a50
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594710"
---
# <a name="aspnet-compatibility"></a>ASP.NET Compatibility

Cet exemple montre comment activer le mode de compatibilité ASP.NET dans Windows Communication Foundation (WCF). Les services qui s’exécutent en mode de compatibilité ASP.NET participent pleinement au pipeline d’application ASP.NET et peuvent utiliser des fonctionnalités ASP.NET telles que l’autorisation de fichier/d’URL, l’état de session et la <xref:System.Web.HttpContext> classe. La <xref:System.Web.HttpContext> classe autorise l’accès aux cookies, aux sessions et à d’autres fonctionnalités ASP.net. Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.

Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS 

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.

Cet exemple nécessite un pool d’applications .NET Framework 4 pour pouvoir s’exécuter. Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.

1. Ouvrez le **Panneau de configuration**.  Ouvrez l’applet **Outils d’administration** sous le titre **système et sécurité** . Ouvrez l’applet du **Gestionnaire de Internet Information Services (IIS)** .

2. Développez l’arborescence dans le volet **connexions** . Sélectionnez le nœud **pools d’applications** .

3. Pour définir le pool d’applications par défaut de sorte qu’il utilise .NET Framework 4 (ce qui peut entraîner des problèmes d’incompatibilité avec les sites existants), cliquez avec le bouton droit sur l’élément de liste **DefaultAppPool** et sélectionnez **paramètres de base...**. Définissez la liste déroulante **version du .NET Framework** sur **.NET Framework v 4.0.30128** (ou version ultérieure).

4. Pour créer un nouveau pool d’applications qui utilise .NET Framework 4 (pour préserver la compatibilité pour d’autres applications), cliquez avec le bouton droit sur le nœud **pools d’applications** , puis sélectionnez **Ajouter un pool d’applications...**. Nommez le nouveau pool d’applications, puis définissez la liste déroulante **version du .NET Framework** sur **.NET Framework v 4.0.30128** (ou version ultérieure). Après avoir exécuté les étapes de configuration ci-dessous, cliquez avec le bouton droit sur l’application **servicemodelsamples** , puis sélectionnez **gérer l’application**, **Paramètres avancés...**. Définissez le **pool d’applications** sur le nouveau pool d’applications.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

Cet exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente un service de calculatrice. Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.

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

Le service utilise la session ASP.NET pour stocker le résultat de chaque session cliente. Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.

> [!NOTE]
> L’état de session ASP.NET et les sessions WCF sont très différents. Pour plus d’informations sur les sessions WCF, consultez [session](session.md) .

Le service a une dépendance intime sur l’état de session ASP.NET et nécessite le mode de compatibilité ASP.NET pour fonctionner correctement. Ces exigences sont définies de manière déclarative en appliquant l’attribut `AspNetCompatibilityRequirements`.

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

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Une fois la solution générée, exécutez Setup. bat pour configurer l’application ServiceModelSamples dans IIS 7,0. Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’application IIS 7,0.

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
