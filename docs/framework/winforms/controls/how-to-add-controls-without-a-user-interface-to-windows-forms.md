---
title: Ajouter des contrôles sans interface utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 43f13b4f009fcd6e5d82fa2c00113a77d48877b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744757"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="b85d7-102">Comment : ajouter des contrôles sans interface utilisateur à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="b85d7-103">Un contrôle (ou un composant) qui fournit des fonctionnalités à votre application.</span><span class="sxs-lookup"><span data-stu-id="b85d7-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="b85d7-104">Contrairement à d’autres contrôles, les composants ne fournissent pas d’interface utilisateur à l’utilisateur et n’ont donc pas besoin d’être affichés sur l’aire de Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b85d7-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="b85d7-105">Lorsqu’un composant est ajouté à un formulaire, le Concepteur Windows Forms affiche un plateau redimensionnable en bas du formulaire où tous les composants sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b85d7-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="b85d7-106">Une fois qu’un contrôle a été ajouté à la barre d’état des composants, vous pouvez sélectionner le composant et définir ses propriétés comme vous le feriez pour n’importe quel autre contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b85d7-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="b85d7-107">Ajouter un composant à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="b85d7-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="b85d7-108">Ouvrez le formulaire dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b85d7-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="b85d7-109">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b85d7-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="b85d7-110">Dans la **boîte à outils**, cliquez sur un composant et faites-le glisser vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="b85d7-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="b85d7-111">Votre composant apparaît dans la barre d’état des composants.</span><span class="sxs-lookup"><span data-stu-id="b85d7-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="b85d7-112">En outre, les composants peuvent être ajoutés à un formulaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b85d7-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="b85d7-113">Il s’agit d’un scénario courant, en particulier parce que les composants n’ont pas d’expression visuelle, contrairement aux contrôles qui ont une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b85d7-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="b85d7-114">Dans l’exemple ci-dessous, un composant <xref:System.Windows.Forms.Timer> est ajouté au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b85d7-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="b85d7-115">(Notez que Visual Studio contient plusieurs minuteries ; dans ce cas, utilisez un composant Windows Forms <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="b85d7-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="b85d7-116">Pour plus d’informations sur les différents minuteries dans Visual Studio, consultez [Présentation des minuteries basées sur un serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="b85d7-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="b85d7-117">Les composants ont souvent des propriétés spécifiques au contrôle qui doivent être définies pour que le composant fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="b85d7-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="b85d7-118">Dans le cas du composant <xref:System.Windows.Forms.Timer> ci-dessous, vous définissez la propriété `Interval`.</span><span class="sxs-lookup"><span data-stu-id="b85d7-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="b85d7-119">Lorsque vous ajoutez des composants à votre projet, veillez à définir les propriétés nécessaires pour ce composant.</span><span class="sxs-lookup"><span data-stu-id="b85d7-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="b85d7-120">Ajouter par programme un composant à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="b85d7-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="b85d7-121">Créez une instance de la classe <xref:System.Windows.Forms.Timer> dans le code.</span><span class="sxs-lookup"><span data-stu-id="b85d7-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="b85d7-122">Définissez la propriété `Interval` pour déterminer l’intervalle entre les graduations de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="b85d7-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="b85d7-123">Configurez toutes les autres propriétés nécessaires pour votre composant.</span><span class="sxs-lookup"><span data-stu-id="b85d7-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="b85d7-124">Le code suivant illustre la création d’une <xref:System.Windows.Forms.Timer> avec sa propriété `Interval` définie.</span><span class="sxs-lookup"><span data-stu-id="b85d7-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b85d7-125">Vous pouvez exposer votre ordinateur local à un risque de sécurité sur le réseau en référençant un UserControl malveillant.</span><span class="sxs-lookup"><span data-stu-id="b85d7-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="b85d7-126">Cela ne serait qu’une préoccupation dans le cas d’une personne malveillante qui crée un contrôle personnalisé nuisible, puis de l’ajouter par erreur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="b85d7-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="b85d7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b85d7-127">See also</span></span>

- [<span data-ttu-id="b85d7-128">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="b85d7-129">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="b85d7-130">Guide pratique pour ajouter des contrôles ActiveX aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="b85d7-131">Placement de contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="b85d7-132">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b85d7-133">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b85d7-134">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85d7-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
