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
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="f7ab3-102">Suppression de l’état d’affichage que le concepteur ajoute à un fichier XAML</span><span class="sxs-lookup"><span data-stu-id="f7ab3-102">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="f7ab3-103">Cet exemple montre comment créer une classe qui dérive de <xref:System.Xaml.XamlWriter> et supprime l'état d'affichage d'un fichier XAML.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-103">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="f7ab3-104">Windows Concepteur de flux de travail écrit des informations dans le document XAML, connu sous le nom d’état d’affichage.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-104">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="f7ab3-105">L'état d'affichage fait référence aux informations qui sont requises au moment du design, telles que le positionnement, et qui ne le sont pas au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="f7ab3-106">Concepteur de flux de travail insère ces informations dans le document XAML au fur et à mesure de leur modification.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-106">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="f7ab3-107">Concepteur de flux de travail écrit l’état d’affichage dans le fichier XAML avec l’attribut `mc:Ignorable`, ces informations ne sont pas chargées lorsque le runtime charge le fichier XAML.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-107">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="f7ab3-108">Cet exemple montre comment créer une classe qui supprime ces informations d'état d'affichage lors du traitement des nœuds XAML.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="f7ab3-109">Discussion</span><span class="sxs-lookup"><span data-stu-id="f7ab3-109">Discussion</span></span>

<span data-ttu-id="f7ab3-110">Cet exemple montre comment créer un writer personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-110">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="f7ab3-111">Pour générer un writer XAML personnalisé, créez une classe qui hérite de <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-111">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="f7ab3-112">Comme les writers XAML sont souvent imbriqués, il est courant d’effectuer le suivi d’un writer XAML « interne ».</span><span class="sxs-lookup"><span data-stu-id="f7ab3-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="f7ab3-113">Ces Writers « internes » peuvent être considérés comme la référence à la pile restante des writers XAML, ce qui vous permet d’avoir plusieurs points d’entrée pour travailler, puis de déléguer le traitement au reste de la pile.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="f7ab3-114">Dans cet exemple, quelques points sont intéressants.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="f7ab3-115">L'un consiste à déterminer si l'élément qui est écrit provient de l'espace de noms d'un concepteur.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="f7ab3-116">Notez que cela supprime également l'utilisation d'autres types de l'espace de noms du concepteur dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

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

<span data-ttu-id="f7ab3-117">Cela crée également une pile de membres XAML utilisés lors de la traversée du flux de nœud.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="f7ab3-118">Le travail restant de cet exemple est en grande partie contenu dans la méthode `WriteStartMember`.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-118">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

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

<span data-ttu-id="f7ab3-119">Les méthodes suivantes vérifient ensuite leur présence dans un conteneur d'états d'affichage et, le cas échéant, retournent et ne transmettent pas le nœud à la pile de writers.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

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

<span data-ttu-id="f7ab3-120">Pour utiliser un writer XAML personnalisé, vous devez le lier à une pile de writers XAML.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="f7ab3-121">Le code suivant montre comment il peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="f7ab3-122">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="f7ab3-122">To use this sample</span></span>

1. <span data-ttu-id="f7ab3-123">À l’aide de Visual Studio 2010, ouvrez le fichier solution ViewStateCleaningWriter. sln.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="f7ab3-124">Ouvrez une invite de commandes et naviguez jusqu'au répertoire où ViewStageCleaningWriter.exe est généré.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="f7ab3-125">Exécutez ViewStateCleaningWriter.exe sur le fichier Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="f7ab3-126">La syntaxe pour le fichier exécutable est affichée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="f7ab3-127">Cela génère un fichier XAML vers \[fichier out], dont toutes les informations d’état d’affichage sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ab3-128">Pour un workflow <xref:System.Activities.Statements.Sequence>, plusieurs indicateurs de virtualisation sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="f7ab3-129">Le concepteur doit donc recalculer la disposition lors du chargement suivant.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="f7ab3-130">Lorsque vous utilisez cet exemple pour un <xref:System.Activities.Statements.Flowchart>, toutes les informations de routage de positionnement et de ligne sont supprimées et, lors du chargement suivant dans le concepteur, toutes les activités sont empilées sur le côté gauche de l'écran.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="f7ab3-131">Pour créer un exemple de fichier XAML à utiliser avec cet exemple</span><span class="sxs-lookup"><span data-stu-id="f7ab3-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="f7ab3-132">Ouvrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="f7ab3-133">Créez une application console de workflow.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="f7ab3-134">Faites glisser et déposez quelques activités sur la zone de dessin.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="f7ab3-135">Enregistrez le fichier XAML de workflow.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="f7ab3-136">Inspectez le fichier XAML pour consulter les propriétés jointes d'état d'affichage.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7ab3-137">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7ab3-138">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-138">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f7ab3-139">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7ab3-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7ab3-140">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f7ab3-140">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
