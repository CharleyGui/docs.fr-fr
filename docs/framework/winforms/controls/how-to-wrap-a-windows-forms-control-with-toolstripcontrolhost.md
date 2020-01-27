---
title: Encapsuler le contrôle avec ToolStripControlHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: c7dbe042623006ed9501016669d6451ba0667cbc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728180"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="9d7cd-102">Comment : inclure un contrôle Windows Forms dans un wrapper avec ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="9d7cd-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="9d7cd-103"><xref:System.Windows.Forms.ToolStripControlHost> est conçu pour permettre l'hébergement de contrôles Windows Forms arbitraires à l'aide du constructeur <xref:System.Windows.Forms.ToolStripControlHost> ou en étendant le <xref:System.Windows.Forms.ToolStripControlHost> lui-même.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="9d7cd-104">Il est plus facile d'encapsuler le contrôle en étendant <xref:System.Windows.Forms.ToolStripControlHost> et en implémentant des propriétés et des méthodes qui exposent les propriétés et les méthodes fréquemment utilisées du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="9d7cd-105">Vous pouvez également exposer des événements pour le contrôle au niveau du <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="9d7cd-106">Pour héberger un contrôle dans un ToolStripControlHost par dérivation</span><span class="sxs-lookup"><span data-stu-id="9d7cd-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="9d7cd-107">Étendez <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="9d7cd-108">Implémentez un constructeur sans paramètre qui appelle le constructeur de classe de base en passant le contrôle souhaité.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="9d7cd-109">Déclarez une propriété du même type que le contrôle encapsulé et retournez `Control` comme type de contrôle correct dans l'accesseur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="9d7cd-110">Exposez les autres propriétés et méthodes fréquemment utilisées du contrôle encapsulé avec des propriétés et des méthodes dans la classe étendue.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="9d7cd-111">Si vous le souhaitez, substituez les méthodes <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A> et <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> et ajoutez les événements de contrôle que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="9d7cd-112">Fournissez l'encapsulage nécessaire pour les événements que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="9d7cd-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="9d7cd-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d7cd-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d7cd-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9d7cd-114">Compiling the Code</span></span>  
  
<span data-ttu-id="9d7cd-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9d7cd-115">This example requires:</span></span>
  
- <span data-ttu-id="9d7cd-116">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="9d7cd-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7cd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d7cd-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="9d7cd-118">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d7cd-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="9d7cd-119">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d7cd-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="9d7cd-120">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d7cd-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
