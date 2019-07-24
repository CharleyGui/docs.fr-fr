---
title: 'Procédure pas à pas : hébergement d’une horloge WPF dans Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400479"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="7400f-102">Procédure pas à pas : hébergement d’une horloge WPF dans Win32</span><span class="sxs-lookup"><span data-stu-id="7400f-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>

<span data-ttu-id="7400f-103">Pour placer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] des applications, <xref:System.Windows.Interop.HwndSource>utilisez, qui fournit le HWND qui contient [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] votre contenu.</span><span class="sxs-lookup"><span data-stu-id="7400f-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="7400f-104">Tout d’abord, <xref:System.Windows.Interop.HwndSource>vous créez le, en lui attribuant des paramètres similaires à CreateWindow.</span><span class="sxs-lookup"><span data-stu-id="7400f-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="7400f-105">Vous indiquez ensuite le <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu que vous souhaitez à l’intérieur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7400f-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="7400f-106">Enfin, vous récupérez le HWND à partir <xref:System.Windows.Interop.HwndSource>du.</span><span class="sxs-lookup"><span data-stu-id="7400f-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="7400f-107">Cette procédure pas à pas montre comment créer une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] interne mixte qui réimplémente la boîte de dialogue **des propriétés de date et d’heure** du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7400f-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7400f-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7400f-108">Prerequisites</span></span>

