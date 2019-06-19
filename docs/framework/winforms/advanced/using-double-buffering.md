---
title: Utilisation de doubles tampons d'enregistrements
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169917"
---
# <a name="using-double-buffering"></a><span data-ttu-id="1ebb4-102">Utilisation de doubles tampons d'enregistrements</span><span class="sxs-lookup"><span data-stu-id="1ebb4-102">Using Double Buffering</span></span>
<span data-ttu-id="1ebb4-103">Vous pouvez utiliser des graphiques de double tampon pour réduire le scintillement dans vos applications qui contiennent des opérations de dessin complexes.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="1ebb4-104">Le .NET Framework contient une prise en charge intégrée de double tampon, ou vous pouvez gérer et restituer manuellement des graphiques.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ebb4-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1ebb4-105">In This Section</span></span>  
 [<span data-ttu-id="1ebb4-106">Graphiques mis deux fois en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="1ebb4-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="1ebb4-107">Introduit la double mise en mémoire tampon concept et les contours .NET Framework prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="1ebb4-108">Guide pratique pour Réduire le scintillement des graphiques avec Double mise en tampon pour les formulaires et contrôles</span><span class="sxs-lookup"><span data-stu-id="1ebb4-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="1ebb4-109">Montre comment utiliser la double mise en mémoire tampon de prise en charge dans le .NET Framework de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="1ebb4-110">Guide pratique pour Gérer manuellement des graphiques mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="1ebb4-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="1ebb4-111">Montre comment gérer le mécanisme de double tampon dans les applications.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="1ebb4-112">Guide pratique pour Restituer manuellement des graphiques mis en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="1ebb4-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="1ebb4-113">Montre comment restituer des graphiques mis en mémoire tampon double.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ebb4-114">Référence</span><span class="sxs-lookup"><span data-stu-id="1ebb4-114">Reference</span></span>  
 <span data-ttu-id="1ebb4-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Méthode de contrôle qui permet la double mise en tampon.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="1ebb4-116"><xref:System.Drawing.BufferedGraphicsContext> Fournit des méthodes pour créer des mémoires tampons de graphiques.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="1ebb4-117">Fournit l’accès au contexte graphique mis en mémoire tampon pour un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1ebb4-117">Provides access to the buffered graphics context for a application domain.</span></span>
