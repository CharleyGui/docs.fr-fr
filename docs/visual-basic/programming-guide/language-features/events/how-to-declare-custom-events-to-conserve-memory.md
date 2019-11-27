---
title: 'Comment : déclarer des événements personnalisés pour économiser la mémoire'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345128"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="d5e97-102">Comment : déclarer des événements personnalisés pour économiser la mémoire (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5e97-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="d5e97-103">Dans certains cas, il est important qu’une application conserve son utilisation de la mémoire faible.</span><span class="sxs-lookup"><span data-stu-id="d5e97-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="d5e97-104">Les événements personnalisés permettent à l’application d’utiliser uniquement la mémoire pour les événements qu’elle gère.</span><span class="sxs-lookup"><span data-stu-id="d5e97-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="d5e97-105">Par défaut, lorsqu’une classe déclare un événement, le compilateur alloue de la mémoire pour un champ afin de stocker les informations sur l’événement.</span><span class="sxs-lookup"><span data-stu-id="d5e97-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="d5e97-106">Si une classe possède de nombreux événements inutilisés, ils occupent inutilement de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d5e97-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="d5e97-107">Au lieu d’utiliser l’implémentation par défaut des événements fournis par Visual Basic, vous pouvez utiliser des événements personnalisés pour gérer l’utilisation de la mémoire plus attentivement.</span><span class="sxs-lookup"><span data-stu-id="d5e97-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5e97-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5e97-108">Example</span></span>  
 <span data-ttu-id="d5e97-109">Dans cet exemple, la classe utilise une instance de la classe <xref:System.ComponentModel.EventHandlerList>, stockée dans le champ `Events`, pour stocker des informations sur les événements en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d5e97-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="d5e97-110">La classe <xref:System.ComponentModel.EventHandlerList> est une classe de liste optimisée conçue pour contenir des délégués.</span><span class="sxs-lookup"><span data-stu-id="d5e97-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="d5e97-111">Tous les événements de la classe utilisent le champ `Events` pour effectuer le suivi des méthodes qui gèrent chaque événement.</span><span class="sxs-lookup"><span data-stu-id="d5e97-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="d5e97-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5e97-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="d5e97-113">Événements</span><span class="sxs-lookup"><span data-stu-id="d5e97-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="d5e97-114">Guide pratique : déclarer des événements personnalisés pour éviter les blocages</span><span class="sxs-lookup"><span data-stu-id="d5e97-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