<span data-ttu-id="7400f-109">Consultez [interopérabilité WPF et Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="7400f-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="7400f-110">Comment utiliser ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="7400f-110">How to Use This Tutorial</span></span>

<span data-ttu-id="7400f-111">Ce didacticiel se concentre sur les étapes importantes de la production d’une application d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="7400f-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="7400f-112">Ce didacticiel est associé à un exemple, l’exemple d’interopérabilité de l' [horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mais cet échantillon reflète le produit final.</span><span class="sxs-lookup"><span data-stu-id="7400f-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="7400f-113">Ce didacticiel décrit les étapes comme si vous démarriez avec un projet [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existant, peut-être un projet préexistant, et que vous ajoutiez un hébergé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à votre application.</span><span class="sxs-lookup"><span data-stu-id="7400f-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="7400f-114">Vous pouvez comparer votre produit final avec l’exemple d’interopérabilité de l' [horloge Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="7400f-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="7400f-115">Procédure pas à pas de Windows Presentation Foundation dans Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="7400f-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="7400f-116">Le graphique suivant illustre le produit final prévu pour ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="7400f-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Capture d’écran qui affiche la boîte de dialogue Propriétés de date et heure.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="7400f-118">Vous pouvez recréer cette boîte de dialogue en C++ créant un projet Win32 dans Visual Studio et en utilisant l’éditeur de boîtes de dialogue pour créer les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="7400f-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Boîte de dialogue Propriétés de date et heure recréées](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="7400f-120">(Vous n’avez pas [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] besoin d’utiliser pour utiliser <xref:System.Windows.Interop.HwndSource>, et vous n’avez pas besoin C++ d’utiliser [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour écrire des programmes, mais il s’agit d’un moyen assez courant de le faire et qui se prête bien à une explication de didacticiel progressive).</span><span class="sxs-lookup"><span data-stu-id="7400f-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="7400f-121">Vous devez effectuer cinq sous-étapes particulières pour placer une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge dans la boîte de dialogue:</span><span class="sxs-lookup"><span data-stu-id="7400f-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="7400f-122">Autorisez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] votre projet à appeler du code managé ( **/CLR**) en modifiant les [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]paramètres du projet dans.</span><span class="sxs-lookup"><span data-stu-id="7400f-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>

2. <span data-ttu-id="7400f-123">Créez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> dans une dll distincte.</span><span class="sxs-lookup"><span data-stu-id="7400f-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="7400f-124">Placez-le <xref:System.Windows.Interop.HwndSource>à l’intérieur d’un. <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7400f-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="7400f-125">Obtenir un HWND pour cela <xref:System.Windows.Controls.Page> à l' <xref:System.Windows.Interop.HwndSource.Handle%2A> aide de la propriété.</span><span class="sxs-lookup"><span data-stu-id="7400f-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="7400f-126">Utilisez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour décider où placer le HWND au sein de l' [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application de plus grande taille</span><span class="sxs-lookup"><span data-stu-id="7400f-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>

## <a name="clr"></a><span data-ttu-id="7400f-127">/clr</span><span class="sxs-lookup"><span data-stu-id="7400f-127">/clr</span></span>

<span data-ttu-id="7400f-128">La première étape consiste à transformer ce [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projet non managé en un projet qui peut appeler du code managé.</span><span class="sxs-lookup"><span data-stu-id="7400f-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span> <span data-ttu-id="7400f-129">Vous utilisez l’option du compilateur/clr, qui est liée aux DLL nécessaires que vous souhaitez utiliser et ajustez la méthode main pour une utilisation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]avec.</span><span class="sxs-lookup"><span data-stu-id="7400f-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="7400f-130">Pour activer l’utilisation du code managé à l' C++ intérieur du projet: Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7400f-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="7400f-131">Sur la page de propriétés **général** (valeur par défaut), remplacez la prise en `/clr`charge du Common Language Runtime par.</span><span class="sxs-lookup"><span data-stu-id="7400f-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="7400f-132">Ensuite, ajoutez des références aux DLL nécessaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pour: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll et UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="7400f-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="7400f-133">Les instructions suivantes supposent que le système d’exploitation est installé sur le lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="7400f-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="7400f-134">Cliquez avec le bouton droit sur le projet win32clock,, puis sélectionnez **références...** et à l’intérieur de cette boîte de dialogue:</span><span class="sxs-lookup"><span data-stu-id="7400f-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="7400f-135">Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .</span><span class="sxs-lookup"><span data-stu-id="7400f-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="7400f-136">Cliquez sur **Ajouter une nouvelle référence**, cliquez sur l’onglet Parcourir, entrez C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="7400f-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="7400f-137">Répétez la procédure pour PresentationFramework. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="7400f-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="7400f-138">Répétez la procédure pour WindowsBase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="7400f-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="7400f-139">Répétez la même opération pour UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="7400f-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="7400f-140">Répétez la procédure pour UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="7400f-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="7400f-141">Cliquez sur **Ajouter une nouvelle référence**, sélectionnez System. dll, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7400f-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="7400f-142">Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.</span><span class="sxs-lookup"><span data-stu-id="7400f-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="7400f-143">Enfin, ajoutez `STAThreadAttribute` à la méthode `_tWinMain` pour l’utiliser avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7400f-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="7400f-144">Cet attribut indique à l’Common Language Runtime (CLR) que lors de son [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]initialisation, il doit utiliser un modèle STA (Single-Threaded Apartment), qui est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nécessaire pour [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)](et).</span><span class="sxs-lookup"><span data-stu-id="7400f-144">This attribute tells the common language runtime (CLR) that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="7400f-145">Créer une page Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="7400f-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="7400f-146">Ensuite, vous créez une DLL qui définit un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Page></span><span class="sxs-lookup"><span data-stu-id="7400f-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="7400f-147">Il est souvent plus facile de créer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le <xref:System.Windows.Controls.Page> comme une application autonome, et d’écrire et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de déboguer la partie de cette façon.</span><span class="sxs-lookup"><span data-stu-id="7400f-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="7400f-148">Une fois terminé, ce projet peut être converti en DLL en cliquant avec le bouton droit sur le projet, en cliquant sur **Propriétés**, en accédant à l’application et en remplaçant le type de sortie par bibliothèque de classes Windows.</span><span class="sxs-lookup"><span data-stu-id="7400f-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="7400f-149">Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projet dll peut ensuite être combiné avec le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projet (une solution qui contient deux projets): cliquez avec le bouton droit sur la solution, puis sélectionnez **projet Add\Existing**.</span><span class="sxs-lookup"><span data-stu-id="7400f-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="7400f-150">Pour utiliser cette [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll à partir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] du projet, vous devez ajouter une référence:</span><span class="sxs-lookup"><span data-stu-id="7400f-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>

1. <span data-ttu-id="7400f-151">Cliquez avec le bouton droit sur le projet win32clock, et sélectionnez **références...** .</span><span class="sxs-lookup"><span data-stu-id="7400f-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="7400f-152">Cliquez sur **Ajouter une nouvelle référence**.</span><span class="sxs-lookup"><span data-stu-id="7400f-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="7400f-153">Cliquez sur l’onglet **Projets**. Sélectionnez WPFClock, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="7400f-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="7400f-154">Cliquez sur **OK** pour quitter les pages de propriétés win32clock, pour ajouter des références.</span><span class="sxs-lookup"><span data-stu-id="7400f-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="7400f-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="7400f-155">HwndSource</span></span>

<span data-ttu-id="7400f-156">Ensuite, vous utilisez <xref:System.Windows.Interop.HwndSource> pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> donner un aspect à un HWND.</span><span class="sxs-lookup"><span data-stu-id="7400f-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="7400f-157">Ajoutez ce bloc de code dans un fichier C++ :</span><span class="sxs-lookup"><span data-stu-id="7400f-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="7400f-158">Il s’agit d’un long bloc de code qui mérite une explication.</span><span class="sxs-lookup"><span data-stu-id="7400f-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="7400f-159">La première partie est constituée de diverses clauses qui vous évitent d’avoir à qualifier complètement tous les appels :</span><span class="sxs-lookup"><span data-stu-id="7400f-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="7400f-160">Ensuite, vous définissez une fonction qui crée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le contenu, en <xref:System.Windows.Interop.HwndSource> met une autour et retourne le HWND:</span><span class="sxs-lookup"><span data-stu-id="7400f-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="7400f-161">Tout d’abord, <xref:System.Windows.Interop.HwndSource>vous créez un, dont les paramètres sont similaires à CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="7400f-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="7400f-162">Ensuite, vous créez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la classe de contenu en appelant son constructeur:</span><span class="sxs-lookup"><span data-stu-id="7400f-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="7400f-163">Vous connectez ensuite la page à <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="7400f-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="7400f-164">Et dans la dernière ligne, retournez le HWND pour <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="7400f-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="7400f-165">Positionnement du Hwnd</span><span class="sxs-lookup"><span data-stu-id="7400f-165">Positioning the Hwnd</span></span>

<span data-ttu-id="7400f-166">Maintenant que vous avez un HWND qui contient l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] horloge, vous devez placer ce HWND dans la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7400f-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span> <span data-ttu-id="7400f-167">Si vous saviez simplement où placer le HWND, vous devez simplement passer cette taille et cet emplacement à la `GetHwnd` fonction que vous avez définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="7400f-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="7400f-168">Toutefois, étant donné que vous avez utilisé un fichier de ressources pour définir la boîte de dialogue, vous ne savez pas exactement où les HWND sont positionnés.</span><span class="sxs-lookup"><span data-stu-id="7400f-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="7400f-169">Vous pouvez utiliser l' [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] éditeur de boîtes de dialogue [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pour placer un contrôle statique à l’emplacement où vous souhaitez placer l’horloge («insérer l’horloge ici») et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’utiliser pour positionner l’horloge.</span><span class="sxs-lookup"><span data-stu-id="7400f-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="7400f-170">Lorsque vous gérez WM_INITDIALOG, vous utilisez `GetDlgItem` pour récupérer le HWND pour l’espace réservé static:</span><span class="sxs-lookup"><span data-stu-id="7400f-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="7400f-171">Vous calculez ensuite la taille et la position de cet espace réservé statique. vous pouvez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donc placer l’horloge à cet endroit:</span><span class="sxs-lookup"><span data-stu-id="7400f-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="7400f-172">RECT rectangle;</span><span class="sxs-lookup"><span data-stu-id="7400f-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="7400f-173">Ensuite, masquez l’espace réservé STATIC :</span><span class="sxs-lookup"><span data-stu-id="7400f-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="7400f-174">Et créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND Clock à cet emplacement:</span><span class="sxs-lookup"><span data-stu-id="7400f-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="7400f-175">Pour rendre le didacticiel intéressant et produire une horloge réelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , vous devez créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôle Clock à ce stade.</span><span class="sxs-lookup"><span data-stu-id="7400f-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="7400f-176">Cette procédure se fait principalement en langage de balisage, avec quelques gestionnaires d’événements dans le code-behind.</span><span class="sxs-lookup"><span data-stu-id="7400f-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="7400f-177">Étant donné que ce didacticiel concerne l’interopérabilité et non la conception des contrôles, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code complet de l’horloge est fourni ici en tant que bloc de code, sans instructions discrètes pour sa création ou ce que signifie chaque partie.</span><span class="sxs-lookup"><span data-stu-id="7400f-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="7400f-178">N’hésitez pas à tester ce code pour changer l’apparence ou la fonctionnalité du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7400f-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="7400f-179">Voici le code XAML :</span><span class="sxs-lookup"><span data-stu-id="7400f-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="7400f-180">Voici le code-behind correspondant :</span><span class="sxs-lookup"><span data-stu-id="7400f-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="7400f-181">Le résultat final ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="7400f-181">The final result looks like:</span></span>

![Boîte de dialogue Propriétés de date et heure du résultat final](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="7400f-183">Pour comparer votre résultat final au code qui a produit cette capture d’écran, consultez [exemple d’interopérabilité Win32 Clock](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="7400f-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="7400f-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7400f-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="7400f-185">Interopérabilité WPF et Win32</span><span class="sxs-lookup"><span data-stu-id="7400f-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="7400f-186">Interopérabilité Win32 Clock, exemple</span><span class="sxs-lookup"><span data-stu-id="7400f-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
