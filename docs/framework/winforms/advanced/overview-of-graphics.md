---
title: Vue d'ensemble des graphismes
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505325"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="c7fa3-102">Vue d'ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="c7fa3-102">Overview of Graphics</span></span>
<span data-ttu-id="c7fa3-103">GDI + est une interface de programmation d’application (API) qui forme le sous-système du système d’exploitation Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="c7fa3-104">GDI + est responsable de l’affichage des informations sur les écrans et les imprimantes.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="c7fa3-105">Comme son nom l’indique, GDI + est le successeur de GDI, l’Interface graphique inclus avec les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="c7fa3-106">Interface de classes managées</span><span class="sxs-lookup"><span data-stu-id="c7fa3-106">Managed Class Interface</span></span>  
 <span data-ttu-id="c7fa3-107">L’API GDI + est exposée via un ensemble de classes déployées comme du code managé.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="c7fa3-108">Cet ensemble de classes est appelé le *interface de classes managées* à GDI +.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="c7fa3-109">Les espaces de noms suivants composent l'interface de classes managées :</span><span class="sxs-lookup"><span data-stu-id="c7fa3-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="c7fa3-110">Avec une Interface graphique, tels que GDI +, vous pouvez afficher des informations sur un écran ou une imprimante sans avoir à se soucier des détails d’un périphérique d’affichage particulier.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="c7fa3-111">Le programmeur effectue des appels aux méthodes fournies par les classes de GDI +.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="c7fa3-112">Ces méthodes effectuent ensuite les appels appropriés aux pilotes de périphériques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="c7fa3-113">GDI + isole l’application du matériel graphique.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="c7fa3-114">C’est cette isolation qui permet à un programmeur créer des applications indépendantes du périphérique.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fa3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7fa3-115">See also</span></span>

- [<span data-ttu-id="c7fa3-116">Vue d’ensemble des graphismes</span><span class="sxs-lookup"><span data-stu-id="c7fa3-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
