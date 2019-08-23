---
title: Multithreading dans les contrôles Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952684"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="a479b-102">Multithreading dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a479b-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="a479b-103">Dans de nombreuses applications, vous pouvez rendre votre interface utilisateur plus réactive en effectuant des opérations qui prennent du temps sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="a479b-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="a479b-104">Un certain nombre d’outils sont disponibles pour le multithreading de vos contrôles de <xref:System.Threading> Windows Forms, y <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> compris l’espace de `BackgroundWorker` noms, la méthode et le composant.</span><span class="sxs-lookup"><span data-stu-id="a479b-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a479b-105">Le `BackgroundWorker` composant remplace et ajoute des fonctionnalités à <xref:System.Threading> l’espace de <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> noms et à la méthode; Toutefois, celles-ci sont conservées pour la compatibilité descendante et l’utilisation ultérieure, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="a479b-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a479b-106">Pour plus d’informations, consultez [vue d’ensemble du composant BackgroundWorker](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a479b-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a479b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a479b-107">In This Section</span></span>  
 [<span data-ttu-id="a479b-108">Guide pratique pour Effectuer des appels thread-safe à des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a479b-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="a479b-109">Montre comment effectuer des appels thread-safe pour Windows Forms contrôles.</span><span class="sxs-lookup"><span data-stu-id="a479b-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a479b-110">Guide pratique pour Utiliser un thread d’arrière-plan pour rechercher des fichiers</span><span class="sxs-lookup"><span data-stu-id="a479b-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="a479b-111">Montre comment utiliser l' <xref:System.Threading> espace de noms et la <xref:System.Windows.Forms.Control.BeginInvoke%2A> méthode pour rechercher des fichiers de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a479b-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a479b-112">Référence</span><span class="sxs-lookup"><span data-stu-id="a479b-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a479b-113">Documente un composant qui encapsule un thread de travail pour les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="a479b-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="a479b-114">Explique comment charger un son de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a479b-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="a479b-115">Décrit comment charger une image de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a479b-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a479b-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a479b-116">Related Sections</span></span>  
 [<span data-ttu-id="a479b-117">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="a479b-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="a479b-118">Montre comment effectuer une opération qui prend du temps avec le <xref:System.ComponentModel.BackgroundWorker> composant.</span><span class="sxs-lookup"><span data-stu-id="a479b-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="a479b-119">Vue d'ensemble du composant BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="a479b-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="a479b-120">Fournit des rubriques qui décrivent comment utiliser <xref:System.ComponentModel.BackgroundWorker> le composant pour les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="a479b-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
