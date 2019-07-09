---
title: Concepteurs composites personnalisés - Présentateur d'éléments de workflow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: b28981196490e249d053ecd1704f6ba978585520
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662865"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Concepteurs composites personnalisés - Présentateur d'éléments de workflow

<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> est un type de clé dans le modèle de programmation de concepteur WF qui permet la modification d’une collection d’éléments contenus. Cet exemple montre comment générer un concepteur d'activités qui expose une telle collection modifiable.

Cet exemple illustre les opérations suivantes :

- Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

- Création d’un concepteur d’activités avec une vue « réduite » et « développée ».

- Substitution d'un concepteur par défaut dans une application réhébergée.

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Ouvrez le **UsingWorkflowItemsPresenter.sln** exemple de solution pour c# ou Visual Basic dans Visual Studio 2010.

2. Générez et exécutez la solution. Une application de concepteur de workflow réhébergée doit s'ouvrir, et vous pouvez faire glisser des activités sur la zone de dessin.

## <a name="sample-highlights"></a>Points clés de l'exemple

Le code de cet exemple illustre les points suivants :

- L'activité pour laquelle un concepteur est conçu : `Parallel`

- La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Quelques points à noter :

  - Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Branches`. `ModelItem` est la propriété sur `WorkflowElementDesigner` qui fait référence à l'objet sous-jacent pour lequel le concepteur est utilisé, dans ce cas, `Parallel`.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> peut être utilisé pour placer un visuel à afficher entre les éléments individuels de la collection.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> est un modèle qui peut être fourni pour déterminer la disposition des éléments dans la collection. Dans le cas présent, un panneau d'empilement horizontal est utilisé.

  L'exemple de code suivant illustre ce point.

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- Effectuez une association de `DesignerAttribute` au type `Parallel`, puis fournissez en sortie les attributs signalés.

  - En premier lieu, enregistrez tous les concepteurs par défaut.

    Voici l'exemple de code.

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - Ensuite, substituez la parallèle dans la méthode `RegisterCustomMetadata`.

    Le code suivant illustre ce point en C# et en Visual Basic.

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- Enfin, notez l'utilisation de modèles de données et de déclencheurs différents pour sélectionner le modèle approprié en fonction de la propriété `IsRootDesigner`.

  Voici l'exemple de code.

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [Développement d’applications avec le Concepteur de flux de travail](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
