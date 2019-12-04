---
title: Suppression de l’état d’affichage que le concepteur ajoute à un fichier XAML-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715619"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Suppression de l’état d’affichage que le concepteur ajoute à un fichier XAML

Cet exemple montre comment créer une classe qui dérive de <xref:System.Xaml.XamlWriter> et supprime l'état d'affichage d'un fichier XAML. Windows Concepteur de flux de travail écrit des informations dans le document XAML, connu sous le nom d’état d’affichage. L'état d'affichage fait référence aux informations qui sont requises au moment du design, telles que le positionnement, et qui ne le sont pas au moment de l'exécution. Concepteur de flux de travail insère ces informations dans le document XAML au fur et à mesure de leur modification. Concepteur de flux de travail écrit l’état d’affichage dans le fichier XAML avec l’attribut `mc:Ignorable`, ces informations ne sont pas chargées lorsque le runtime charge le fichier XAML. Cet exemple montre comment créer une classe qui supprime ces informations d'état d'affichage lors du traitement des nœuds XAML.

## <a name="discussion"></a>Discussion

Cet exemple montre comment créer un writer personnalisé.

Pour générer un writer XAML personnalisé, créez une classe qui hérite de <xref:System.Xaml.XamlWriter>. Comme les writers XAML sont souvent imbriqués, il est courant d’effectuer le suivi d’un writer XAML « interne ». Ces Writers « internes » peuvent être considérés comme la référence à la pile restante des writers XAML, ce qui vous permet d’avoir plusieurs points d’entrée pour travailler, puis de déléguer le traitement au reste de la pile.

Dans cet exemple, quelques points sont intéressants. L'un consiste à déterminer si l'élément qui est écrit provient de l'espace de noms d'un concepteur. Notez que cela supprime également l'utilisation d'autres types de l'espace de noms du concepteur dans un workflow.

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

Cela crée également une pile de membres XAML utilisés lors de la traversée du flux de nœud. Le travail restant de cet exemple est en grande partie contenu dans la méthode `WriteStartMember`.

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

Les méthodes suivantes vérifient ensuite leur présence dans un conteneur d'états d'affichage et, le cas échéant, retournent et ne transmettent pas le nœud à la pile de writers.

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

Pour utiliser un writer XAML personnalisé, vous devez le lier à une pile de writers XAML. Le code suivant montre comment il peut être utilisé.

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2010, ouvrez le fichier solution ViewStateCleaningWriter. sln.

2. Ouvrez une invite de commandes et naviguez jusqu'au répertoire où ViewStageCleaningWriter.exe est généré.

3. Exécutez ViewStateCleaningWriter.exe sur le fichier Workflow1.xaml.

   La syntaxe pour le fichier exécutable est affichée dans l'exemple suivant.

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   Cela génère un fichier XAML vers \[fichier out], dont toutes les informations d’état d’affichage sont supprimées.

> [!NOTE]
> Pour un workflow <xref:System.Activities.Statements.Sequence>, plusieurs indicateurs de virtualisation sont supprimés. Le concepteur doit donc recalculer la disposition lors du chargement suivant. Lorsque vous utilisez cet exemple pour un <xref:System.Activities.Statements.Flowchart>, toutes les informations de routage de positionnement et de ligne sont supprimées et, lors du chargement suivant dans le concepteur, toutes les activités sont empilées sur le côté gauche de l'écran.

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Pour créer un exemple de fichier XAML à utiliser avec cet exemple

1. Ouvrez Visual Studio 2010.

2. Créez une application console de workflow.

3. Faites glisser et déposez quelques activités sur la zone de dessin.

4. Enregistrez le fichier XAML de workflow.

5. Inspectez le fichier XAML pour consulter les propriétés jointes d'état d'affichage.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
