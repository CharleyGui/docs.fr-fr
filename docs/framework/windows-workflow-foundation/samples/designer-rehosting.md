---
title: Réhébergement du concepteur
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b72e3450799db40988c8b99e4db3707de330d8ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182817"
---
# <a name="designer-rehosting"></a>Réhébergement du concepteur
Le réhébergement du concepteur est un scénario courant qui fait référence à l'hébergement de la zone de dessin de conception du workflow dans une application personnalisée. L'application d'hébergement avec laquelle la plupart des personnes sont familières est Visual Studio, mais il existe plusieurs scénarios où l'affichage du concepteur de workflow dans une application peut être utile :  
  
- Applications d'analyse (permettant à un utilisateur final de visualiser le processus ainsi que les données d'exécution sur le processus, telles que l'état actuellement actif, les données de durée d'exécution agrégées ou d'autres informations relatives à une instance du workflow).  
  
- Applications qui permettent à un utilisateur de personnaliser le processus avec un ensemble limité d'activités.  
  
 Pour prendre en charge ces types d'applications, le concepteur de workflow accompagne le .NET Framework et peut être hébergé à l'intérieur d'une application WPF, ou dans une application WinForms avec le code d'hébergement WPF approprié. Cet exemple montre :  
  
- Réhébergement du concepteur WF.  
  
- Utilisation de la boîte à outils réhébergée ainsi que de la grille des propriétés.  
  
## <a name="rehosting-the-designer"></a>Réhébergement du concepteur  
 Cet exemple montre comment créer la disposition WPF pour contenir le concepteur, comme dans la disposition de grille suivante (code de boîte à outils omis pour des raisons d'espace). Notez la désignation des bordures qui contiennent le concepteur et la grille des propriétés.  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 Ensuite, l'exemple crée le concepteur et associe son <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> primaire et <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> au conteneur approprié dans l'interface utilisateur. Quelques lignes supplémentaires de code dans l'exemple suivant méritent une explication. L’appel <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> est nécessaire pour associer les concepteurs d’activités par défaut pour les activités expédiées avec .NET Framework. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> est appelé pour passer l'élément WF à modifier. Enfin, le <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (zone de dessin primaire) et le <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (grille des propriétés) sont placés sur la surface d'interface utilisateur.  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a>Utilisation de la boîte à outils réhébergée  
 Cet exemple utilise de façon déclarative le contrôle de boîte à outils réhébergée dans XAML. Notez que, dans le code, un type peut être passé au constructeur <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper>.  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a>Utilisation de l'exemple  
  
1. Ouvrez la solution DesignerRehosting.sln dans Visual Studio 2010.  
  
2. Appuyez sur F5 pour compiler et exécuter l'application.  
  
3. Une application WPF démarre avec un concepteur réhébergé.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
