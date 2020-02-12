---
title: 'Procédure pas à pas : héberger une horloge WPF dans Win32'
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 0aecde96d182e12ab72b1a6cba129ab1d8a28391
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123777"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a><span data-ttu-id="b1575-102">Procédure pas à pas : héberger une horloge WPF dans Win32</span><span class="sxs-lookup"><span data-stu-id="b1575-102">Walkthrough: Host a WPF Clock in Win32</span></span>

<span data-ttu-id="b1575-103">Pour placer des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans des applications Win32, utilisez <xref:System.Windows.Interop.HwndSource>, qui fournit le HWND qui contient le contenu de votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1575-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="b1575-104">Tout d’abord, vous créez le <xref:System.Windows.Interop.HwndSource>, en lui attribuant des paramètres similaires à CreateWindow.</span><span class="sxs-lookup"><span data-stu-id="b1575-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="b1575-105">Ensuite, vous indiquez à la <xref:System.Windows.Interop.HwndSource> à propos du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] souhaité.</span><span class="sxs-lookup"><span data-stu-id="b1575-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="b1575-106">Enfin, vous récupérez le HWND à partir du <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="b1575-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="b1575-107">Cette procédure pas à pas montre comment créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mixte dans une application Win32 qui réimplémente la boîte de dialogue **des propriétés de date et d’heure** du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b1575-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1575-108">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="b1575-108">Prerequisites</span></span>

<span data-ttu-id="b1575-109">Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="b1575-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="b1575-110">Comment utiliser ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="b1575-110">How to Use This Tutorial</span></span>

<span data-ttu-id="b1575-111">Ce didacticiel se concentre sur les étapes importantes de la production d’une application d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="b1575-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="b1575-112">Ce didacticiel est associé à un exemple, l' [exemple d’interopérabilité de l’horloge Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock), mais cet échantillon reflète le produit final.</span><span class="sxs-lookup"><span data-stu-id="b1575-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock), but that sample is reflective of the end product.</span></span> <span data-ttu-id="b1575-113">Ce didacticiel décrit les étapes comme si vous travailliez avec un projet Win32 existant, peut-être un projet préexistant, et que vous ajoutiez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé à votre application.</span><span class="sxs-lookup"><span data-stu-id="b1575-113">This tutorial documents the steps as if you were starting with an existing Win32 project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="b1575-114">Vous pouvez comparer votre produit final avec l' [exemple d’interopérabilité de l’horloge Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span><span class="sxs-lookup"><span data-stu-id="b1575-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="b1575-115">Procédure pas à pas de Windows Presentation Foundation dans Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="b1575-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="b1575-116">Le graphique suivant illustre le produit final prévu pour ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="b1575-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Capture d’écran qui affiche la boîte de dialogue Propriétés de date et heure.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="b1575-118">Vous pouvez recréer cette boîte de dialogue en C++ créant un projet Win32 dans Visual Studio et en utilisant l’éditeur de boîtes de dialogue pour créer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b1575-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Boîte de dialogue Propriétés de date et heure recréées](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="b1575-120">(Vous n’avez pas besoin d’utiliser Visual Studio pour utiliser <xref:System.Windows.Interop.HwndSource>, et vous n’avez pas besoin C++ d’utiliser pour écrire des programmes Win32, mais il s’agit d’un moyen assez courant de le faire et qui se prête bien à une explication progressive du didacticiel).</span><span class="sxs-lookup"><span data-stu-id="b1575-120">(You do not need to use Visual Studio to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write Win32 programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="b1575-121">Vous devez effectuer cinq sous-étapes particulières pour placer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge dans la boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="b1575-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="b1575-122">Autorisez votre projet Win32 à appeler du code managé ( **/CLR**) en modifiant les paramètres du projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1575-122">Enable your Win32 project to call managed code (**/clr**) by changing project settings in Visual Studio.</span></span>

2. <span data-ttu-id="b1575-123">Créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dans une DLL distincte.</span><span class="sxs-lookup"><span data-stu-id="b1575-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="b1575-124">Placez ce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> à l’intérieur d’un <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="b1575-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="b1575-125">Obtenir un HWND pour ce <xref:System.Windows.Controls.Page> à l’aide de la propriété <xref:System.Windows.Interop.HwndSource.Handle%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1575-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="b1575-126">Utiliser Win32 pour décider où placer le HWND dans une application Win32 plus grande</span><span class="sxs-lookup"><span data-stu-id="b1575-126">Use Win32 to decide where to place the HWND within the larger Win32 application</span></span>

## <a name="clr"></a><span data-ttu-id="b1575-127">/clr</span><span class="sxs-lookup"><span data-stu-id="b1575-127">/clr</span></span>

