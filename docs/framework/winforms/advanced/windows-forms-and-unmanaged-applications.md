---
title: Applications non gérées
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746369"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="a989e-102">Applications Windows Forms et non managées</span><span class="sxs-lookup"><span data-stu-id="a989e-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="a989e-103">Les contrôles et les applications Windows Forms peuvent interagir avec des applications non managées, avec certaines restrictions.</span><span class="sxs-lookup"><span data-stu-id="a989e-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="a989e-104">Les sections suivantes décrivent les scénarios et les configurations pris en charge et non pris en charge par les applications et les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a989e-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a989e-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a989e-105">In This Section</span></span>  
 [<span data-ttu-id="a989e-106">Vue d'ensemble des applications Windows Forms et non managées</span><span class="sxs-lookup"><span data-stu-id="a989e-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="a989e-107">Propose des informations générales sur l'utilisation et l'implémentation des contrôles Windows Forms qui fonctionnent avec les applications non managées.</span><span class="sxs-lookup"><span data-stu-id="a989e-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="a989e-108">Guide pratique pour prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog</span><span class="sxs-lookup"><span data-stu-id="a989e-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="a989e-109">Fournit un exemple de code qui montre comment utiliser la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour exécuter un Windows Form dans une application non managée.</span><span class="sxs-lookup"><span data-stu-id="a989e-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="a989e-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span><span class="sxs-lookup"><span data-stu-id="a989e-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="a989e-111">Fournit un exemple de code qui montre comment exécuter un Windows Form sur son propre thread.</span><span class="sxs-lookup"><span data-stu-id="a989e-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="a989e-112">Consultez également [Procédure pas à pas : prise en charge de COM Interop en affichant chaque Windows Forms sur son propre thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a989e-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a989e-113">Reference</span><span class="sxs-lookup"><span data-stu-id="a989e-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a989e-114">Permet de créer un thread distinct pour un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="a989e-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a989e-115">Démarre une boucle de message pour un thread.</span><span class="sxs-lookup"><span data-stu-id="a989e-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="a989e-116">Marshale les appels à partir d’une application non managée vers un formulaire.</span><span class="sxs-lookup"><span data-stu-id="a989e-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a989e-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a989e-117">Related Sections</span></span>  
 [<span data-ttu-id="a989e-118">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="a989e-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="a989e-119">Propose des informations générales sur l'utilisation de types .NET Framework dans les applications non managées.</span><span class="sxs-lookup"><span data-stu-id="a989e-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
