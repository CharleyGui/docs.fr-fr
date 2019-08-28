---
title: Concepteurs composites personnalisés - Présentateur d'éléments de workflow
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038371"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Concepteurs composites personnalisés - Présentateur d'éléments de workflow
Le <xref:System.Activities.Presentation.WorkflowItemPresenter> est un type de clé dans le modèle de programmation de concepteur WF qui permet la création d’une «zone de dépôt» où une activité arbitraire peut être placée. Cet exemple montre comment générer un concepteur d’activités qui couvre une telle «zone de dépôt».

 Cet exemple illustre les opérations suivantes :

## <a name="demonstrates"></a>Démonstrations

- Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.

- Inscription du concepteur personnalisé à l'aide du magasin des métadonnées.

- Programmation de la boîte à outils réhébergée de façon déclarative et impérative.

## <a name="sample-details"></a>Détails de l'exemple
 Le code de cet exemple illustre les points suivants :

- Le concepteur d'activités personnalisées est généré pour la classe `SimpleNativeActivity`.

- La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Body`. `ModelItem`est la propriété sur <xref:System.Activities.Presentation.ActivityDesigner> qui fait référence à l’objet sous-jacent pour lequel le concepteur est utilisé, dans ce cas, **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Ouvrez la solution dans Visual Studio 2010.

2. Appuyez sur F5 pour compiler et exécuter l'application.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [Développement d’applications avec le Concepteur de flux de travail](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
