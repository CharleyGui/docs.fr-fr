---
title: Activité de stratégie externalisée dans .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: efc8b8169a6b984e003444c4669122ce6fa7f9d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283167"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Activité de stratégie externalisée dans .NET Framework 4.5

Cet exemple montre comment l’activité ExternalizedPolicy4 permet d’exécuter des objets <xref:System.Workflow.Activities.Rules.RuleSet> .NET Framework 3,5 Windows Workflow Foundation (WF 3,5) existants dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation (WF 4,5) directement à l’aide du moteur de règles fourni dans WF 3,5. À l'aide de cette activité, vous pouvez ouvrir et exécuter n'importe quel <xref:System.Workflow.Activities.Rules.RuleSet> WF 3.5 existant. Pour plus d’informations sur le moteur de règles WF 3,5 inclus dans le cadre de Windows Workflow Foundation, consultez [la présentation du moteur de règles Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=166079). Pour plus d’informations sur la migration de règles vers [!INCLUDE[wf1](../../../../includes/wf1-md.md)] dans [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], consultez les [conseils de migration](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projets dans cet exemple

|Nom du projet|Description|Fichiers principaux|
|-|-|-|
|ExternalizedPolicy4|Contient l'activité ExternalizedPolicy4 et son concepteur WF 4.5.|**ExternalizedPolicy4.cs**: définition de l’activité.<br /><br /> **ExternalizedPolicy4Designer. Xaml**: concepteur personnalisé pour l’activité ExternalizedPolicy4. Il utilise l'éditeur de Règles (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) du moteur de règles WF 3.5.|
|ImperativeCodeClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application ExternalizedPolicy4 utilisant du code C# impératif (aucun concepteur utilisé).|**ApplyDiscount. Rules**: fichier avec [!INCLUDE[wf1](../../../../includes/wf1-md.md)] définitions de règles.<br /><br /> **Order.cs**: type qui représente une commande client. Les règles sont appliquées aux objets de ce type.<br /><br /> **Program.cs**: configure et exécute un workflow qui a une activité Policy4 pour appliquer des règles définies dans ApplyDiscount. Rules aux instances d’objets de commande.<br /><br /> App.config : fichier de configuration avec le chemin d’accès du fichier de règles.|
|DesignerClientSample|Exemple d'application cliente qui configure et exécute un workflow à l'aide d'une application ExternalPolicy4 dans le concepteur [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1. Xaml**: workflow séquentiel qui utilise une activité Policy4 pour effectuer des évaluations de règles.<br /><br /> **Program.cs**: exécute une instance du workflow définie dans Sequence1. Xaml.|

## <a name="the-externalizedpolicy4-activity"></a>Activité ExternalizedPolicy4

L'activité ExternalizedPolicy4 est un <xref:System.Activities.NativeActivity> qui permet l'exécution d'objets <xref:System.Workflow.Activities.Rules.RuleSet> WF 3.5 dans des workflows WF 4.5. L'exemple suivant est une définition simplifiée du modèle d'objet public de l'activité.

```csharp
public class ExternalizedPolicy4Activity<TResult>: CodeActivity
{
    public string RulesFilePath

    public string RuleSetName

    [RequiredArgument]
    public InArgument<T> TargetObject

    [RequiredArgument]
    public OutArgument<T> ResultObject

    public OutArgument<ValidationErrorCollection> ValidationErrors
}
```

|Propriété|Description|
|-|-|
|RuleSetFilePath|Chemin d’accès au fichier <xref:System.Workflow.Activities.Rules.RuleSet> de .NET Framework 3.5 à évaluer lorsque l’activité est exécutée.|
|RuleSetName|Nom du <xref:System.Workflow.Activities.Rules.RuleSet> à utiliser dans le fichier .rules.|
|TargetObject|Objet sur lequel les objets <xref:System.Workflow.Activities.Rules.Rule> de <xref:System.Workflow.Activities.Rules.RuleSet> sont évalués.|
|ResultObject|Objet qui en résulte une fois les règles appliquées (par exemple, les règles sont appliquées sur l’argument Input et le résultat est stocké dans l’argument Result).|
|ValidationError|Liste des erreurs de validation retournées par le moteur de règles WF 3.5 lors de la validation de <xref:System.Workflow.Activities.Rules.RuleSet> sur l’objet cible avant l’exécution.|

## <a name="externalizedpolicy4-activity-designer"></a>Concepteur de l'activité ExternalizedPolicy4

Le concepteur d'ExternalizedPolicy4 vous permet de configurer une activité pour utiliser un ensemble de règles (RuleSet) existant sans écrire de code. Définissez simplement le chemin d’accès de l’emplacement où se trouve le fichier .rules et spécifiez le nom du <xref:System.Workflow.Activities.Rules.RuleSet> que vous voulez utiliser. Il vous permet également de modifier <xref:System.Workflow.Activities.Rules.RuleSet>. Après avoir généré la solution, il se trouve dans la boîte à outils, dans la section Microsoft.Samples.Activities.Rules. Le concepteur vous permet de sélectionner un fichier .rules et un <xref:System.Workflow.Activities.Rules.RuleSet>. Quand l’utilisateur clique sur le bouton modifier l’ensemble de **règles** , le <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> WF 3,5 s’affiche. Cette boîte de dialogue, qui est l'éditeur de règles WF 3.5 réhébergé, est utilisée pour afficher et modifier les règles que l'activité ExternalizedPolicy4 exécute.

## <a name="policy4-and-externalpolicy4"></a>Policy4 et ExternalPolicy4

L’activité de stratégie vous permet de créer et d’exécuter un ensemble de règles .NET Framework 3,5 dans un flux de travail WF 4,5. <xref:System.Workflow.Activities.Rules.RuleSet> est sérialisé inline dans la définition XAML de l'activité Policy4. L'exemple ExternalizedPolicy4 montre comment utiliser un <xref:System.Workflow.Activities.Rules.RuleSet> externe existant (contenu dans un fichier .rules).

## <a name="use-this-sample"></a>Utilisez cet exemple

Aucune configuration particulière n'est requise pour exécuter cet exemple. Ouvrez la solution dans Visual Studio, puis appuyez sur **F5** pour exécuter l’application.

Cet exemple contient deux applications clientes : ImperativeCodeClientSample et DesignerClientSample. Le client ImperativeCodeClientSample montre comment configurer et exécuter l'activité ExternalizedPolicy4 à l'aide de code C# impératif. DesignerClientSample montre comment configurer et exécuter l'activité ExternalizedPolicy4 à l'aide du concepteur.

### <a name="run-the-imperativecodeclientsample-application"></a>Exécuter l’application ImperativeCodeClientSample

1. À l’aide de Visual Studio, ouvrez le fichier solution *Policy4sample. sln* .

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ImperativeCodeClientSample** , puis sélectionnez **définir comme projet de démarrage**.

3. Pour exécuter le projet, appuyez sur **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Exécuter l’application DesignerClientSample

1. À l’aide de Visual Studio, ouvrez le fichier solution *Policy4sample. sln* .

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DesignerClientSample** , puis sélectionnez **définir comme projet de démarrage**.

3. Appuyez sur **Ctrl**+**MAJ**+**B** pour compiler le projet.

4. Appuyez sur **Ctrl**+**F5** pour exécuter le projet.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].
>
> Cet exemple se trouve dans le répertoire suivant :
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
