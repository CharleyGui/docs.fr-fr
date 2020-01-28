---
title: Ajouter des contrôles ActiveX aux formulaires
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 920c1111a5703352a4b624068e3d5ceae9892591
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746844"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="84861-102">Comment : ajouter des contrôles ActiveX aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="84861-103">Tandis que le Concepteur Windows Forms dans Visual Studio est optimisé pour héberger des contrôles de Windows Forms, vous pouvez également placer des contrôles ActiveX sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84861-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="84861-104">Il existe des limitations de performances pour Windows Forms lors de l’ajout de contrôles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="84861-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="84861-105">Avant d’ajouter des contrôles ActiveX à votre formulaire, vous devez les ajouter à la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="84861-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="84861-106">Pour plus d’informations, consultez [composants com, boîte de dialogue Personnaliser la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="84861-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="84861-107">Ajouter un contrôle ActiveX à votre Windows Form</span><span class="sxs-lookup"><span data-stu-id="84861-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="84861-108">Pour ajouter un contrôle ActiveX à votre Windows Form, double-cliquez sur le contrôle dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="84861-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="84861-109">Visual Studio ajoute toutes les références au contrôle dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="84861-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="84861-110">Pour plus d’informations sur les éléments à prendre en compte lors de l’utilisation de contrôles ActiveX sur des Windows Forms, consultez [considérations relatives à l’hébergement d’un contrôle ActiveX dans un Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="84861-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="84861-111">L’importateur de contrôles ActiveX (AxImp. exe) de Windows Forms crée des arguments d’événement d’un type différent de celui prévu lors de l’importation de bibliothèques de liens dynamiques ActiveX.</span><span class="sxs-lookup"><span data-stu-id="84861-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="84861-112">Les arguments créés par AxImp. exe sont semblables à ce qui suit : `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quand `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` est attendu.</span><span class="sxs-lookup"><span data-stu-id="84861-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="84861-113">N’oubliez pas que cette irrégularité n’empêche pas le code de fonctionner normalement.</span><span class="sxs-lookup"><span data-stu-id="84861-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="84861-114">Pour plus d’informations, consultez [Windows Forms ActiveX Control importateur (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="84861-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84861-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84861-115">See also</span></span>

- [<span data-ttu-id="84861-116">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="84861-117">[Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="84861-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="84861-118">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="84861-119">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="84861-120">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="84861-121">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84861-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
