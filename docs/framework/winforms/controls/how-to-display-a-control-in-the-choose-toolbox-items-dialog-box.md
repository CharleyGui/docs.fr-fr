---
title: 'Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015895"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="c7752-102">Procédure : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="c7752-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="c7752-103">Lorsque vous développez et distribuez des contrôles, vous souhaiterez peut-être que ces contrôles s’affichent dans la boîte de dialogue **choisir des éléments de boîte à outils** de Visual Studio, qui s’affiche lorsque vous cliquez avec le bouton droit sur la boîte **à outils** et sélectionnez **choisir les éléments**.</span><span class="sxs-lookup"><span data-stu-id="c7752-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="c7752-104">Vous pouvez activer votre contrôle pour qu’il s’affiche dans cette boîte de dialogue à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="c7752-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="c7752-105">Pour afficher votre contrôle dans la boîte de dialogue choisir des éléments de boîte à outils:</span><span class="sxs-lookup"><span data-stu-id="c7752-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="c7752-106">Installez votre assembly de contrôle sur le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c7752-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="c7752-107">Pour plus d'informations, voir [Procédure : installer un assembly dans le Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="c7752-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>

  <span data-ttu-id="c7752-108">ou</span><span class="sxs-lookup"><span data-stu-id="c7752-108">-or-</span></span>

- <span data-ttu-id="c7752-109">Inscrivez votre contrôle et ses assemblys au moment du design associés à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="c7752-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="c7752-110">AssemblyFoldersEx est un emplacement du registre où les fournisseurs tiers stockent les chemins d’accès de chaque version de l’infrastructure qu’ils prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="c7752-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="c7752-111">La résolution au moment du design peut rechercher des assemblys de référence dans cet emplacement du Registre.</span><span class="sxs-lookup"><span data-stu-id="c7752-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="c7752-112">Le script de Registre peut spécifier les contrôles que vous souhaitez voir apparaître dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="c7752-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7752-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7752-113">See also</span></span>

- [<span data-ttu-id="c7752-114">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="c7752-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="c7752-115">Guide pratique pour installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c7752-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [<span data-ttu-id="c7752-116">Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="c7752-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