<span data-ttu-id="b1575-128">La première étape consiste à transformer ce projet Win32 non managé en un projet qui peut appeler du code managé.</span><span class="sxs-lookup"><span data-stu-id="b1575-128">The first step is to turn this unmanaged Win32 project into one that can call managed code.</span></span> <span data-ttu-id="b1575-129">Vous utilisez l’option du compilateur/clr, qui est liée aux DLL nécessaires que vous souhaitez utiliser et ajustez la méthode main pour une utilisation avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1575-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="b1575-130">Pour activer l’utilisation du code managé dans le C++ projet : cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b1575-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="b1575-131">Sur la page de propriétés **général** (valeur par défaut), modifiez la prise en charge du Common Language Runtime pour `/clr`.</span><span class="sxs-lookup"><span data-stu-id="b1575-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="b1575-132">Ensuite, ajoutez des références aux DLL nécessaires pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll et UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="b1575-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="b1575-133">Les instructions suivantes supposent que le système d’exploitation est installé sur le lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="b1575-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="b1575-134">Cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **références...** et à l’intérieur de cette boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="b1575-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="b1575-135">Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .</span><span class="sxs-lookup"><span data-stu-id="b1575-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="b1575-136">Cliquez sur **Ajouter une nouvelle référence**, cliquez sur l’onglet Parcourir, entrez C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="b1575-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="b1575-137">Répétez la même procédure pour PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="b1575-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="b1575-138">Répétez la même procédure pour WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="b1575-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="b1575-139">Répétez la même procédure pour UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="b1575-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="b1575-140">Répétez la même procédure pour UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="b1575-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="b1575-141">Cliquez sur **Ajouter une nouvelle référence**, sélectionnez System. dll, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1575-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="b1575-142">Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.</span><span class="sxs-lookup"><span data-stu-id="b1575-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="b1575-143">Enfin, ajoutez le `STAThreadAttribute` à la méthode `_tWinMain` à utiliser avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b1575-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="b1575-144">Cet attribut indique au common language runtime (CLR) que lorsqu’il initialise le modèle COM (Component Object Model), il doit utiliser un modèle STA (Single-Threaded Apartment), qui est nécessaire pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (et Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="b1575-144">This attribute tells the common language runtime (CLR) that when it initializes Component Object Model (COM), it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and Windows Forms).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="b1575-145">Créer une page Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="b1575-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="b1575-146">Ensuite, vous créez une DLL qui définit un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="b1575-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="b1575-147">Il est souvent plus facile de créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> en tant qu’application autonome, et d’écrire et de déboguer la partie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de cette façon.</span><span class="sxs-lookup"><span data-stu-id="b1575-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="b1575-148">Une fois terminé, ce projet peut être converti en DLL en cliquant avec le bouton droit sur le projet, en cliquant sur **Propriétés**, en accédant à l’application et en remplaçant le type de sortie par bibliothèque de classes Windows.</span><span class="sxs-lookup"><span data-stu-id="b1575-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="b1575-149">Le projet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll peut ensuite être combiné avec le projet Win32 (une solution qui contient deux projets) : cliquez avec le bouton droit sur la solution, puis sélectionnez **projet Add\Existing**.</span><span class="sxs-lookup"><span data-stu-id="b1575-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the Win32 project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="b1575-150">Pour utiliser cette [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll à partir du projet Win32, vous devez ajouter une référence :</span><span class="sxs-lookup"><span data-stu-id="b1575-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the Win32 project, you need to add a reference:</span></span>

1. <span data-ttu-id="b1575-151">Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .</span><span class="sxs-lookup"><span data-stu-id="b1575-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="b1575-152">Cliquez sur **Ajouter une nouvelle référence**.</span><span class="sxs-lookup"><span data-stu-id="b1575-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="b1575-153">Cliquez sur l’onglet **projets** . Sélectionnez WPFClock, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="b1575-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="b1575-154">Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.</span><span class="sxs-lookup"><span data-stu-id="b1575-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="b1575-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="b1575-155">HwndSource</span></span>

<span data-ttu-id="b1575-156">Ensuite, vous utilisez <xref:System.Windows.Interop.HwndSource> pour que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> ressemble à un HWND.</span><span class="sxs-lookup"><span data-stu-id="b1575-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="b1575-157">Ajoutez ce bloc de code dans un fichier C++ :</span><span class="sxs-lookup"><span data-stu-id="b1575-157">You add this block of code to a C++ file:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 <span data-ttu-id="b1575-158">Il s’agit d’un long bloc de code qui mérite une explication.</span><span class="sxs-lookup"><span data-stu-id="b1575-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="b1575-159">La première partie est constituée de diverses clauses qui vous évitent d’avoir à qualifier complètement tous les appels :</span><span class="sxs-lookup"><span data-stu-id="b1575-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="b1575-160">Ensuite, vous définissez une fonction qui crée le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], met un <xref:System.Windows.Interop.HwndSource> autour et retourne le HWND :</span><span class="sxs-lookup"><span data-stu-id="b1575-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="b1575-161">Tout d’abord, vous créez un <xref:System.Windows.Interop.HwndSource>, dont les paramètres sont similaires à CreateWindow :</span><span class="sxs-lookup"><span data-stu-id="b1575-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

<span data-ttu-id="b1575-162">Ensuite, vous créez la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant son constructeur :</span><span class="sxs-lookup"><span data-stu-id="b1575-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="b1575-163">Vous connectez ensuite la page à la <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="b1575-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="b1575-164">Et dans la dernière ligne, retournez le HWND pour l' <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="b1575-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="b1575-165">Positionnement du Hwnd</span><span class="sxs-lookup"><span data-stu-id="b1575-165">Positioning the Hwnd</span></span>

<span data-ttu-id="b1575-166">Maintenant que vous avez un HWND qui contient le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge, vous devez placer ce HWND dans la boîte de dialogue Win32.</span><span class="sxs-lookup"><span data-stu-id="b1575-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the Win32 dialog.</span></span> <span data-ttu-id="b1575-167">Si vous saviez simplement où placer le HWND, vous devez simplement passer cette taille et cet emplacement à la fonction `GetHwnd` que vous avez définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="b1575-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="b1575-168">Toutefois, étant donné que vous avez utilisé un fichier de ressources pour définir la boîte de dialogue, vous ne savez pas exactement où les HWND sont positionnés.</span><span class="sxs-lookup"><span data-stu-id="b1575-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="b1575-169">Vous pouvez utiliser l’éditeur de boîtes de dialogue de Visual Studio pour placer un contrôle statique Win32 à l’endroit où vous souhaitez que l’horloge se trouve (« insérer l’horloge ici ») et l’utiliser pour positionner le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge.</span><span class="sxs-lookup"><span data-stu-id="b1575-169">You can use the Visual Studio dialog editor to put a Win32 STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="b1575-170">Lorsque vous gérez WM_INITDIALOG, vous utilisez `GetDlgItem` pour récupérer le HWND pour l’espace réservé STATIC :</span><span class="sxs-lookup"><span data-stu-id="b1575-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="b1575-171">Vous calculez ensuite la taille et la position de cet espace réservé statique, de sorte que vous pouvez placer la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge à cet endroit :</span><span class="sxs-lookup"><span data-stu-id="b1575-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="b1575-172">RECT rectangle;</span><span class="sxs-lookup"><span data-stu-id="b1575-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="b1575-173">Ensuite, masquez l’espace réservé STATIC :</span><span class="sxs-lookup"><span data-stu-id="b1575-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="b1575-174">Et créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND horloge à cet emplacement :</span><span class="sxs-lookup"><span data-stu-id="b1575-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="b1575-175">Pour rendre le didacticiel intéressant et produire une horloge de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] réelle, vous devrez créer un contrôle d’horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à ce stade.</span><span class="sxs-lookup"><span data-stu-id="b1575-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="b1575-176">Cette procédure se fait principalement en langage de balisage, avec quelques gestionnaires d’événements dans le code-behind.</span><span class="sxs-lookup"><span data-stu-id="b1575-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="b1575-177">Dans la mesure où ce didacticiel concerne l’interopérabilité et non la conception des contrôles, le code complet de l’horloge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est fourni ici comme bloc de code, sans instructions discrètes pour sa création ou ce que signifie chaque partie.</span><span class="sxs-lookup"><span data-stu-id="b1575-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="b1575-178">N’hésitez pas à tester ce code pour changer l’apparence ou la fonctionnalité du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b1575-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="b1575-179">Voici le code XAML :</span><span class="sxs-lookup"><span data-stu-id="b1575-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="b1575-180">Voici le code-behind correspondant :</span><span class="sxs-lookup"><span data-stu-id="b1575-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="b1575-181">Le résultat final ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="b1575-181">The final result looks like:</span></span>

![Boîte de dialogue Propriétés de date et heure du résultat final](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="b1575-183">Pour comparer votre résultat final au code qui a produit cette capture d’écran, consultez [exemple d’interopérabilité Win32 Clock](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span><span class="sxs-lookup"><span data-stu-id="b1575-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1575-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1575-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="b1575-185">Interopérabilité WPF et Win32</span><span class="sxs-lookup"><span data-stu-id="b1575-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="b1575-186">Interopérabilité Win32 Clock, exemple</span><span class="sxs-lookup"><span data-stu-id="b1575-186">Win32 Clock Interoperation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock)
