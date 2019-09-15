---
title: 'Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f52c1d127df8f0e831db0749e3453bb1c54d5886
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972069"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="4b438-102">Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="4b438-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="4b438-103">Lorsque vous développez et distribuez des contrôles, vous souhaiterez peut-être que ces contrôles s’affichent dans la boîte de dialogue **choisir des éléments de boîte à outils** de Visual Studio, qui s’affiche lorsque vous cliquez avec le bouton droit sur la boîte **à outils** et sélectionnez **choisir les éléments**.</span><span class="sxs-lookup"><span data-stu-id="4b438-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="4b438-104">Vous pouvez activer votre contrôle pour qu’il s’affiche dans cette boîte de dialogue à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="4b438-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="4b438-105">Pour afficher votre contrôle dans la boîte de dialogue choisir des éléments de boîte à outils :</span><span class="sxs-lookup"><span data-stu-id="4b438-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="4b438-106">Installez votre assembly de contrôle sur le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="4b438-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="4b438-107">Pour plus d’informations, consultez [Guide pratique pour installer un assembly dans le Global Assembly Cache](../../app-domains/install-assembly-into-gac.md)</span><span class="sxs-lookup"><span data-stu-id="4b438-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md)</span></span>

  <span data-ttu-id="4b438-108">ou</span><span class="sxs-lookup"><span data-stu-id="4b438-108">-or-</span></span>

- <span data-ttu-id="4b438-109">Inscrivez votre contrôle et ses assemblys au moment du design associés à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="4b438-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="4b438-110">AssemblyFoldersEx est un emplacement du registre où les fournisseurs tiers stockent les chemins d’accès de chaque version de l’infrastructure qu’ils prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="4b438-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="4b438-111">La résolution au moment du design peut rechercher des assemblys de référence dans cet emplacement du Registre.</span><span class="sxs-lookup"><span data-stu-id="4b438-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="4b438-112">Le script de Registre peut spécifier les contrôles que vous souhaitez voir apparaître dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4b438-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b438-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b438-113">See also</span></span>

- [<span data-ttu-id="4b438-114">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="4b438-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="4b438-115">Guide pratique : installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="4b438-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="4b438-116">Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="4b438-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
