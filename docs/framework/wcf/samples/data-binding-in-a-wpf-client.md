---
title: Data Binding in a Windows Presentation Foundation Client
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 926b60bd489d65dd2ec051baae399f2688e52cd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289215"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="ca5dd-102">Data Binding in a Windows Presentation Foundation Client</span><span class="sxs-lookup"><span data-stu-id="ca5dd-102">Data Binding in a Windows Presentation Foundation Client</span></span>

<span data-ttu-id="ca5dd-103">Cet exemple illustre l’utilisation de la liaison de données dans un client Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="ca5dd-104">L’exemple utilise un service Windows Communication Foundation (WCF) qui génère de manière aléatoire un tableau d’albums à retourner au client.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="ca5dd-105">Pour chaque album, un nom, un prix et une liste des pistes y figurant sont définis.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="ca5dd-106">Un nom et une durée sont indiqués pour chaque piste.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="ca5dd-107">Les informations retournées par le service sont automatiquement liées à l’interface utilisateur (IU) fournie par le client Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca5dd-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ca5dd-109">La liaison de données permet à une source de données d’être automatiquement liée à une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="ca5dd-110">Cela simplifie le modèle de programmation car vous n'êtes pas obligé ainsi de mettre à jour par programme chaque élément de l'interface utilisateur avec les données provenant d'un objet de données ou d'un tableau d'objets de données.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="ca5dd-111">Vous pouvez lier un objet à un seul élément d'interface utilisateur ou un tableau à une commande acceptant plusieurs entrées, comme `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="ca5dd-112">Le code suivant indique comment lier des données au `DataContext` d'un élément d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="ca5dd-113">Dans l'exemple précédent, le `DataContext` de l'élément de mise en page `grid` nommé `myPanel` a pour valeur les données retournées par la méthode `GetAlbumList`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="ca5dd-114">Le `DataContext` permet aux éléments d'hériter des informations de leurs éléments parents concernant la source de données utilisée pour la liaison ainsi que d'autres caractéristiques afférentes à cette dernière telles que le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="ca5dd-115">La ligne de code doit être exécutée à chaque mise à jour des données sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="ca5dd-116">Par exemple, cette ligne doit être exécutée lorsque la fenêtre est initialisée et lorsqu'un nouvel album est ajouté.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="ca5dd-117">Dans l'exemple de code XAML suivant, `ListBox` spécifie `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="ca5dd-118">Cela signifie que les données liées à l'élément d'interface utilisateur de niveau supérieur sont également liées à cette commande (c'est-à-dire au tableau d'albums).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="ca5dd-119">En outre, `ItemTemplate="{StaticResource AlbumStyle}"` spécifie le modèle de données à utiliser pour chaque élément dans `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="ca5dd-120">Vous pouvez également définir des modèles de données afin de spécifier les modalités de formatage des données.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="ca5dd-121">Ces modèles peuvent ensuite être réutilisés pour d'autres éléments d'interface utilisateur figurant dans l'application. Ces modèles présentent l'avantage d'être définis et conservés à un même emplacement.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="ca5dd-122">Le modèle de données `AlbumStyle` définit une grille contenant deux `TextBlock` côte à côte.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="ca5dd-123">Le premier spécifie le nom de l'album et le second le nombre de pistes figurant dans cet album.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="ca5dd-124">L'exemple de code XAML suivant crée une seconde commande `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="ca5dd-125">Le code spécifie le chemin d’accès à `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="ca5dd-126">Cela signifie que les données liées à cette commande ne correspondent pas aux données de niveau supérieur mais à une propriété de ces données nommées `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="ca5dd-127">Cette propriété représente le tableau de pistes contenues dans l'album.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="ca5dd-128">Un modèle `DataTemplate` nommé `TrackStyle` est également spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="ca5dd-129">La mise en page du modèle `TrackStyle` est semblable à celle du modèle `AlbumStyle`, mais les `TextBlock` sont liés à des propriétés différentes.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="ca5dd-130">Cela est dû au fait que ces deux modèles sont utilisés avec des objets de données différents.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca5dd-131">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ca5dd-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ca5dd-132">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ca5dd-133">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ca5dd-134">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca5dd-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ca5dd-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca5dd-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ca5dd-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ca5dd-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca5dd-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ca5dd-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
